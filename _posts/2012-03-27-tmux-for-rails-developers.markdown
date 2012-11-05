---
title: 'Tmux for rails developers'
description: 'tmux for rails developers'
keywords: tmux, rails, vim, pair programming
category: rails
layout: blog
---

There has been a lot of buzz about [tmux](http://tmux.sourceforge.net/)
recently. The fine pragmatic programmers folks published a very good
[book](http://pragprog.com/book/bhtmux/tmux) about it and on twitter, at least
on my stream, there are a lot people in love with it. Actually, I run into it
for a *real word* need (I'll explain this later) and I found it incredible
useful in a lot of other situations. So, I would like to share them with you.

I assume you already know what tmux **is**, it's pointless to write again what
could easily find somewhere else. Indeed, there are a
[lot](http://blog.hawkhost.com/2010/06/28/tmux-the-terminal-multiplexer/)
[of](http://blog.hawkhost.com/2010/07/02/tmux-%E2%80%93-the-terminal-multiplexer-part-2/)
[interesting](http://blog.hawkhost.com/2010/07/02/tmux-%E2%80%93-the-terminal-multiplexer-part-2/)
[resources](http://mutelight.org/articles/practical-tmux)
[out](http://robots.thoughtbot.com/post/2641409235/a-tmux-crash-course)
[there](http://robots.thoughtbot.com/post/2166174647/love-hate-tmux) for an
introduction to tmux. So, what I'm trying to do with this article is just
offering the point of view of a Rails developer who is actually using tmux
daily.

## When you can use tmux

Using tmux means meeting the following implicit requirements:

- Using the terminal is a big part of your development workflow

  Yeah, I know. It looks like a stupid point. But it really isn't. It doesn't
  make sense at all to give tmux a try if you're not using the terminal all
  the time. It's not a strict requirement but trying something that will speed
  up your productivity with something you don't use it's really pointless.

- You use an editor that works well in the terminal

  If you already read something else here on my blog then you know that I love
  Vim, so if you, like me, are a Vim user you're lucky. But that's not the
  real point. You need a whatever editor that works fine in the terminal. So,
  if you use some fancy editor (or some super-fancy IDE) that doesn't work
  well in the terminal you can stop reading this article. *You're wasting your
  time here.*

## Why You should use tmux for Rails development

Well, this is the *real* question, right?

I have my simple answer: tmux will help you to stay totally focused on what
you're doing. Plain and simple. I talked to people that were saying "I don't
know. It really is that better than switching terminal tabs?  Or switching
applications?". It's a fair point but the answer is "Yes, it is **better**".
In my experience, there is always a context switch when you have to read why a
test is failing or you have to read the log or you have to open up a terminal
tab or you have to...  OK you got it.

The tmux answer is panes.

Tmux has this *killer* feature that responds to the name of panes. They are
better that windows because you really don't have to switch a context, what
you're looking for is already there. It's a tiny difference but it's a very
important one. Furthermore, tmux has a lot of keyword shortcuts. Fortunately,
you can configure them because I found them a bit crappy (read crappy as
**extremely difficult to remember**). And you don't have to forget that each
single pane is an entire terminal session. It's obvious because tmux is a
terminal multiplexer but it's not that obvious to have this opportunity with
another software if you really think about it.

To help you getting a picture of how panes can be used I'll talk about how is
my workflow with Rails projects: I have two panes with horizontal layout (nice
tmux feature here, it has various pane layouts and you can switch through them
with a single keystroke). In the top pane (that is the bigger one) I usually
have Vim with a spec open and in the bottom pane I run the spec, usually with
Guard. When a I need to read the log or to open a console I open a new window
and I read it there.  It a simple setup but it's like a dream for me because I
can do all I need to do while developing within the same visual space. I
[configured](https://github.com/lucapette/dotfiles/blob/master/tmux.conf) tmux
in a manner it's more similar to Vim. So I don't even have to remember new
stuff. And I'm pretty happy with its appearance too now:

<a href="/img/tmux-and-rails.png" target='_blank'>
  <img src="/img/tmux-and-rails.png" width="700" height="394" alt="tmux and rails" />
</a>

It looks nice, doesn't it?

Of course, panes are not all. There are windows and sessions too. I personally
use windows when I do want a *context switch* but you could find them useful
for another reason. Sessions are the *real word* reason why I run into tmux.
In this period, I'm doing a lot of remote pair programming. When we started to
pair we tried a lot of different solutions combining video calling and screen
sharing. But none of them worked well. These technologies are an amazing way
of communicating with people but unfortunately they requires a very good
connection to work fine. But, even when the connection is very good, there is
another problem: you have to choose who types in the pair session because you
can't switch easily. And that's very important for pair programming. So I did
a bit of a research and I found that a lot of people solved this problem using
tmux. And that is how I run into tmux. At first, I didn't understood how tmux
could help in such a situation. Then, I finally understood what tmux session
are and how you can easily attach your terminal to an existing tmux session.
I think that tmux is a perfect solution for remote pair programming. It's
fast, light (in terms of connection) and very easy to set-up.

## the tmux book

Someo days ago, some guy I respect a lot tweeted, with a note of sarcasm, that
a book about tmux would be longer of the source code of tmux itself. Yes, nice
and reasonable point. Indeed, I was very sceptical before I bought the book.
My concern was I didn't really need an entire book for such a tool. By the
way, when I was approaching tmux for pair programming I was in real need of
getting a working configuration quickly. The book is cheap and I thought
reading it could have been a way to save time. I read it in two times,
probably it just took a couple of hours to read it entirely but now I can say
**the book it's absolutely worth reading it**. It contains a lot of useful
information, it's well written and it is very cheap. So, if you're interesting
in knowing more about tmux, just **buy it**.

## tmuxinator

While using tmux on a daily basis I noticed a pattern:

- cd to ~/code/awesome-project
- run tmux
- split the session in two horizontal panes
- run git status in the top pane
- run guard in the bottom pane

Furthermore, when awesome-project is a Rails project (that is quite always the
case for me) I generally create another window where I start the server or run
tail for the logging. After some days of executing always the very same steps
I run into [tmuxinator](https://github.com/aziz/tmuxinator), thanks to the
mentioned book. This gem is a way to *manage complex tmux sessions easily* and
I have to say I like the idea very much. Actually, I would have written such a
gem if there wasn't already one. The basic idea behind the gem is giving you
the opportunity to run just a single command in order to create a complex tmux
session, with panes and windows. tmuxinator uses a simple configuration file
that is really is self-explanatory:

{% highlight yml %}
project\_name: awesome-project
project\_root: ~/code/awesome-project
socket\_name: awesome-project
pre: alias tmux='tmux -2'
tabs:
- editor:
layout: main-horizontal
panes:
- git st
-
- logs: tail -f log/test.log
- console: rails c test
{% endhighlight %}

So each tab creates a window, there you can just run a command or create
panes and run commands in them. Pretty neat.

I'm very glad there is a `pre` option because, using gnome-terminal, tmux
won't behave correctly if it doesn't assume it's running inside a 256 colours
terminal. tmuxinator is a good gem and there is some room for improvements too.
For example, at this very moment there is no way to specify a socket name and
it would be great to have it because using a socket name is a quick way to do
some pair programming using tmux. By the way, I checked the pull-requests and
there is a lot of nice stuff there (included a patch for the socket name).

I recommend you to give tmuxinator a try, if you're going to use tmux the odds
are you'll like this gem.

## Issues I run into

I'm having a great time using tmux and I have the feeling it'll become an
indispensable tool for me. Sadly, there is always room for issues. The first
issue I run into has been a good one. I didn't ever spent some time trying to
configure colours for my gnome-terminal because I was using the GUI version of
Vim and there the colours are awesome. So, I had to spend some time tweaking
the configuration of gnome-terminal. And now I have a very good looking
gnome-terminal.

All the other issues I run into are Vim related. First of all, I miss how
beautiful look the GUI versions of some Vim features. Just things like
underlined chars, bad-spelled words. The other issue is about mappings. Some
of my mappings aren't working in the terminal. Actually, the problem should
be related to gnome-terminal but I didn't investigated it yet. You'll have
some problem if you're using MacVim and apple key mappings. They won't work
either in the terminal. I read a lot of people just remapped some stuff using
the leader key. Actually, I have the feeling that sometimes is a good thing to
[embrace the
uncomfortable](http://matt.might.net/articles/programmers-resolutions/). And,
fot that very reason, I'm trying to do some od the stuff I was doing with that
mappings in another way and I'm learning a lot of new stuff!

## Where the Rails stuff?

Yes, re-reading the post I had the feeling I ended up talking about Rails
specific stuff less than I thought while I was going to write it. But, I can
understand why: tmux isn't specific to Rails, of course. It just fits very
well with my personal habits. Furthermore, one of the most important thing I'm
(still) learning living our profession is giving new stuff a try when I have
the chance. Especially, when a lot of people are already trying or using the
same stuff. So, give tmux a try if you're using the console all the time. I
bet most of you will really like it.
