---
title: "Using Flow and jest"
description: Fourth article of the series "my journey with React and its ecosystem"
keywords: react, flowtype, jest, pomodoro technique
category: react
layout: articles
---

This article is part of the series [my journey with React and its
ecosystem](/react.html). If you are not familiar with it, I suggest you check
that out first!

In the previous article of the series, I explained how I introduced a timer in
[passata](https://github.com/lucapette/passata), my playground application for
the pomodoro technique. At the time, the code was part of the `Layout`
component, and I planned to extract the timer to its own class, add some tests
and learn more about ES6, jest and Flow. This was an exciting plan and it turned
out to be even more interesting than I anticipated. Each small step I took
generated many questions, I have always been a fan of such activities.

## How do I test with jest?

[jest](https://facebook.github.io/jest/) is a testing framework and I've wanted
to try it out for a while. I heard good things about it from people I trust and
had a good impression while skimming its documentation. Setting it up took
minutes, I only had to install two packages: jest and `babel-jest`. I got a
first green test [here](https://github.com/lucapette/passata/commit/e1cf076) in
no time, because I deliberately wrote a meaningless test: my goal was to test
the toolchain and understand it better. I considered it a successful test
because it generated many questions:

- Am I even running Flow? I set it up a while ago but now I'm not sure it's
  working.
- If I'm running Flow, am I running it when running the tests?
- How do I make the build fail when Flow reports errors? I believe there's no
  point in annotating the source code otherwise.

I felt slightly overwhelmed, yet I could turn it into excitement. After all I'm
still learning.

## How do I flow?

I turned out I had never run [Flow](https://flowtype.org) after setting it up.
As soon as I ran it again, Flow gave me so many errors that its output was
scary. I decided to investigate the problem and fix the errors before moving on
to integrating Flow with the rest of the toolchain.

I researched the errors Flow reported and understood I needed to install
[flow-typed](https://flowtype.org/docs/third-party.html#using-flow-typed). Most
JavaScript libraries are not written with Flow types, therefore they're
_untyped_. `flow-typed` is a central repository of Flow library definitions, it
provides definitions for widely diffused libraries. The experience with
`flow-typed` was nice. Once I installed it, I only needed to run:

```sh
$ ./node_modules/.bin/flow-typed install
```

The command analysed my dependencies, downloaded all the available libraries'
definitions and provided stubs for the unavailable ones. This
[commit](https://github.com/lucapette/passata/commit/a1f0a98) contains all the
definitions I needed. Finally, Flow detected no errors.

## How do I flow and test?

I read jest [getting started
guide](https://facebook.github.io/jest/docs/getting-started.html) which is
friendly and well written. However, I felt I needed to know more about the
framework matchers and other utilities you normally find in a testing framework.
The [API documentation](https://facebook.github.io/jest/docs/api.html) is clear
and useful but I find its table of contents confusing. For example, the matchers
menu item is labeled
[expect](https://facebook.github.io/jest/docs/expect.html#content); I know it's
technically correct but that did not result in good user experience for me. The
API itself is friendly and familiar to [RSpec](http://rspec.info/) users. I have
always had a soft spot for RSpec so I felt at home with jest.

If there's one situation in which I'm fine with using mocking, it is when I need
to fake time. jest offers a simple API to [fake
timers](https://facebook.github.io/jest/docs/timer-mocks.html#content), and I
was happy to find out that the functionality is builtin. I implemented some
[tests](https://github.com/lucapette/passata/commit/f2e5234) and started playing
with the command line options jest offers. The framework is fast, you can feel
it even with just a couple of tests, and I liked its default output. At first, I
did not understand how to run jest with additional parameters via yarn. But it
was a matter of adding `--` before the additional option as in:

```sh
yarn test -- --watch
```

The `--watch` option I used in this example is quite helpful, I suggest you
check it out.

At this point, I had a setup I liked and a couple of tests I could live with, so
I moved on to figure out how to run Flow when running tests. I ended up with
[this solution](https://github.com/lucapette/passata/commit/305cbdb). I would
prefer more integration between Flow and jest but, for now, it does the job.

## How do I flow and build?

I did some research to answer this question and found out I needed to use
`preloaders`. Webpack documentation was great (as always): `preloaders` were
removed in `2.x`. The documentation explains [how to deal with
it](https://webpack.js.org/guides/migrating/#module-preloaders-and-module-postloaders-was-removed).
I needed to install a plugin called
[flowtype-loader](https://github.com/torifat/flowtype-loader) and to make some
minor changes to the build configuration. I did all the changes in [this
commit](https://github.com/lucapette/passata/commit/4877303). The documentation
of the plugin was outdated so I opened a [pull
request](https://github.com/torifat/flowtype-loader/pull/9), hoping that other
people wouldn't run into this problem during the transition phase between
version `1.x` and `2.x`.

## Tick, tock

Next step was to integrate the timer with the rest of the application. I did it
[here](https://github.com/lucapette/passata/commit/977a01f338f0dbb79e393e8cc915e8050aae249c)
and I liked the exercise. I had to adapt the initial API I designed for the
timer. As always, I felt unhappy with the code I wrote. To be honest, I'm never
happy with the code I write and I consider it a good sign. It's the main reason
why I don't believe much in the principle "write code that is easy to change". I
prefer to "write code that is easy to delete". I find changeability to be a
feature overcharged with meaning by our instinctive need for refactoring.

The timer worked fine but I wanted to be able to update the document's title
with the current time. I researched how to update the title of a document "the
react way" and ran into a project I liked. It's called
[react-document-title](https://github.com/gaearon/react-document-title). That's
great naming: it's called what it does and I always appreciate that. I
integrated it
[here](https://github.com/lucapette/passata/commit/2bc71a668e475755cd141be1038a6dd855e0fc8b)
and managed to play a bit with [lodash](https://lodash.com/) too. I remember
running into lodash in the past and thinking that it was a nice little
"underscore.js alternative". Now, I get the impression the project has much more
to offer and I plan to get back to it.

At this point, passata has its main functionality: the timer works fine and it's
nicely presented in a little progress bar. I still can't use the application
every day, though, as it misses a set of features I can't live without:

- CRUD of categories.
- CRUD of notes.
- Running a pomodoro in a selected category.

In short, I can't use a pomodoro application that doesn't store my activities.
Those features generate many questions for me, as I have no idea how to persist
objects in a React project. In the next article I will be answering these
questions and I hope you'll find the answers useful.

Thank you for reading me and stay tuned for the next article!
