---
title: "First steps with webpack, babel, and yarn"
description: First steps with webpack, babel, and yarn
keywords: react, yarn, babel, webpack, flowtype
category: react
redirect_from:
  - /my-journey-with-react-and-its-ecosystem-first-steps-with-webpack-babel-and-yarn
layout: articles
---

I have just started my journey in the [React](https://facebook.github.io/react/)
ecosystem. I decided to take notes along the way so I could share my experience
with you. Most of the resources I found focus on the _coding experience_: how to
test, how to integrate React with X and so on. I, on the other hand, tend to
focus on:

- Available documentation
- Error messages when I make mistakes
- How to ship an application written in X to production
- What does the community look like? Is it inclusive? Is it active? Is it
  welcoming to newcomers?

Furthermore, I knew *nothing at all* about React when I started my journey,
which makes me an experienced newcomer: I have been working in the industry for
more than a decade but I know nothing about React.

## What I want to learn

Here is the list of technologies I intend to explore:

- [React](https://facebook.github.io/react/)
- [ES6](http://es6-features.org/)
- [Webpack](https://webpack.js.org/)
- [Babel](http://babeljs.io/)
- [Flow](https://flowtype.org)
- [Electron](http://electron.atom.io/)
- [React native](https://facebook.github.io/react-native/)

As I knew _nothing_ about _any_ of the technologies I listed, I decided to build
a small application to support me with the [pomodoro
technique](http://cirillocompany.de/pages/pomodoro-technique/). I intend to
adopt React for a larger application soon, and a small application I can use
everyday is a fun way to understand if I'm heading in the right direction.

## Overwhelming setup

I started with a React "hello world":

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Hello World!</h1>,
document.getElementById("root"));
```

```html
<html>
  <body>
    <div id="root">
    </div>
    <script src="/App.js"  type="text/javascript"></script>
  </body>
</html>
```

It's just a few lines of code but I felt _overwhelmed_: there's so much going
on. I read React [installation
guide](https://facebook.github.io/react/docs/installation.html) and I understood
I needed webpack and babel. I ran into [yarn](https://yarnpkg.com/) and it
looked great, so I decided to add one more item to my list. I read up on docs a
bit more, tried some commands locally and felt discouraged.

I had to learn upfront so many things to run a hello world program that I
started looking for help. I tried
[create-react-app](https://github.com/facebookincubator/create-react-app) and
I got this nice "it just works" feeling. I could have started with React
components right away, but I care too much about _how X works_ rather than
just _coding with X_. I can't use technology as a closed box and carry on with
my little application. It was late in the evening that day so I decided to
start over the day after and went to bed.

I started over twice: the first time I realised I did not want to use
create-react-app; then I decided to take notes so I could write the
article you are reading.

Here are the first commands I typed:

```sh
mkdir passata
cd passata
git init
yarn init
```

I felt good about yarn. Its output is helpful and the [UI](
https://github.com/lucapette/passata/commit/c223ce6abb79aa7fac2b5e86e164ec559126086f)
is intuitive. And it is fast, *really* fast.

## Hello world

I moved on to create my first [React
application](https://github.com/lucapette/passata/commit/3540512). It wasn't
working and that was a conscious strategy: one tiny step at the time so I could
understand all the tooling involved. I needed react and react-dom and I added
them as dependencies. I enjoyed yarn's output one more time: in the [commit
message](https://github.com/lucapette/passata/commit/478cae7) you can see how
nice some details of this tool are. Yarn reported there was no lock info file.
It informed me, but it didn't block the process. Instead, it went ahead and
created the lock file for me. I think that's good user experience for a
developer.

Since the hello world code I wrote uses ES6, I needed to bring Babel in right
after the obvious dependencies were met. I had no idea what Babel was and what
it did, so I checked the website to understand the basics. And that was the
first roadblock of my tiny project: the [home page](https://babeljs.io/) says
*nothing* about how to get started with it. It has two big CTAs:

- **Setup**: There are thirty seven buttons on the page and I knew nothing about
most of the them. I knew I needed webpack so I clicked that one. That brought up
some incredibly minimal documentation.
- **Trying it out**: I get it, it does cool stuff. I still didn't get how to use
  it and where to start, though.

I kept reading the documentation on the website and found "presets". I
understood I needed some of them but I did not know why, so I went for "let's
try things out and see if they work". I moved on to webpack thinking I
needed to use it to run Babel anyway. I wasn't really sure though and it
did not feel great.

I spent a while reading webpack documentation. The
[concepts](https://webpack.js.org/concepts/) section is great for people that
have no idea how the tool works. I read the entire section and realised that:

- I needed at least one [entry
  point](https://webpack.js.org/concepts/entry-points/)
- I needed an [output](https://webpack.js.org/concepts/output/)

I configured them [here](https://github.com/lucapette/passata/commit/3c0cbfc).
I added a "scripts" section to the package.json in the same commit as the
documentation explains
[here](https://webpack.js.org/guides/hmr-react/#package-json). This way I could
use yarn as a task runner and skip the creation of a Makefile at the moment.

The application was still not working though, as you can see
[here](https://gist.github.com/lucapette/72e753dfdbbf4a33bf87eacce7cef23a).
Babel wasn't doing anything because it wasn't configured. Somehow I _felt_ I
needed presets (no one had explained to me before what they were, though). I
_assumed_ I needed two:

- es2015
- react

I couldn't figure out if the order was relevant and, if so, what the right order
to add presets was. For the first time since I had started, I had to search the
web. I ran into a [nice blog
post](https://www.twilio.com/blog/2015/08/setting-up-react-for-es6-with-webpack-and-babel-2.html)
and decided to trust the order of the presets mentioned in the article. I added
the [configuration](https://github.com/lucapette/passata/commit/0e35422) but the
result was confusing me. Babel seemed to work on its own; compiling the App.js
file with it produced the right output. But it was still not working when run
via webpack.

### It works!

I made it work
[here](https://github.com/lucapette/passata/commit/328ab199041e075cd1462c0cd6d3d3309fb626cd).
It took me some time to understand why it wasn't working. I had made a mistake a
few commits before and fixing it was tricky: I had the wrong version of webpack
in my `yarn.lock`. I am not sure why yarn picked a `1.x` version for webpack. I
thought the reason was that `2.x` version had been released a few days before.
Once I got the right version, I could correct another little mistake in the
configuration and then finally build my first React application.

It took only a few hours and it was great experience. The most important
learning was: documentation is *vital* and it's hard to write. And it's even
harder to write documentation for newcomers. In this regard, React'
documentation is great. I needed only the installation guide to get things work
and I knew *nothing* about React when I started. Webpack 2 docs are good too.
It's great they take quite some time to explain the main concepts. I cannot say
the same about Babel, the experience with the documentation has been very
frustrating so far.

## What's next?

I have a lot of questions:

- What's a good way to run a React application in development mode? I've read
  somewhere there's a webpack plugin (are they called plugins?).
- What about css and images? I _guess_ I want webpack to take care of assets
  too. Should I do something special about bootstrap if I want to use it?
- How do I layout the project's folders? Is there any convention for React
  applications?

Thank you for reading and stay tuned for the next article in the series!
