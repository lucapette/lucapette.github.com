---
title: "Getting started with Vim"
description: Trying to make Vim's learning curve more gradual
keywords: vim, learning, editor, drew neil, practical vim, tpope
layout: articles
---

A few days ago a friend asked me: "How do I get started with Vim?"
[She](https://twitter.com/lady_jcb) explained to me she tried Vim out for a
few days and enjoyed the idea of working inside the terminal, as well as the
consistency of the experience across different servers. Good reasons, no
doubt.  I collected some notes and some links for her which I decided to turn
into the article you're reading.

My goal is to suggest a path for starting out with Vim without the anxiety and
the frustration this process usually brings about - the editor is _not_ famous
for being easy to start with. As I will focus on the path, I won't be getting
into the details of the topics I will cover. There are awesome resources on
this matter and I will link them at the end of each section.

## vimtutor

Vim ships with an awesome little tutorial. I suggest you start from there even
if you think you already know the basics. It is supposed to take 25-30 minutes
and I suggest you do it in one session. If you have Vim on your machine, you can
type `vimtutor` and start right away. The tutorial is designed to teach you all
the basic commands and concepts. Vim is a [modal
editor](http://unix.stackexchange.com/questions/57705/modeless-vs-modal-editors#57708)
with a variety of
[modes](https://en.wikibooks.org/wiki/Learning_the_vi_Editor/Vim/Modes). Its
nature may be new to you and the tutorial will proceed slowly. Take your time to
complete it.

## Vim has no shortcuts

The next natural step would be to use Vim on a daily basis. But it's not an easy
goal, because editing text in Vim will feel clumsy, there's too much to remember
and most commands are not represented by a mnemonic sequence. For these reasons,
I want to share my understanding of the "Vim way". I wish someone explained this
to me when I started, as I'm convinced the approach makes Vim more approachable.

I ran into Vim during a lab lesson about C programming and operating systems
back when I was at university. It was overwhelming. Nothing in Vim made sense to
me, and my professors were neither friendly nor helpful. All those `dd`, `yy`,
`A` made me wonder why on earth anyone would use Vim. How could I possibly
remember all the shortcuts? I was used to an IDE with all sorts of shortcuts,
but they were easier to remember. Moreover, there were menus with intuitive
labels to help me in case I had forgotten how to do something. Vim commands were
not mnemonic and the problem hunted me for weeks. I ended up just being scared
by Vim and went back to my IDE.

A couple of years after this traumatic experience I gave Vim another try. I was
working with Perl and Ruby at the time, and an IDE did not fit my terminal
emulator centric workflow. Then one day I ran into [text
objects](http://vimdoc.sourceforge.net/htmldoc/motion.html#object-select): it
was the turning point. Nowadays, text objects are the reason why I wouldn't be
able to edit code with any other editor. They let you describe regions of text,
here are a few examples:

- A word
- A sentence
- A paragraph
- A HTML tag
- A function

Vim has a command for deleting text, one for pasting and so on. You can combine
those with text objects and get a powerful small language for text editing. You
can say things like:

- Remove the next three words
- Copy this paragraph
- Change the content of this HTML tag

This is why I say Vim has no shortcuts. I like to describe it this way:

> Vim is a small language for editing text that ships with a small user
> interface.

That small user interface is your editor. Looking at it from this perspective
can be enlightening. You can focus on learning how the language works instead of
learning its standard library by heart. You can focus on thinking about editing
text the "Vim way". I think this way Vim becomes easier to approach and its
learning curve is more gradual.

One other aspect of Vim I wish someone had explained to me when I started is to
focus on normal mode. Vim has multiple modes but one stands out because of its
name. It's called "normal" mode because it's normal to use Vim in that mode. You
do most of your editing in that mode: moving text around, pasting it, deleting
it. All in normal mode. You can combine the focus on normal mode, the idea of
Vim being a small language and text objects:

> Vim has a normal mode to operate on text via text objects.

Links:

- [Vim Text Objects: the definitive
  guide](http://blog.carbonfive.com/2011/10/17/vim-text-objects-the-definitive-guide/)
- [:h text-objects]([http://vimdoc.sourceforge.net/htmldoc/motion.html#object-select)
- [Your problem with Vim is that you don't grok
  vi.](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118#1220118)


## Vim plugins

Vim does not ship with all you need and finding your way around the ecosystem
can be hard. There are many plugins that try to solve the same problems and it's
difficult to pick one. I wrote about how to
[configure](/vim-for-rails-developers-lazy-modern-configuration) Vim in the past
and I still agree with the approach of doing things on your own so you can learn
about Vim. However, if I'd be writing the same article today, I would focus more
on plugin management; things became easier in that regard. Now I use
[Vundle.vim]([https://github.com/VundleVim/Vundle.vim) and I couldn't be happier
about it. I suggest you go ahead and use Vundle too. It comes with a few
commands that make installing, updating and removing plugins so simple that you
do not need to remember anything. Simplicity is the key: you will play around
with many plugins, so adding and removing them has to be as easy as it can get.

People's workflow differs a lot so I'm not going to compile a list of the "100
Vim plugins you can't miss". I will try, however, to provide you with the bare
minimum to get you started.

### fugitive.vim

_You can skip this part if you're not a git user._

[fugitive.vim](https://github.com/tpope/vim-fugitive) is your perfect companion
when it comes to git. Using its author's words:

> I'm not going to lie to you; fugitive.vim may very well be the best Git
> wrapper of all time

It may sound like a bold claim, but I do not think it is. The plugin is really
awesome and has delightful features. The best way to learn how to use it is to
watch a good series of
[screencasts](http://vimcasts.org/blog/2011/05/the-fugitive-series/). I can't
recommend it enough.

### tpope plugins

[tpope](https://github.com/tpope) is not only the author of fugitive.vim. He
writes and maintains an incredibly long list of must-have plugins. My suggestion
is to skim his repository lists and try all the plugins you think you may need.
If I had to pick one, it would be
[surround.vim](https://github.com/tpope/vim-surround). Editing code often means
dealing with "surroundings": parenthesis, brackets, quotes and so on.
Surround.vim helps a great deal with those.

Links:

- [VimAwesome](http://vimawesome.com/)

## Practical Vim

[Drew Neil](https://twitter.com/nelstrom) wrote [Practical
Vim](https://pragprog.com/book/dnvim/practical-vim) and I recommend it every
time I can. It's a perfect book for people that want to deepen their Vim
knowledge. As soon as you get comfortable with using Vim on a daily basis, I
suggest you read this book. It's a wonderful collection of tips and it will
speed up your learning path. I can't imagine a better resource for Vim,  I think
there's a _before_ and _after_ reading "Practical Vim".

Drew Neil published quite some screencasts at [vimcasts](http://vimcasts.org/)
and I recommend them as well. Drew's explanations are clear and easy to follow.
I watched them all and I suggest you do the same.

## Again, how do I get into Vim?

Here are the steps I suggest you take:

- Complete the tutor
- Think about text the vim way
- Get to learn the plugin ecosystem
- Read the best book out there and watch all the author's screencasts
- Happy editing!

Thank you for reading and stay tuned!
