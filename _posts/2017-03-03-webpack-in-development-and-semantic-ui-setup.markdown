---
title: "Webpack in development and semantic-ui setup"
description: Webpack in development and semantic-ui setup
keywords: react, webpack, source maps, flowtype, semantic-ui
category: react
layout: articles
---

This article is part of the series [my journey with React and its
ecosystem](/react.html). If you have not familiar with it, I suggest you
check that out first!

## How do I setup webpack for development?

Webpack documentation is so good that the answer takes up an entire
[section](https://webpack.js.org/guides/development/) of the guide. It took me a
few minutes to understand how to configure `webpack-dev-server`. I wanted it to
serve via the `public` directory. The result impressed me: I could already
automatically reload the application every time I saved a file. You can have a
look at the configuration
[here](https://github.com/lucapette/passata/commit/2b34d5e).

## Source maps and flow

Reading the documentation wasn't sufficient to make source maps work. I had to
research a bit and stumbled upon an
[issue](https://github.com/webpack/webpack/issues/2145#issuecomment-274261381).
It did the trick for me and I had working source maps in this
[commit](https://github.com/lucapette/passata/commit/8ab59d9). I'm not sure why
I had to do it that way, but I assumed the documentation was out of sync and
moved on to flow.

I had wanted to learn more about [flow](flowtype.org) for a long time before I
started my journey. I like the way flow is designed and I have always wondered
how it would feel to set it up and work with it. The setup was easy, I
encountered only minor issues:

- The package is called `flow-bin`. I assumed the package would be called
  `flow`.
- flow checks everything in the current directory, that means it checks node
  modules too and I did not want that.

I found an [issue](https://github.com/facebook/flow/issues/3208) regarding the
second point and it taught me two things:

- [yarn why](https://yarnpkg.com/en/docs/cli/why) is **awesome**.
- flow can be configured to avoid checking node modules. I disagree with the
  design decision of having such a wide default setting. However, I don't mind
  when a software has strong opinions as long as I can get along with them. Yarn
  is easy to configure and it is well documented, so we get along.

I pushed the configuration
[here](https://github.com/lucapette/passata/commit/3836fc2); it was finally time
to move on to code organisation.

## Application layout

I knew this step wasn't strictly necessary for a toy application like `passata`.
But the point of my journey is to learn the technology and not to just get
something done. Moreover, I'm using this journey as a warm-up exercise for a
bigger project where all those aspects are relevant.

My first question was:

> Where do I put what?

It can take years for a community to agree on how to layout a project. I often
argue that this is one of the main reasons why Rails grew popular so fast: the
framework tells you where to put things. It comes handy when navigating a new
code base, and that is important to me: it's about how you communicate with
other developers via simple structures and conventions. I researched the topic
and read the following articles:

-[Organize large React
applications](http://engineering.kapost.com/2016/01/organizing-large-react-applications/)
-[How to better organize your React
applications](https://medium.com/@alexmngn/how-to-better-organize-your-react-applications-2fd3ea1920f1#.n4pw42yk5)

I think I like the idea of laying out the folders of a project by its parts. I
can think of pages and flows as the parts that compose a project. As I said,
`passata` is so small that I can keep all the code in the same directory for a
long time. I ended up doing a tiny
[commit](https://github.com/lucapette/passata/commit/66a6cae) to keep things
going, but I was very happy with the experience and with what I learned.

## Loading CSS with JavaScript

At the time, I did not even know you can load CSS via JavaScript nowadays, so I
had no idea how to make it work in practise. I read webpack documentation and
understood I needed a new rule and a new loader. I stumbled upon a
[survivejs.com](http://survivejs.com/webpack/handling-styles/loading/) article
and liked the website, I thought I would be consulting it often from then on.
Then I realised I needed two loaders to load images and fonts too, and I made it
work [here](https://github.com/lucapette/passata/commit/ec05cd1). It's not much
code but this was a difficult commit. I had to declare the `style-loader` before
the `css-loader`, otherwise it wouldn't have worked. As I am new to this world,
I couldn't explain why; I did not find any documentation explaining or even just
stating that this is the right order.

## semantic-ui

My initial plan was to use [bootstrap](http://getbootstrap.com/), I'm familiar
with it and it saved me from building embarrassingly looking pages many times. I
found two React components libraries for bootstrap:

- [reactstrap](https://reactstrap.github.io/)
- [react-boostrap](https://react-bootstrap.github.io/)

They both looked nice and both gave me the impression my timing wasn't great as
they were doing major refactoring of the projects at the time. I became a tad
doubtful and decided to look around to see if I could find something else. I
discovered there's an incredible number of open source [UI
components](https://github.com/facebook/react/wiki/Complementary-Tools#ui-components)
and I found [semantic-ui](http://semantic-ui.com/). I decided to give it a try
as it looked well-maintained, the [react
components](http://react.semantic-ui.com/introduction) got me excited.

Getting everything to work was the first roadblock of my experience with React
and its ecosystem. It was hard to correctly import the library, the examples in
the documentation did not work for me. The problem seemed too big for me to
solve at once, so I made [components
work](https://github.com/lucapette/passata/commit/ab53953a71c208499052b82c29ff3a968b2f9fe4)
and then moved on to loading CSS via webpack. I tried loading semantic-ui CSS
from a CDN link and everything worked, that made me realise the problem had to
be in the build process. [This
issue](https://github.com/Semantic-Org/Semantic-UI-CSS/issues/21) helped me to
figure it out. The problem was fixed in version 2.2.6, but yarn complained there
was no such version. It was hard to figure out how to make all the different
parts [work](https://github.com/lucapette/passata/commit/c053e8f). At that
point, `passata` was ready to do something. I sketched the screens of the
application with pencil and paper. I ended up with three screens and a dynamic
menu which I will be sharing next week.

Thank you for reading me and stay tuned for the next article!
