---
title: "Vim for Rails developers: Lazy modern configuration"
description: How I think you should deal with configuring Vim
keywords: vim, rails, configuration, pathogen.vim
categories:
- vim
- rails
layout: blog
---
{% include vim_for_rails.html %}

Vim is very customizable, it has thousands of plugins suitable for everyone's needs. Each of us uses some of them. Furthermore, it has a good number of files you can use to configure some aspects of the editor and it would be very nice to keep all this stuff under a version control system. But, before I try to do my best to explain what I mean with lazy modern configuration, I would like to say some words about Vim distro. In short: **Do not use a vim distro**. This is the most important thing to consider about configuring vim. So I'll repeat it: **Do not use a Vim distro**. I prefer to sound unpopular but it's not the Vim way. If you need an Editor that makes things for you, go look for something else. Vim is just the opposite, Vim is the perfect editor that leaves you the possibility of making things the way you prefer. With a Vim distro, you'll never master Vim or at least you'll reduce the chances to learn how Vim really works. I'm not totally against distro, they can inspire you. It's like code reading for configurations: know them, get inspired by them but choose your own way. I'm not saying you should start from scratch. If you're using a Vim distro at the moment you could do the following exercise. Think about what you really use all the time inside the Vim editor that is given by a plugin. The odds are you'll come up with three or four plugins at the moment and a number of mappings. So you could grab those plugins and start from there.

After my little battle against distros, what does *lazy modern* configuration mean? Or, at least, what do I mean?

Modern
------

Programmers are [lazy](http://c2.com/cgi/wiki?LazinessImpatienceHubris). And it's a good thing. Being lazy can help you become a better programmer. If you're lazy, you will write programs that do stuff for you. Regarding Vim, you want a modern way of automatic handling your vim configuration for tasks like new installations and plugins updating. So modern means "do not copy and paste files over configurations directories, do not try to update plugins by hand". It's 2011 and we need a good way of managing all this stuff. As many of you already imagined, I deliberately steal the modern adjective from a good nice [article](http://tammersaleh.com/posts/the-modern-vim-config-with-pathogen).

Lazy
----

Spend your time configuring something only and only when you really need it. Highly configurable tools could be a double-edged sword, and Vim is the most incredible tool I've ever used from this point of view. While hanging around the web you meet nice mappings, nice plugins, nice stuff and you get excited about suddenly using them. Please simply don't. When I run into new plugins or mappings and find them useful, I bookmark them and go ahead. Then, while working in Vim, it comes to my mind I could use that bookmarked stuff. Now you're thinking that I put that new wonderful thing into my configuration. Actually I don't, I do my best to resist. And I make this process happen many times. Only when I get really tired of desiring that particular thing in my workflow, I eventually go find it and put it into Vim.
I can assure you this process will work very well for various reasons:

- You really understand what your configuration lacks when you run into the same need many times in a row. That's the main point.
- You don't make your configuration dirty.
- You use only what you need.

    *Perfection is attained, not when no more can be added, but when no more can be removed.* said [someone](http://en.wikiquote.org/wiki/Antoine_de_Saint-Exup%C3%A9ry).

Taking care of plugins
----------------------

Now, if you want to obtain a real lazy modern configuration you have to do at least the following things:

- Choose a plugin manager
- Put your vim directory under a version control system
- Make the vim directory update process easy
- Make the plugins update process easy

Now you could choose the plugin manager you prefer, there are many of them. But I strongly recommend you to use [pathogen.vim](http://www.vim.org/scripts/script.php?script_id=2332). [Tpope](http://tpo.pe/) wrote it, and it should be enough to use it. No, seriously, I've played a bit with other solutions but I still prefer pathogen. Citing the README: "Manage your 'runtimepath' with ease. In practical terms, pathogen.vim makes it super easy to install plugins and runtime files in their own private directories." And this is the reason why I really love pathogen. You simply have to put a plugin in the bundle directory in order to use it. This makes it very easy to test plugins too, I do it all the time. It is very easy to setup and it's so awesome you can even bundle the plugin itself. If you don't use it and you want to give it a try consider using the following steps:

- Create the .vim/bundle directory
- Put pathogen.vim there
- Put on the top of your .vimrc the following lines:
{% highlight 'vim' %}
    runtime bundle/pathogen/autoload/pathogen.vim
    call pathogen#infect()
    call pathogen#helptags()
{% endhighlight %}

Now, you could move all your plugins in the bundle directory. They should keep working fine. This is a good starting point to make your configuration modern and clean but it still lacks the lazy part. You can't update your plugins easily. And in my point of view, *easily* should mean maximum one command to update plugins. So, once again, you can achieve such a result in many ways, but you should go straight with git. Git is widely used in our (as a note: our means rails+vim users) world and the odds are you will find the plugin you want to add on github. Actually, there is even a [http://vim-scripts.org/](http://vim-scripts.org/) project. It's *sweet*. Another great reason to adopt pathogen.vim is the natural integration with [git submodules](http://book.git-scm.com/5_submodules.html). With submodules and pathogen.vim you can get a lazy modern vim configuration. Now, I want to say just a couple of words about my way of using this stuff to make more clear what I mean with *easily*. I added to the pile of tools just another one. I'm a Rubyist, not a Ruby Hero but an ordinary Rubyist. So, for me, solving a boring task with files and the shell means *Use Rake*. So I used Rake but you could use a bash script or whatever else. The real point is focusing on the two above mentioned steps. When I want to update my vim configuration directory I type:

{% highlight 'sh' %}
rake
{% endhighlight %}

and when I want to update my plugins I type:

{% highlight 'sh' %}
rake update_bundles
{% endhighlight %}

Just a command per step but please be careful. I tell you once again: you don't have use my rake tasks or someone else's solution. Do what you prefer, use the tools you like but make it easy. With an easy process it will be simple to add and remove things from Vim. **You'll never find the right configuration**, you will change your coding habits, your needs will change as well. You'll learn a new language or give up using another one. So, you need a simple process to take care of this ever-changing status because you don't have to waste too much time configuring your editor.

Runtime directories and files
-----------------------------

We've just talked about a big part of the problem. But there is another thing to consider. Your own configuration consists basically of two things: the plugins you use and all the rest. We took care of the plugins, now we have to think about the rest. That means your vimrc and all your files in the other Vim runtime directories. Now before we talk about how to keep your files clean, we need to spend sometime talking about vim runtime directories. Every time you run Vim, it searches in a number of directories in order to load default and custom preferences. This process is described briefly in [runtimepath](http://vimdoc.sourceforge.net/htmldoc/options.html#'runtimepath'). Now, you have to know what some of these directories are if you want to keep things clean:

- after

  The after directory is a very important one. You can use it to override system settings, it has the same structure of the entire vim configuration directory (itself excluded).

- autoload

  This directory is a bit underused and poorly known. The nice thing is that it works exactly how a rubyist imagines it to work. You can put in this directory all the functions you want to call with a particular mapping or functions without problems. The nice thing is that these functions will be only loaded the first time you call them.

- colors

  Put your colorschemes here and then you could load them.

- compiler

  The files you put here won't be loaded by Vim at startup but you can use them with the [compiler](http://vimdoc.sourceforge.net/htmldoc/quickfix.html#:compiler) command in order to set the errorformat and the make options.

- ftplugin

  The files in this dir follow the simple convention based on the filetype of the buffer you are opening with Vim. So if you put here a file called ruby.vim, it will be loaded only when you open a Ruby file.

- ftdetect

  This directory follows the same convention of ftplugin but serves a different purpose. You can use this dir to detect filetypes when a particular condition is met. See [docs](http://vimdoc.sourceforge.net/htmldoc/filetype.html#ftdetect) for a good example.

- plugin

  All the files that you put here will be automatically loaded by Vim when you open it.

Now you have some information to clean your vim directory and you can focus on *cleaning and removing* stuff. Let me tell you what helped me a lot:

- Divide your mapping in two types

  - General mappings

      Mappings you will use in all files.

  - Filetype mappings

      Mappings you will use, for example, only with Ruby files or with Coffeescript files.

- Organize your general mappings

    I've used a dir with some files in it, each file groups a number of mappings according to its own name. It will help you to focus on what you really need and what you currently have.

- Put your filetype based files in the after/ftplugin directory and use the [buffer](http://vimdoc.sourceforge.net/htmldoc/map.html#:map-<buffer>) argument for mappings, it's an important feature and you should spend some time to understand it. Maybe a bit poorly known. Thus, you won't mess Vim configuration for those files.

- Order personal settings and group your plugin settings in your vimrc

    Use the criteria you find more logic for your setting. But keep them ordered. When you change something, you'll know where to go. Grouping your settings by plugin is a good idea too.

- Comment your settings

    I'm writing about it because I would force myself to do it too. It's important even for obvious things. If you have your vim directory on a public service like github or bitbucket, you're being kind to other people.


OK but why?
-----------

I know all this configuration stuff might seem a bit paranoid but I think I have a strong point to support my ideas: You won't stop learning about Vim. I mean unless you're a [Vim](http://tpo.pe/) [Hero](http://stevelosh.com/). You're are going to learn a thing a day with your editor if you choose Vim. So a lazy modern configuration sure can help you to stay focused on what you are doing. Whatever it is learning Vim itself, writing code, blogging or something else.
