---
title: "All I have done wrong running a product team"
description: The first time you do something, you learn a lot. It's time to share that.
keywords: product management, product teams, product development
layout: articles
---

Two years ago I had an opportunity to shift my career towards product
management. It took me a while to accept the job, it was no easy decision. I
needed to be ready for leading people who were doing a job I had never done
before, I needed to take product decisions. While I felt ready on the
leadership part, I was afraid of not being able to get up to speed with the
product part fast enough.

Two years passed and I learned a lot. Along the way, I made a few mistakes and
in this article I want to focus my attention on those four or five things I consider crucial.
Now these learning seem just _common sense_ to me. I often find myself
summarising this experience in a joke:

> Common sense is not so common

This is the reason why I feel compelled to share the learnings I consider
basic product management now. I will present my list in no particular order.

## Data is nothing. Information is the key

We have introduced [blazer](https://github.com/ankane/blazer) at work
recently. I've wanted to add this little tool to our portfolio of internal
applications for a long time. The reaction coming from other departments
was great. Everyone was happy about the tool and it was a stimulating
process for me. I started asking myself what the real difference between these
two processes is:

- A product development team providing data for the rest of the company, and
- Everyone being able to ask questions on their own

My assumption was that people were happy about shortening the feedback loop.
It's like writing tests instead of deploying code, right? It takes less time
to figure out you broke something if there are tests around.

I was wrong. My technical background made me focus on the wrong aspect of this
problem. Everyone wants answers faster, no discussion there. However, people's
enthusiasm was not driven by the shorter lead time, they were happy because
they could finally participate in the process of transforming data points into
useful information. One day I came to realise data is nothing. Blazer was
useful because it could help with information, not because it increased data
availability for the rest of the company. No one really cares about the
conversion rate comparison in two different countries. Everyone wants to know
the *why* of the differences and similarities. The information that explains
the data is the key. People can do a better job if they can extract
knowledge out of data. Knowing _why_ a company performs better in a market is
the key information. Finding the answer will improve your marketing strategy,
and it could change the story of your company drastically.

Working with product managers and senior management meant being in
conversations where all you would hear is data. It took me a while to realise
I was confusing data for information. I had no process in place to make that
transformation happen. What we needed was a systematic approach to this
process. To cut a long story short,

> When presented with data, ask yourself: why that data?

Ask questions all the time. You hear data points and you automatically ask
yourself why. What is the explanation behind it? You need to transform all the
data points you hear into useful information. I believe this process should
back up your roadmap. It's a three-step process:

1. Look at the data
2. Ask yourself why
3. Extract information

And I think it should be a big chunk of the product discovery phase. Most of
the time the answer to the question "what's next?" is already there, well
hidden in your data points. You don't know the answer because you're not
systematically asking yourself why.

## Say no to CEO features

I define "CEO features" as features we build because someone says so or just
because it sounds cool to build them. According to my definition, those
features do not always come from the CEO. The key mistake is fast tracking
features without the necessary scrutiny. It was very tricky for me to figure
out how to handle the features coming specifically from the CEO. Here is the
problem:

- My CEO set up the vision of the company
- My job was execute that vision translating it into a product vision
- My team and I translated that vision into a product roadmap
- We built things from our roadmap

The problem lies in the tiny border between vision and roadmap. I think they
need to overlap, they must compliment each other. And that's exactly why this
has been so tricky for me. I struggled a lot with the concept as I could
correlate with my CEO saying "we should do this because it's the right thing".
It happened to me often while leading developers: to struggle between giving
people enough room for decision and needing to do what I believed was the
right thing. So how do I say no to a "CEO feature" and keep the overlap
between his vision and the product vision?

It was hard, however, it had a very simple solution. The word _feature_ is not
present in the sentence "translating the vision into a product roadmap". It's
about the vision and its implementation: a roadmap is not a set of features. A
crucial mistake I believe only a newcomer like me could make. The roadmap is a
visualisation of your strategy, a high level concept. Nothing about the CEO
vision and the product roadmap is about the features you build and it took me a
while to truly understand it.

Once again, it is just common sense. _Of course_ you should not let your "CEO
features" be fast tracked. _Of course_ it makes no sense to fast track any
feature. Now I think I have a good understanding of the relationship between
the CEO and the product team and I can back up my "No, we won't be doing that"
with good reasoning. It's not about a list of features, it's about clear
strategy and its execution.

## Say no with reason

[Saying no](https://duckduckgo.com/?q=saying+no+product+managment&ia=web)
seems to be a required feature for good product management. I can agree to
that sentiment but I think it's an incomplete statement. When I started
running my first product team, we did not have enough people and experience to
say no. I struggled with it as I felt we were not saying no often enough. It
had bad consequences:

- Irrelevant features were creeping into our building cycle
- We would often build the wrong thing and only realise after the roll-out
- We would build more than we needed

It was not the nicest situation and it was that rare case in which hiring was
the answer (hint: use hiring as the _last_ answer to your problems, it brings
the best in you and the people around you). We hired more people and brought in
the necessary skills. Finally my team was saying no to feature requests. Oh, it
felt good. We were saying no to things that made no sense to us. But it had
consequences for the rest of the company. People were frustrated by this new
attitude. I was expecting it but I still got something wrong: I thought it was a
temporary phenomenon. I was telling myself that we just needed some time to
adapt and people would understand why saying no to most requests was the right
thing to do. Here we go, it's just common sense again: why would people
understand a no without any context?

We were saying no but we were not explaining its benefit. It turns out this is
easy to fix: you say no to people and always provide them with an explanation on
what you are going to do *instead*. It's as easy as that. This approach comes
with mutual benefits for both your product team and the rest of your company:

- The rest of the company understands better how you prioritise product work.
It's vital they get it.
- You have to convince people your prioritisation is
correct. Great side-effects:
  - You learn how to express things clearly and in plain English. No jargon, no
  acronyms. It makes your communication more inclusive.
  - Together with other teams you can catch errors in the prioritisation and that is a *great*
  outcome too.

## Do not ship what you can't measure

I must confess I felt guilty while reading about [feature
factories](https://hackernoon.com/12-signs-youre-working-in-a-feature-factory-44a5b938d6a2#.wkyer1gmt).
We were showing clear signs when it came to impact analysis. What I did wrong
here was realising too late how important it is to design a process around
impact. It felt especially bad to realise I was doing it wrong; it's obvious to
me there is value in analysing the impact of features.

Nowadays, I would be able to design a process around impact analysis but I have
never tested it yet. I think it would be as easy as:

- Require all the feature specs to provide an expected impact.
- Set up a recurrent meeting with the product team to evaluate expected impact
versus reality.
- Share the outcome of the meeting twice: with the development teams and with
  the rest of the company.

I consider this process a good start and I would love to evaluate it during
retrospectives. I am curious to hear other folks' opinion on the subject as my
approach is still just a hypothesis that needs testing and feedback. I like to
say:

> In theory, there's no difference between theory and practise, in practise
> there is always a difference.

## Get rid of features no one uses

Deprecating features simplifies your product, simpler is better. I think feature
deprecation is strongly connected to impact analysis. We did not do this enough
because we did not know enough about some of our features. This way our product
kept growing in terms of complexity and we missed the opportunity to make our
life easier and, above all, the experience of our customers better.

Given my background as a developer, I found myself thinking about this problem
the same way I think about refactoring code. It helped me realise I can approach
decommissioning of features as I approach a code base. My approach is

> you should not be refactoring your code

It's more of a catchy title for a short article but I think it conveys my
message. You should be improving your code base with every single change. You
should be doing it up to a point when you don't need any set of changes
(developers tend to call it "pull requests" these days) consisting only of
refactored code. Applying this approach to product management can translate
loosely into:

> Simplify your product with *every* new feature. Give more to your customers by
> having *only* the features they need and use.

# Conclusion

Running a product team was great experience. I learned a lot and had fun
building features for such an exciting product. Product management is tricky:
the job is not well defined and being on the border between technology and
business is challenging. Over time, I enriched a metaphor I had read somewhere
in the past (maybe it was [Dr. Alan
Cooper](https://twitter.com/MrAlanCooper)'s writing) and I use it often to
explain what's tricky and exciting about product management. I compare product
development to the construction of a building:

- Product people are the architects. They decide how the windows work, where the stairs are, where and how the lifts work and so on.
- Developers are the construction workers. They build all the blocks and care about all the tiny details that bring the building to life.

The kind of decisions product managers take are hard: stakeholders think they
know which windows you should put in your building because they use windows. As
a developer, I've never experienced this problem; there are few people who
actually know how windows work. Stakeholders just want to use windows or give
them to their customers. This difference between product management and
development was an exciting new challenge for me.

I'm glad I accepted the job back then and I'm happy I will be dedicating my time
to other things now. I have a lot of writing ahead of me and I have never been
so excited about it in my life.

Thank you for reading and stay tuned!
