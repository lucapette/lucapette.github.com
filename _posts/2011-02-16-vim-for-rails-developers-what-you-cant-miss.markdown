---
title: "Vim for rails developers: what you can't miss"
description: my first article of the series "vim for rails developer". I will use the article as an index for the series
keywords: vim, rails,rails.vim, NERDTree, FuzzyFinderTextMate, codepath
category: vim
layout: articles
---

Vim is my editor of choice and Rails is my framework. I think many of us have
the same taste and I want to share with you my experiences while using both.
I'm going to write a series of posts regarding this topic. I start with _what
you can't miss_ when you decide to use both rails and vim seriously.

## Am I miss something?

So you use vim, you code in Ruby and you are building the most exciting
web-application of the world with Rails. But, in spite of that, you are still
searching for a way to make your vim/ruby/rails coding more productive. First
of all, you need some plugins even you are still not aware of that. I mean you
have rails.vim, NERDTree and FuzzyFileFinderTextMate, don’t you? Obviously
what I am saying is kind of a joke but, as always, it’s a bit of reality too.

## rails.vim

There are some things you need to consider if you plan to use vim for Rails
development in a productive way. You should think about what you really need
to improve when you are coding a Rails project with vim. Vim is a very
powerful editor, I love it and if you are reading this post the odds are that
you love it too. Well, all vim users know that its powerful features need to
be contextualized for an effective use. Based on my experience, one of the
most negative and unproductive aspects of vim/ror combination is represented
by the following common situation:

When you are working on a feature that involves many files you have to switch
among them continuously. It implies that you have to close the file you are
editing, navigate your file-system to find your next file and open it for
editing, which could become a WTF work-flow very quickly. A first glance
solution could be to open all the files you want to edit with the _-O/-o_ vim
option but, come on, nobody knows how many files have to be edited before the
work starts.  For example, consider the problem of editing a view, say an
index, and the correspondent controller. You edit the controller to dig some
records out, then you go to a browser and discover you need an extra field in
your awesome HTML table. So you have to close the index file and open the
controller file with vim. Yes, I am talking about a few seconds but, you know,
a few seconds spent a great number of times in a day mean a waste of time. The
solution for this problem is called rails.vim by our true hero
[tpope](http://tpo.pe/). This plugin isn’t just a must-have for the vim/ror
combination, it’s your only choice because it’s simply awesome. Probably you
are familiar both with the goto File _gf_ vim feature and with the vim
command-line. Well, tpope did an incredible job to make our vim life simple,
and the aspect that hits me more is the pure vim spirit in which it has been
developed. The _gf_ feature of vim is extremely useful even with default
behaviour (take a look at
[help](http://vimdoc.sourceforge.net/htmldoc/editing.html#gf)) but rails.vim
has made goto file _Rails oriented_. Practically, rails.vim adds a bunch of
your project directories to vim path. This feature is sure to make you happy.
Please, try to open a controller, put the cursor on the name of a model, then
type _gf_. Voilà! rails.vim opens that model for your editing pleasure.
Furthermore, this incredible plugin gives you a number of extremity useful
command such as _:A_ or _:R_. Digging into rails.vim features is a real
pleasure, there are commands like _:Rcontroller_, _:Riew_ and _:RModel_. I
guess it’s not a problem to figure out what they do. The aspect you’ll love
more is that the plugin commands work in the vim way. In addition to all these
nice features, rails.vim can do for you other nice stuff like automatic
partial extraction, interfacing rails scripts and integration with other
awesome plugins. So, go straight to
[http://rails.vim.tpope.net/](http://rails.vim.tpope.net/), download and
install it. I can assure you - the boost of productivity will be incredible.

## FuzzyFinderTextMate

So you have just solved your problem with directories without leaving vim. Now
you have to face other tiny problems that occur while editing Rails projects.
Fairly often I run into a small problem that really annoys me: I don’t
remember the exact name of the file I need to read/edit or where exactly it is
stored. This situation can be a problem, imagine the use case: _"How on earth
did I call that lib?" "Where the hell is that *wtf.rb*?"_ - you could waist a
minute or two every time you run into this problem. Obviously, there are a lot
of solutions to this problem and the best one, in my opinion, is the
[FuzzyFinder](http://www.vim.org/scripts/script.php?script_id=1984) with the
improvements of
[FuzzyFileFinderTextMate](http://weblog.jamisbuck.org/2009/1/28/the-future-of-fuzzyfinder-textmate)
by another true hero [Jamis Buck](http://weblog.jamisbuck.org/). I am also a
Java Developer (don’t give me away) and the only thing I miss (I swear it’s
the only one)  is the ctrl-shift-r that you can find either in Eclipse or in
Netbeans. Practically, the Find-Resource is a very nice feature you can use
when you want to find a file “project scoped”. This functionality is fairly
famous in the Rails eco-system because of TextMate “cmd-T” feature, and the
fame is well-deserved. I mean once you start using it you will never stop.
However this plugin has a tiny but annoying problem. By default,
FuzzyFileFinder use the current directory _*"."*_ as root directory for
performing searches. When you want to open a file being in a sub-directory of
your Rails project, say ‘app/model/’, you start searching for it but
FuzzyFileFinder won’t be able to find it if your file is not placed in
‘app/model’. In such a situation you lose all the power of FuzzyFileFinder.
You have at least two ways to solve this problem. The first one uses a
function made available by rails.vim:

{% highlight vim %}
autocmd User Rails let  g:fuzzy_roots = [RailsRoot()]
{% endhighlight %}

Adding that line to your .vimrc solves the problem for you. In fact, when you
open user.rb being in ‘app/model’ and perform a search, FuzzyFinderTextMate
will use your project root as a its root directory. Just to clarify the things
said consider this example:

{% highlight bash %}
[lucapette@hal9000 code ]$rails new demo -m rails-templates/basic.rb && cd demo
[lucapette@hal9000 code ]$cd app/controller
[lucapette@hal9000 code ]$vi application_controller.rb
{% endhighlight %}

Please consider you don't necessary have to cd in 'app/controller' because
it's likely you have set the
[autocmd](http://vimdoc.sourceforge.net/htmldoc/autocmd.html) feature in vim.
When you trigger a FuzzyFinderTextMate search _*without*_ the previous
configuration you'll see something like that:

![/img/fuzzy_finder_not_configured.png](/img/fuzzy_finder_not_configured.png)

_*With*_ the previous configuration you'll see something like that:


![/img/fuzzy_finder_configured.png!](/img/fuzzy_finder_configured.png)

Another way to solve this problem involves two things. First of all, this
solution works only on the condition that you store all your projects in a
single directory, such as /home/lucapette/code, and that you have no problems
with using a tiny vim plugin I wrote a couple of weeks ago called
codepath.vim. For more information about it take a look at
[https://github.com/lucapette/codepath.vim](https://github.com/lucapette/codepath.vim)

## NERDTree

So we solved another problem and I think we can solve at least another one
now. When I started using vim on a daily basis, a feature I wanted to have was
a good way of navigating the file-system tree. As many other vim users, I run
into [NERDTree](https://github.com/scrooloose/nerdtree) plugin and I started
using it straight away. NERDTree is a fabulous plugin that produces a window
like the following:

Furthermore, it comes with a handy mapping to open sub-directories and files
in your vim instance. I confess I don’t use it very much but in certain
situations it is absolutely useful. Traversing your project directories could
be a zen way of thinking about the project itself, in such moments NERDTree
will give you a hand.

## Wrap-up considerations

While writing this post, I have deliberately omitted all the effort and all
the hours spent configuring vim. This choice is a consequence of two simple
ideas. First of all, I hope you could have focused yourself on what you need
to change in vim for Rails development. Secondly, I’m a free person and I
don’t like it when someone tells me how to configure my tools of choice to
their own taste. That doesn’t mean though I don’t like to read other
configurations, indeed, sources like
[https://gist.github.com/gists/search?q=vimrc&page=1](https://gist.github.com/gists/search?q=vimrc&page=1)
can be a great source of inspiration and a good way of learning new things.

### Resources

A few links:

- [rails.vim](http://rails.vim.tpope.net/)
- [NERDTree](https://github.com/scrooloose/nerdtree)
- [FuzzyFinderTextMate](http://weblog.jamisbuck.org/2009/1/28/the-future-of-fuzzyfinder-textmate)
- [Configuration tips](http://codeulate.com/2010/02/installing-fuzzyfinder_textmate-textmates-cmdt-in-vim/)
- A bit of advertising: [codepath.vim](http://www.vim.org/scripts/script.php?script_id=3435)
- Here too: [my dotfiles](https://github.com/lucapette/dotfiles)
