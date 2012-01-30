---
title: 'Vim for Rails developers: browse Ruby, RSpec and Rails docs quickly'
description: 'Install vim-ruby-doc and vim-jquery-doc for better API docs browsing'
keywords: vim, ruby, rails, rspec, jquery, API doc, apidock.com
categories:
- vim
- rails
layout: blog
---
{% include vim_for_rails.html %}

In this post I just want to bring to your attention a little plugin I extracted
from my [vimfiles](http://github.com/lucapette/vimfiles). We all need to read
some API docs during our work day. And I dislike a lot the idea of opening the
browser, going to a website, typing something in (very often just a single
word) and waiting for the result. So I started to search for something better
and I found [apidock.vim](https://github.com/mileszs/apidock.vim) that does a
good job. I wrote something very similar to the plugin for my vimfiles because
the plugin itself didn't fit my needs very well.

Well, I was quite happy with the result. Finally I got something I liked about
doc browsing and Vim. I just had to type a particular mapping and voilà
suddenly I was reading the doc I was looking for.

So, just a couple of days ago, I found out that
[api.jquery.com](http://api.jquery.com) has a very nice feature. In fact, if
you go to [http://api.jquery.com/each](http://api.jquery.com/each) it just
works fine.  It works fine even if you go to
[http://api.jquery.com/ea](http://api.jquery.com/ea). I searched for a plugin
similar to what I had in my vimfiles and didn't find anything, so I decided I
could have created it. And here we are. It's a very small plugin, you can find
it [here](https://github.com/lucapette/vim-jquery-doc). When your cursor is on
a jQuery method, type `JJ` and the plugin will open a new tab in your browser
(or a new instance of the browser) to the related docs.

After writing the jQuery plugin, I thought it would be very simple to create a
tiny and flexible plugin for Ruby, RSpec and Rails. Yesterday I released
[vim-ruby-doc](http://github.com/lucapette/vim-ruby-doc). It works in the same
manner as vim-jquery-doc does. When your cursor is on something you would look
up on apidock.com, type:

- `RB` for Ruby
- `RS` for RSpec
- `RR` for Rails

and the plugin will open a new tab in your browser (or a new instance of the
browser) to the related docs. Obviously, I added options to both the plugin, in
case you need other mappings or another command. Check out the README for
further information.

I hope you can find it useful. Actually, I use it all the time and I'm asking
myself what I can do to improve it. Maybe you have some ideas.
