---
title: "A couple of useful aliases for docker"
description: A couple of useful aliases for docker that I use everyday
keywords: docker, bash, zsh
category: docker
layout: articles
---

Writing [Dockerfiles](http://docs.docker.io/reference/builder/) is pretty
funny experience. I like the idea of writing the minimum amount of
instructions that will make it possible to run
[kafka](http://wurstmeister.github.io/kafka-docker/),
[redis](http://docs.docker.io/examples/running_redis_service/),
[influxdb](https://index.docker.io/u/lucapette/influxdb/) or whatever thing is
suitable for containers. While making my first steps in developing a
Dockerfile I noticed there were a few commands I was typing all the time. And
they were tedious to write. Since I'm a bit lazy I started looking into
aliases other people were using to solve the same problem (being lazy also
means you don't want to re-invent the wheel). I think I found something that
really fits my needs and it is done the way I would do it.  However,  I
couldn't find the reference anymore so I finished re-implementing the aliases
on my own (that felt like re-inventing the wheel somehow) and I can't give
credit to the person that originated this idea.

The basic idea is adding aliases to docker in a way they feel like *native*
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
{% endhighlight %}

The function is using its first argument to check if there is a command on the
system that matches the argument itself using a convention that I have already
seen in git (there is a nice stackoverflow dicussion about how to check if a
command exists
[here](http://stackoverflow.com/questions/592620/how-to-check-if-a-program-exists-from-a-bash-script)).
Basically, if you want to add a `docker clean` command, you need to make an
executable named `docker-clean` available in your path. If this command
exists, it gets executed. Otherwise the function delegates the execution of
the given command to docker. Pretty simple and pretty neat.  So far I added
two aliases for commands I'm executing all the time. I have a `docker clean`
that looks like this:

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
add it soon. I hope this helps to simply your workflows while building
Dockerfiles.
