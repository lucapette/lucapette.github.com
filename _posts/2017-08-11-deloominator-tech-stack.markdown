---
title: "deloominator tech stack"
description: A quick overview of deloominator tech stack
keywords: golang, react, graphql, semantic-ui, vega, vega-lite
layout: articles
---

`deloominator` is a data visualization application for SQL users I published a
few weeks ago. You can read the announcement
[here](/deloominator-a-data-visualization-tool-for-sql-users). This article is
meant to be an overview of the technologies with basic information about why I
chose them. Here is a list of technologies that `deloominator` uses at the
moment:

- [Go](https://golang.org)
- [React](https://facebook.github.io/react)
- [GraphQL](http://graphql.org/)
- [React Semantic UI](https://react.semantic-ui.com/)
- [Vega Lite](https://vega.github.io/vega-lite-1/)

# Constraints as a design methodology

When I decided to build deloominator, I had to decide which language and
frameworks to use, and so on. This is an exciting problem to solve and one of
the most interesting phases of building an application. In this phase, I let
constraints drive my decision-making process. I categorize constraints in two
groups:

- Inherent constraints
- Self-set constraints

Using deloominator as an example, I will explain what I mean with these terms:

Inherent constraints are constraints set by the problem you're trying to solve:
I can't build a data visualization tool for SQL users without choosing which
technology will render the visualizations. I can spend some time refining the
scope of the question, something like "which framework?" versus "how hard is it
to build it from scratch?". But I can't move on without knowing how to visualize
graphs.

Self-set constraints are more interesting because we define them for ourselves.
I decided that `deloominator` had to have **zero** dependencies and an image
export feature from the start. A data visualization tool doesn't require you to
solve those two problems, therefore I call those constrains self-set.

What we're used to call "product vision" can be formalized as _the set of
self-set constraints_ we choose for the product we're building. In fact, these
constraints define the product itself.

When I started building deloominator, I knew I wanted **zero** dependencies and
an image export _right away_. Both constraints had interesting implications on
the technology stack and turned out to weigh more on my decisions than the
inherent constraints. I see it as a common pattern, but I don't think it has
ever been formalized anywhere. Maybe that's a good topic for a different
article.

## Zero dependencies

**Zero** dependencies means designing the easiest installation process I could
think of. The idea is that you should be able to go from reading what
deloominator is to running deloominator on your machine in two steps:

1. Download the binary
2. Start it

"Download the binary" automatically meant Go for me. Go builds statically linked
binaries and I _really_ like the language. Moreover, there are already other web
applications that ship as self-contained binaries (like the great
[pgweb](https://github.com/sosedoff/pgweb)), so I could sneak-peak their build
process. For those of you who are not familiar with the technique, here is a
quick explanation: the binary of the application contains both the API server
and the UI application (which in this case is a single page application built
with React). The build task does the following:

- It builds the UI assets (via webpack)
- Then it embeds the bundle into the binary that contains the API server too

As the building process is not a trivial command, I provided a Makefile and
documented it, so that building the project is as easy as typing `make build`.
The effect of this build process on the product is _exactly_ what I was looking
for. You can download the binary and start it right away. It doesn't get easier
than that, and I'm committed to keeping it that way as I move forward.

## Image export

Before I wrote a single line of code for `deloominator`, I was 100% sure I was
going to use D3 for the data visualization part. D3 can render any visualization
you can think of and it has an awesome community. But things changed a little
when I started searching for an way to export charts as images. I must say I
didn't really go deep into the research so now I'm not sure how hard (or easy)
this feature is with D3. What happened is that I randomly bumped into Vega and
immediately fell in love with it. Vega is a data visualization grammar that uses
D3 to render graphs (so, ah!, I'm actually using D3 after all). But the
difference looks subtle only on the surface. Being a grammar specification, Vega
unlocks the door for incredibly powerful tooling I may use in the future.
Rendering images in Vega is a built-in functionality. The idea graphs are
represented as a JSON specification makes me very comfortable with the future of
deloominator. One bonus point is that integrating it with React was really easy
(there's an awesome library for that).

If you're not familiar with Vega, I recommend you have a look at it. The
specification and the tooling around it is great!

# Constraints are not everything

Go and Vega were consequences of the only two self-set constraints I had when I
started building deloominator. As for the rest of the stack, I followed my heart
so to say.

### React

React wasn't even up for discussion in my personal view of the frontend world.
I've always been unhappy with frontend development (and, partially because of
this, not good at it). I've always been unhappy because frontend development did
not fit my mental model. I think of back-end development as a data pipeline: you
have some data and you need part of it somewhere, so you build a pipeline. For
example: get data from a db, output it into a JSON format which another service
reads, so it can output other data as well. Frontend development has always been
one step more than that. You traverse all your pipeline up to your JavaScript
code and you're not done yet. You have to traverse the DOM in some way and
update the right thing. That last step has always broken my mental model. React
has been life-changing from this perspective. I don't have to bother with DOM
updates anymore, I can finally think about frontend code in the same boring way
I think about other programming domains. It's "just passing data around" from
one stage to another.

### semantic-ui

I chose to introduce a front-end framework, because I'm not sufficiently fluent
at CSS to build a non-trivial UI without one. I would prefer to craft only the
UI I really need on my own, but I'm just not good enough with CSS to do so. That
was a somewhat _personal_ constraint more than a technical decision, so I can
imagine that the day deloominator has a CSS-fluent contributor, we may revert
this decision. I thought I'd use bootstrap but, again, while searching for a
React library for bootstrap (well, one other way to really love React for me:
reusable styled components I can use right away. That's a dream come true), I
ran into semantic-ui and I was very impressed. It's a good, full-featured UI
library with a very active community and a **great** official React library. I
was immediately sold.

### graphql

graphql is a fantastic idea and I consider it a clear step forward from the REST
approach. It checks very interesting points (like automatic documentation) and I
was eager to try it first hand. In this sense, more than a technical decision,
this was a personal test. I can already say it's not paying off well so far. As
for what deloominator does right now, two or three endpoints would have
simplified the Go part quite a lot. But I don't intend to revert the decision as
I see the value long-term and I can't wait to write more about it.

# Next steps

I hope you enjoyed this quick overview. I will be writing more about Go and
GraphQL (somehow I have more to say about those two right now), but please
approach me with any feedback, I'd like to write more about this topic!
