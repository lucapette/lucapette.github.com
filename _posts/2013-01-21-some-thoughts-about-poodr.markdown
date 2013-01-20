---
title: A few thoughts about Practical Object-Oriented Design In Ruby
description:  A few thoughts about Practical Object-Oriented Design In Ruby by Sandi Metz. Published by Addison-Wesley in 2012
keywords: object-oriented programming, ruby, book, review, poodr, Sandi Metz
category: books
layout: blog
---

Object-Oriented Design is a big part of the debate the Ruby community has had
in the latest couple of years. People are writing blog posts, giving talks at
conferences and writing books on the subject. OOD is nothing new, let's say
it, but I think the status of many Rails projects is the reason why there is
all this attention to the topic in the Ruby community. Be careful I'm not
blaming the framework, I'm making a living by using it. I'm just saying that if
you're writing non trivial applications with Rails you generally end up asking
yourself why everything looks so messed-up and is hard to maintain. The first
question I ask myself when I consider reading a technical book is: *is this
book worth my reading time?* Well, I think this book finally fills the gap for
a need that was pretty clear to me: explaining simple OOD that feels like Ruby
using proper examples. So yes, the answer is yes. The book is worth reading,
definitely. And I think the community will benefit from it a lot since
there are still a lot of doubts about OOD.

# The book

OK, let me focus on the book itself now. It explains *simple* OOD that *feels
like Ruby* using *proper examples*. I divide my short review in three
paragraphs as I think the winning in this book is in the words I put in
italics.

## Simple

[@sandimetz](https://twitter.com/sandimetz) writes in a dead simple way. Every
sentence is clear and well crafted. She uses a lot of metaphors in the book and
most of them are just perfect. I'll give you an example of a concept that I
find crucial for basic understanding of OOD. I think messages are the key
concept of OOD; sending messages is the way we make things work in OO
languages. It's the way our objects interact and get their job done. But the
problem is that most of the time we keep thinking about the classes. We write
classes with methods and not objects that send messages. And the author, while
discussing how to find the public interface, came up with a paragraph that I
**love**:

> Changing the fundamental design question from "I know I need this class,
> what should it do?" to "I need to send this message, who should respond to
> it?" is the first step in that direction.

Where the direction is moving from class-based design to message-based design.
Then the dead simple masterpiece:

> You don't send messages because you have objects, you have objects because
> you send messages.

Well, that's the kind of awesomeness you'll find in the book. It's completely
full of sentences so dense and simple at the same time. I think it's the first
technical *Ruby* book in which I was actually highlighting sentences.

## Feels like Ruby

The techniques she presents throught the book will always feel like Ruby code
and not something ported from a different language. I don't want to show you
any example because it would probably be out of context and won't make any
difference. But what I can tell you is the feeling I had while reading the code
in the book. Generally, the code presented is simple and readable. It's exactly
the Ruby code that made me crazy about the language some years ago.

And this is great for two reasons:

- It's the first time that I read code samples in Ruby on the subject that can
help you shaping the API of your objects in a way they become polite citizens
of the Ruby world. Well, with the exception of [Eloquent
Ruby](http://eloquentruby.com/) that is perfect for writing code that looks
like Ruby even though it helps to improve code not from a design technique
perspective, but from the language perspective. So it doesn't count.

- [@sandimetz](https://twitter.com/sandimetz) repeats it many times in the book
that the aim of OOD is reducing costs. I can't agree more and this is the
second reason why I think the code samples are great. While reading articles
about OOD techniques in Ruby, most of the time I had some difficulties reading
the code.  since there were too many levels of indirection or maybe just too
many things.  This felt wrong because Ruby has a clean and simple syntax and it
has to be simple to read. In this book the examples are always very readable.
We spend a lot of time reading code at work, so writing readable code reduces
costs because we'll read code more often than we'll write new one.

## Proper examples

The author did a great job here. In a certain way this point is connected with
the previous one since most of the examples involve code. But the real point
about the examples is that they are abstract enough to let the author talk
about the concepts behind OOD techniques and concrete enough to show you good
pieces of code. And this is definitely a new thing in the world of Ruby books.
There is another very good book out there about OOD in the Ruby community -
[Objects on Rails](http://objectsonrails.com/). The book is great and I
recommend it heartily. But it has this small issue with the blog example. I
talked to a lot of people about the book and I got this sad response from many
of them: "Yeah, it's cool but man it's too much complicated for a blog".  Of
course, that's not book's fault. It's just that we keep fixating on the code.
Because we're programmers. And for this very reason, the code samples are
crucial for the success of this kind of book.

# My conclusion

If you're interested in the topic, this book will be a joy to read. I have a
very long queue of technical reading and I put this book in the middle of it
since I want to re-read it soon. My suggestion is to read it. It's really worth
the time. It's literally full of great thoughts on the topic. I already hope
there will be another book by Sandi Metz in the future.
