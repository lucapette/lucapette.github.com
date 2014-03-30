---
title: "Go, docker and a CI server"
description: A short tale about my first steps with go and docker
keywords: go, golang, docker, gitlab, gitlab-ci
category: go
layout: blog
---

Lately I've been playing with [go](http://golang.org) and
[docker](https://docker.io) a lot.  I have several reasons why I'm spending
part of my (not really copious) free time to have a look at those two
technologies but I'll skip them now because they would offer you nothing
practical to read about, it would just be my opinion and I'm not sure that's
interesting. So, the story started with a side-project I can't open source yet
and this project is written in go. Of course, starting a new project comes
with some obvious questions like:

- how do I CI it?
- how do I deploy it?

Generally I have some sort of canned answers for Ruby projects but this
doesn't apply to a brand-new go project, partly because go is a compiled
language (so, for example, deployment contains a "produce a binary and upload
it" phase) and party because it's a completely new world for me. On top of
this, there is a small list of goals I wanted to achieve with this project:

- My private repository hosting has to be cheap
- Same for my CI server
- My CI server must not have any of my project dependencies installed
- My deployment script had to be fast and short (in terms of code lines)

So keeping that in mind, I did some research and I came up with the following
recipe:

- gitlab & gitlab-ci
- mina
- docker

[gitlab](https://www.gitlab.com/gitlab-ce/) and
[gitlab-ci](https://www.gitlab.com/gitlab-ci/) were obvious choices IMO. I
must confess I was a bit sceptical at first because I remember when I first
tried gitlab I wasn't that much impressed. The truth is that the project
hugely evolved and now I can't really find any flaw in it. The installation
process was extremely easy (I lost a few minutes of a specific step that was
made clear  by [this](https://github.com/gitlabhq/gitlab-ci-runner/pull/78)
pull request) and the UI is fast and mature. I can't say how gitlab and
gitlab-ci would react under heavy usage but I'm positively impressed with what
I saw.  The integration between the code hosting and the CI server is very
nice and took no time to configure. Last but least, the two applications run
smoothly on a 10 $/month server with 1gb of RAM.

[mina](http://nadarei.co/mina/) is a very fast capistrano-like deployer. I got
interested in it because being fast was a design goal for this project. So
answering the question *how do I deploy it?* was easy and I think Mina helped
in making it easy. The only tricky part for me was finding a way of producing
the binary and sending it to the production machine. I've read about people
using storage hosting like s3 but I'm not a fan of these solutions because I
find them costly without adding any value. Moreover, I wouldn't own all the
steps of my deployment process. So now I'm using something brutally simple:
rsync. Faking that my project is called awesome-go-project, this is how my
deployment script looks like now:

{% highlight ruby %}
set :deploy_binary, lambda { "awesome-go-project-#{`git --no-pager log --format="%h" -1`.strip}" }

task setup: :environment do
  queue! %[mkdir -p "#{deploy_to}/shared/log"]
  queue! %[chmod g+rx,u+rwx "#{deploy_to}/shared/log"]
end

desc 'Build a release'
task :release do
  sh 'make build-release'
  sh "rsync --progress -avzp -e 'ssh -p #{port}' release/awesome-go-project #{user}@#{domain}:/tmp/#{deploy_binary}"
end
{% endhighlight %}

I omitted most of the boring configuration setup and the actual deploy task
since the task is just linking the `deploy_binary` to a generic named binary a
`sudo service awesome-go-project restart`. The only thing I'd spend a word
about is the way I manage the binary, because since it's a binary and I don't
need the source code on the server it's not obvious which version of the code
I'm actually running on production, so all I'm doing with the `deploy_binary`
variable is creating a binary that contains the SHA-1 of the commit I'm
deploying. Another detail to take into account is that I had to learn how to
cross-compile go code, since I use a mac and the production machine is an
ubuntu machine, but that was made very easy by
[golang-crosscompile](https://github.com/davecheney/golang-crosscompile).

The real fun started with docker. When thinking about how to avoid installing
dependencies on my CI server, I thought it would be first time I could try
docker for something that is more than a "Hello World" container. My
side-project has a few dependencies (like the awesome
[influxdb](http://influxdb.org/) and mysql) but for the sake of this
discussion let's limit it to early stages of the project where the only
dependency to run the tests was the `go test -v` command. The first thing I
did was creating two docker repositories,
[go-lang](https://index.docker.io/u/lucapette/go-lang/) and
[go-command](https://index.docker.io/u/lucapette/go-command/). It felt a bit
like re-inventing the wheel because there are already repositories doing
something similar but none of them is doing exactly what I wanted. So, since
I'm in a truly learning-mode with side-projects, instead of going for *"I
adapt to existing solution so I'm fast"* I went for *"I write my own thing so
I have exactly what I want but then I'm slow"*. And it was a nice experience.
Developing a Dockerfile is an interesting process and it's pleasant to learn
because docker itself has a very nice interface and a good documentation. So,
`lucapette/go-lang` looks like this:

{% highlight sh %}
FROM debian:jessie

MAINTAINER lucapette <lucapette@gmail.com>

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    git \
    make

# Get and compile go
RUN curl -s https://go.googlecode.com/files/go1.2.1.src.tar.gz | tar -v -C /usr/local -xz
RUN cd /usr/local/go/src && ./make.bash --no-clean 2>&1
ENV PATH /usr/local/go/bin:/go/bin:$PATH
ENV GOPATH /go
{% endhighlight %}

The only noticeable thing is the image I started from. I'm following the
advices from the wonderful [Dockerfile Best Practices - take
2](http://crosbymichael.com/dockerfile-best-practices-take-2.html), you should
totally read it (and take one too). This container is *just* providing us
with a installation of go. What I did next was using the image produced by
`lucapette/go-lang` in order to create a `lucapette/go-command`:

{% highlight sh %}
FROM lucapette/go-lang

RUN mkdir -p /go/src

ENTRYPOINT ["go"]
{% endhighlight %}

That is very short because all the magic is contained in the
[ENTRYPOINT](http://docs.docker.io/en/latest/reference/builder/#entrypoint)
instruction. In short, this instruction makes the container act as an
executable, in this case the `go` command. Now, let's keep the assumption my
project is called `awesome-go-project`, my CI script is something like the
following:

{% highlight sh %}
#!/bin/bash

set -e

docker run --rm=true -v `pwd`:/go/src/github.com/lucapette/awesome-go-project -w /go/src/github.com/lucapette/awesome-go-project  lucapette/go-command test -v
{% endhighlight %}

The script makes the assumption it will run from the root directory of the
awesome-go-project. There are a few things happening, let's dissect the docker
command I'm running:

- `--rm=true`

  Awesome feature. As soon as the container exits, docker will remove it.

- `-v `pwd`:/go/src/github.com/lucapette/awesome-go-project`

  This command is mounting the current directory (i.e. the source code of the
  project) in the path specified after the `:`.

- `-w /go/src/github.com/lucapette/awesome-go-project`

  This is setting the working path to the given directory.

- `test -v`

  Since we have an `ENTRYPOINT` set, this is considered an argument for the `go`
  command.

When I push to master, gitlab-ci will run the script that is running a docker
command that runs my tests. I find it **awesome** that I can **really** run my
tests on the CI server without having to install anything related to the code
I'm testing, not *even* the programming language I'm using for the project. My
only dependency on the server is docker itself and I think this is a very good
trade-off. I'm currently in the process of making the test suite more
robust, that will result in having more dependencies like a real influxdb
server. And I can already foresee how funny it will be to
[link](http://docs.docker.io/en/latest/use/working_with_links_names/) my
containers for running the tests.
