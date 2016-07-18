---
title: A review of The RSpec Book
description:  A review of The RSpec Book by David Chelimsky. Published by The Pragmatic Programmer in Dicember 2010
keywords: the rspec book, ruby, book review, David Chelimsky, tdd, bdd, cucumber
layout: articles
---

As usual, my considerations grouped by chapter:

### Introduction

The book starts with an introduction to the reasons behind BDD. It’s a cool
introduction, small and clear. It’s very useful if these topics are a closed
book for you. To cut a long story short, if you want a spectacular and small
introduction to BDD/TDD reasons watch [this](http://vimeo.com/23061155) by
[Corey Haines](http://coreyhaines.com/).

### Hello

The chapter follows the every-good-programming-book-starts-with-a-hello-world
rule. The author will give two simple examples: a spec with the class
described by the spec itself and a cucumber feature with its step definitions.
If you already know this stuff you could skip this chapter.

### Describing Features

The chapter starts with a brief description of a game that will guide the
reader throughout the book. The author explains the rules of the game in a
nice way. He describes how to extract stories from a project and write
cucumber features and scenarios. If you are new to cucumber you’ll find this
chapter enlightening.

### Automating Features With Cucumber

Writing features and scenarios is like writing in less or more plain English.
That is nice but it’s not strictly related to the quick feedback you need
while developing. So the author introduces the step definitions to you and the
single parts of a step: given, when and then. A very clear explanation.

### Describing Code With RSpec

Cucumber is your friend when you are at the application level but, when you
need more granularity in your automatic tests, you would like to use RSpec.
The chapter presents the anatomy of a spec. The first paragraphs are
interesting, the point of view of the author is simple and clear. It explains
details without wasting your time. Then it goes on with the red/green
technique and you’ll read how to describe code behaviour (it’s all about
behavior! would say a nice [guy](http://dannorth.net/)). The chapter finishes
with refactoring. BDD gives you confidence with refactoring. That’s why I’m in
love with it.

### Adding New Features

When you add a new feature to a project there are chances you will break both
your features and your specs. That’s just fine, the author will guide you in
adding new features in the way you will get all things working and go home.

### Specifying An Algorithm

This chapter is one of my favourites. It contains a number of important
things. First of all, it gives you a piece of advice you should follow: start
with the simplest thing and then go on with the next simplest. Following this
path you will find nice opportunity of code refactoring without losing your
confidence with what you’re doing. If you break something, your specs will
tell you. In short, rapid feedback is the key to success.

### Refactoring With Confidence

I’ve just said that the previous chapter is one of my favourites. Well, maybe
this one is even better. You get to know what code smells are. A code smell is
“a hint that something has gone wrong somewhere in your code”. It’s a very
enjoyable chapter.

### Feeding Back What We’ve Learned

This is a wrapping up chapter that will show you how to experiment with code
in order to understand if there is room for improvements.

### The Case For BDD

The part of the book devoted to BDD as a practice and a technique starts with
this chapter. The author will give you a bit of background about BDD, some
fundamental reasons behind it. A very readable chapter.

### Writing Software That Matters

The chapter goes beyond the reasons and gives you a concrete perspective of
how to apply BDD to projects.

### Code Examples

The chapter covers all the basic syntax of RSpec. It is very informative and I
think you’ll enjoy it.

### RSpec::Expectations

I really liked this chapter because I of the approach of the author to
explaining things. It is detailed and simple. In particular, I enjoyed the
paragraph “How It works” related to the have methods.

### RSpec::Mocks

The chapter explores the world of mocks and stubs. It gives you a complete view of names and options that you have when you need mocks.

### Tools And Integration

RSpec has a nice executable, you can use it in a terminal. The author will
show the numerous options the executable has. Furthermore, he will give you a
short description of how to integrate RSpec with Rake, autotest and TextMate.

### Extending RSpec

RSpec is a polite Ruby citizen. This chapter covers configurations aspects you
need to know if you want to change the default behaviour of some parts of
RSpec.

### Intro To Cucumber

The chapter will give you an effective introduction to the crucial aspects of
cucumber.

### Cucumber Details

And this one goes straight to cucumber details. Informative.

### BDD In Rails

Rails is everyone’s framework. This chapter will tell you how to get a good
working BDD cycle in Rails. Furthermore, it explains how to set up a Rails
project with RSpec.

### Cucumber In Rails

Like the previous chapter but for cucumber.

### Simulating The Browser With Webrat

Webrat is a nice DSL that will help you to test an application *simulating the
browser*. It makes it possible to test how various layers of a Rails
application work together.

### Automating The Browser With Webrat And Selenium

Webrat helps you to simulate the interaction with your application as if the
test were executed by a browser. However, this can’t help with pages that have
many javascript features. The chapter covers basic aspects of integrating
RSpec, Webrat and Selenium.

### Rails Views

The chapter tries to reply the question “Why do I have to test views in
isolations?” and gives nice reasons. It teaches you how to test your reails
views and how to mock ActiveRecord Models.

### Rails Controllers

As the previous one but for controllers.

### Rails Models

As the previous one but for models.

The book contains three appendixes and the first one is wonderful. You’ll read
a nice introduction to a really wonderful project:
[rubyspec](http://rubyspec.org/). I strongly recommend you to take a look to
this project.

What I liked most
-----------------

This book covers topics I like very much, so it would be strange if I disliked
it. **You surely have to read this book** if you care about topics covered.
What I really likes most is the care for details. For example, you’ll find
many things covered with implementation details about the framework. This
approach increases the quality of a technical book and I’d like to see this
kind of details in other books too.

What I disliked most
--------------------

Nothing in particular. The book covers many other things apart from RSpec and,
ironically, this could be considered a flaw because you would prefer to stay
focused on the framework. However, the other topics are quite interesting to
read so I don’t consider it to be a problem.
