---
title: "A couple of useful aliases for docker"
description: A couple of useful aliases for docker that use everyday
keywords: docker, bash, zsh
category: docker
layout: blog
---

Writing [Dockerfiles](http://docs.docker.io/reference/builder/) is a pretty
funny experience. I like the idea of writing the minimum amount of
instructions that will make possible to run kafka, redis, influxdb or whatever
thing is suitable for containers. While making my first steps developing a
Dockerfile I noticed there were a couple of commands I was typing all the
time. And they were a bit tedious to write. Since I'm a bit lazy I started
looking into aliases other people were using to solve the same problem (being
lazy means you don't want to re-invent the wheel too). I think I found
something that really fit my needs and how I would have done it but the thing
is that I couldn't find the reference anymore so I finished re-implementing
the aliases on my own (that felt like re-inventing the wheel someone) and I
can't give credit to the person that originated this idea.

The basic idea is adding aliases to docker in a way the feel like *native*
commands. They look like:

{% highlight sh %}
docker clean
{% endhighlight %}

instead of following the usual `alias foo=bar` approach. In order to achieve
the *native feeling* I implemented the following function:

{% highlight sh %}
docker() {
  if command -v "docker-$1" > /dev/null 2>&1; then
    subcommand=$1
    shift
    docker-$subcommand $@
  else
    /usr/local/bin/docker $@
  fi
}
```
{% endhighlight %}

The function is using its first argument to check if there is a command on the
system that matches the argument itself using a convention that I saw already
used in git (there is a nice stackoverflow dicussion about how to check a
command exists
[here](http://stackoverflow.com/questions/592620/how-to-check-if-a-program-exists-from-a-bash-script)).
Basically, if you want to add a `docker clean` command, you need to make
available in your path an executable names `docker-clean`. If this command
exists it gets executed otherwise the function delegates to the docker
executable the execution of the given command. Pretty simple and pretty neat.
So far I added two aliases for commands I'm executing all the time. I have a
`docker clean` that looks like this:

{% highlight sh %}
#/bin/bash

docker rm $(docker ps -a -q)
{% endhighlight %}

Simple and effective. And then I have a `docker sh` that looks like this:

{% highlight sh %}
#/bin/bash

docker run -i -t --entrypoint=/bin/bash $1 --
{% endhighlight %}

Very helpful to look around in a container while building it.

Now the only thing I miss is auto-completion for my custom commands but I may
add it soon.
