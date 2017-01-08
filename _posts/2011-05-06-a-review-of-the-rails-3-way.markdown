---
title: A review of The Rails 3 way
description: Published by Addison Wesley in Dicember 2010
keywords: the rails 3 way, book, review, Obie Fernandez
category: reading
layout: articles
---

This book doesn’t need an introduction. [Obie
Fernandez](http://obiefernandez.com/) has done an incredibly awesome work with
this book, many of us already knew it. Generally, my reviews start with a tiny
description of the reviewed book, then go on with considerations grouped by
chapter and finish with a general consideration about what I liked and
disliked most in the book. But… [The Rails 3 way](http://tr3w.com/) deserves
an exception. This book should live on your desktop if you’re a Rails
developer. Indeed, I could stop the review with the previous sentence. Really.
I mean, only if you are Obie Fernandez or “put a name of a Rails core team
member here” you can escape that rule. So if you are impatient, you could even
not read this review. Buy the book and you’ll be happy :)

Well, as usual, my considerations grouped by chapter:

### Rails Environments and configuration

The book starts where a Rails application bootstraps. Nice thing. The author
will guide you trough all the configurations of Rails. Starting with bundler
and finishing with logging, all the aspects of configuring a Rails app are
well-explained and perfectly detailed.

### Routing

In my humble opinion, routing is one of the killer features of the Rails
stack. It has an elegant, simple and powerful APIs. Obie explains in detail
all the aspects of the routing API. Furthermore, you’ll find a good discussion
about \*path and\_url version of a route helper, it’s a topic I enjoyed a lot.

### REST, Resources and Rails

The first part of the chapter will show you a great quality of the author, the
one I liked most. His way of expression is clear and simple, he will guide you
through one of the most interesting features of Rails and you will be very
satisfied. I really liked the short description of each of the REST actions.

### Working with controllers

The chapter covers very well all the features of Rails related to this topic.
I was very pleased while reading the good introduction to Rack. Obie just
gives you the right amount of background about every topic he covers.
Obviously, the chapter covers everything about controllers.

### Working with ActiveRecord

I think it’s fair to say that ActiveRecord is one of the main reasons why
people approached Rails. So I was looking forward to reading how a good writer
like Obie Fernandez introduced the topic. And, once again, I really liked the
approach. The introduction to ActiveRecord is clean, linear and meaningful. He
described all the stuff related to attributes, queries and options you have. I
really enjoyed how the author chose to write about the ActiveRecord world, the
separation in three chapters is a winning choice.

### Active Record Migration

The chapter is short but extremely informative. I found useful the description
of all the Rails’ tasks and the columns mapping table.

### ActiveRecord Associations

“Here be the dragons” would say someone. By the way, let me say it straight
away: if you are new to Rails this chapter will save you much time. If you
aren’t new then you’ll enjoy a great presentation of all the associations
ActiveRecord implements. If the book had only this chapter, it would be still
worth buying.

### Validations

The chapter will give you all the required information about the topic. I
really liked the considerations about how you can make your validations more
DRY.

### Advanced Active Record

Although the word advanced could give the impression of covering difficult
topics, the chapter will simply cover all the under-known aspects of
ActiveRecord like callbacks, STI, polymorphic relationships and etc..
Furthermore it will give you a nice introduction about how to extend
ActiveRecord.

### Action View

The chapter starts with a description of how Rails renders templates, that’s
just the right starting point. Then, the author talks about decent\_exposure,
a very nice gem for declarative exposing of data to the layer view. I will not
suggest adopting this way of preparing information for the view layer, but I
can say I like opinionated people, so I liked this part of the chapter.
In my opinion, the best part of the chapter is the one about partials. Obie
Fernandez covers all the aspects in a very complete and simple way, you’ll
enjoy it.

### All About Helpers

Helpers are helpers, there is no much to write about them. But once again the
author made a great work. He presents *all about helpers* in a way you can
only enjoy. There is just everything you need about helpers in this chapter.

### Ajax on Rails

In each book we read there’s always something you don’t like much, even in a
great book like this. I have to confess I didn’t like this chapter a lot but,
in a certain way, that’s not a problem of the book. I mean, a topic like Ajax
on Rails deserves an entire book like this one, so my feelings could be
justified by this lack. However, the chapter deserves attention because it
covers nice stuff.

### Session Management

Session management is one of the controversial aspects of Rails. I really like
the position of the author and how he explains the whole philosophy behind the
“minimalistic” approach of Rails to session management. He also covers
performance aspects.

### Authentication

The chapter covers the most notable solutions currently out there: authlogic
and devise. I read this one hastily, it’s nice and covers very good solutions.
By the way, I’m not that sure about the inclusion of this topic in a book
called “The Rails way”.

### Xml and activeresource

The chapter covers aspects of Rails that aren’t well-covered and well-known.
You’ll find very useful information, I’ve found out that to\_xml is more
powerful than I thought :)

### Action Mailer

I have a strong Java background and the very first time I successfully sent a
mail with Rails I was happy beyond words. ActionMailer APIs have been a major
change in Rails 3, so the chapter is very interesting. I really liked the
approach of the author about all the APIs changes between Rails 2 and Rails 3.
He never compares the APIs, he talks about Rails 3 as if Rails 2 didn’t even
exist. You’ll appreciate that, it makes things very clear.

### Caching and Performance

The chapter covers all the techniques Rails provides for caching stuff. The
topic is huge and this chapter can be considered a nice and simple
introduction to it.

### RSpec

RSpec is a wonderful framework. It has a great, sexy and simple syntax and
Obie Fenandez deserves another compliment for the very good introduction he
has written to it. If you use RSpec on a daily basis you could skip it but I
suggest you to read it in any way. If you aren’t familiar with RSpec you’ll
enjoy it very much.

### Extending Rails with plugins

I think this topic is gaining great interest among the majority of us and,
once again, I can say that the chapter is very well-written and covers the
topic very well.

### Background processing

The chapter covers notable solutions for handling jobs as delayed\_jobs and
resque. As for the chapter about authentication, I’m not quite sure about the
inclusion of this topic in a book called “The Rails way”. But it’s worth
reading.

Generally speaking, I don’t like appendixes because I don’t like reading
topics covered shallowly. However, the appendixes of Rails 3 are a very
pleasing exception. They cover ActiveSupport and ActiveModel APIs, you’ll find
them useful.

What I liked most
-----------------

If you have read the introduction to this review you already know what I think
about this book. **There are no excuses, if you are seriously interested in
Rails you have to buy this book. No more to say.**

What I disliked most
--------------------

This is nearly a perfect book in my opinion. If I have to be overcritical
about it I'd say that, although I really liked the choice of haml, I would
have preferred to read some sort of introduction to it. But… **I’m not that
critical, this book is wonderful. Buy it, do yourself a favour**.
