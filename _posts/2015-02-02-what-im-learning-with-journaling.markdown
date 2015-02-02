---
title: "What I'm learning with journaling"
description: thoughts about journaling
keywords: journaling
layout: articles
---

A few months ago I started writing a journal and I'd like to share some
thoughts about journaling and why I'm still doing it. I think it's something
worth giving a try.

## I'm not sure why I started journaling

Let's start with why I started. I find this one particularly funny. I don't
really know. I didn't have an actual reason to try journaling.
I've seen people around the internet talking about it and started pondering if
doing it would be positive for my mind and my life in general. What I
generally search for are techiniques to cope with my lack of organisation and
I thought journaling would help in this regard because most folks are saying
it helps clear thinking, it helps organising a day. That was almost all I had
when I started considering it and since it was an easy try I started searching
for how to write.

## Of course I use vim (with a few stupid tricks)

If you have a look around you'll realise there are a lot of apps for
journaling. Most of them have a great integration with smartphones and allow
you to attach media files such as pictures to your entries. I did consider
using one of them, namely day one which looks gorgeous, but then I decided to
approach this new activity the same way I approach a program. I wanted to make
it work and then I would start to consider making it good if needed.
I spend most of my day in a terminal so I thought to actually just use Vim and
an alias to make the process pleasant and my mind focused on the matter I'm
writing about. After playing a couple of hours with the idea I came up with the
following:

- I have a `j` alias which opens a journaling file with the current date.
- I use [goyo](https://github.com/junegunn/goyo.vim), a plugin that makes it
  very easy for me to focus on the current paragraph.
- I use a specialised colorscheme since colours do help my contextual memory.

That's mostly it. It's probably worth mentioning I use _tags_ to give some
context to my entries. I ended up using only `@personal` and `@work` which
have obvious usage.

## I don't really review things yet and I think it's OK

After a couple of months of writing entries almost every day I started asking
myself what to do with the content produced. I wanted a way to get a sense of
what I was writing. I like numbers, stats and graphs so I thought it would be
good to have some visualization of my activity. I wrote a
[sinatra](http://sinatrarb.com) application that serves a page that renders a
calendar using a nice JQuery [plugin](http://fullcalendar.io). Now I can
see how many entries I have per day (grouped by tag) and a trivial word count
to get a sense of how intense my activity in the given day was.
Now I have a fancy way of reviewing what I write and I actually never do. I
basically use the application only to figure out if I'm writing in a
timeframe or not. I almost never read what I wrote. When I realised I wasn't really
reviewing what I was writing I had a small journaling crisis. I though it was
stupid to write all the time and then not to use the content I was producing at
all. So I stopped writing for a few days. Maybe a week or so. But I suddenly
missed it. I felt I needed to cover some topics in my journal. Just writing about them
was helping me to cope with stress or with a particularly tricky work related
problem. And I decided to ignore the review part for now. I don't review my
entries and I feel good about it anyway.

## English? Italian? Both?

If you've ever heard me speaking you know pretty well I'm not a native speaker -
it feels like I'm one of the characters of Donnie Brasco or the
Godfather. That brings up a discussion about what language I should
use while writing. Now the interesting thing is: this discussion I had
with myself started a couple of months after I had already been writing all my
entries in English. It felt natural as I do have more entries tagged
`@work` and I speak only English at work. So not paying the price for the linguistic
context switch was a natural decision. Infact, it wasn't a decision at all. At
some point though, the number of `@personal` entries increased so I started
missing my native language, the only language I can use when I'm in a very deep
conversation with myself. This peek in `@personal` entries made me think about
mixing languages. I even asked around about this specific topic. I tried
using Italian for `@personal` entries and English for `@work` which I thought
to be a crazy idea and it actually was. It didn't really work so in the end I
use only English. In a way, I think it's better. I don't really own this
language. I have to simplify my thinking. I can't workaround problems with my
property of the language as I mostly don't have such a thing in English. I'm
forced to use my favourite mantra _less is more_. And I do benefit from this
choice in the end.

## I should just blog more

I wrote about the process itself because I was searching for some sort of
conclusion about journaling. Some answer to why I would do something everyday
without a strong reason for doing so. I'm very happy with journaling because
it made me realise I just love writing. I did know about this already. I wrote
a lot in my life (even a novel in Italian when I was 20). And I always
connected writing to deeply emotional feelings. Which holds true when it comes
to creative writing. I can write a short tale in one shot when subjected to
emotions and I've always disliked this connection I had in my mind. I
enjoyed writing but I did not enjoy to wait for emotional distress in
order to be able to create something. Journaling changed the game and made me
realise something that you may consider obvious, but I can assure you it
wasn't for me. It made me realise I can enjoy the act of writing itself. It
doesn't have to be creative writing, I don't really have to write a novel or a
short tale or a free poem to love writing. I can write about myself in a
journal, I can write more blog posts about things I find relevant and worth sharing
(maybe they aren't and that's why I love feedback). I can just write more and
enjoy the act of writing itself. So my suggestion is giving journaling a try
if you've ever considered doing so. It may turn to change something for the better in
your life and I don't think there are many activities in our life that can
actually change it for the better with little effort.
