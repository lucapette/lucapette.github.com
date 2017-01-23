---
title: "All I have done wrong running a product team"
description: The first time you do something, you learn a lot. Time to share that.
keywords: product management, product teams, product development, management
layout: articles
---

Two years ago I had the opportunity to shift my career toward product
management. It took me a while to accept the job, it was no easy decision.
I needed to be ready for leading people doing a job I never did before,
I needed to take product decisions. While I felt ready on the leadership part,
I was afraid of not being able to get up to speed fast enough with the product
part.

Two years passed and I learned a lot. On the way, I made a few crucial
mistakes and I want to focus my attention toward those four or five things
I consider crucial. I consider those to be just _common sense_. Often, I find
myself summarising this experience with a joke:

> Common sense is not so common

This is the reason why I feel compelled to share mistakes I consider basic
product management now. Furthermore, writing helps me clearing my own thoughts
about things. It is a discovery process and the best part is that someone else
may even find it useful.

I will present my list in no particular order. All I learned in the past two
years revealed to be important to me.

## Data is nothing. Information is key

Recently, we introduced [blazer](https://github.com/ankane/blazer) at work.
I wanted to add this little to our portfolio of internal applications for
a long time. The reaction from other departments' folk was great. Everyone was
happy about the tool and it was a stimulating process for me. I started asking
myself what it is the real difference between a product development team
providing data for the rest of the company and everyone being able to ask
questions on their own. My assumption was that people were happy about
shortening the feedback loop. It's like writing tests instead of deploying
code, right? It takes less time to figure out you broke something if there are
tests around.

I was wrong. My technical background made me focus on the wrong aspect of this
problem. Everyone wants answers faster, no discussion there. The shorter lead
time could not explain the enthusiasm so I started interviewing the people
I worked with in other departments. One day I came to realise data is nothing.
No one really cares about the conversation rate comparison of two countries.
Everyone wants to know the *why* of the differences and similarities. The
information that explains the data is the key. People can do a better job when
they can extract knowledge out of data. Knowing why a company performs better
in a market is key information. Finding the answer will improve your marketing
strategy and this kind of initiative can change the story of a company
dramatically.

Working with product managers and senior management meant being in
conversations where all you would hear is data. It took me a while to realise
I was confusing data for information. I had no process in place to make that
transformation happening. I needed to figure out we needed a systematic
approach to the transformation process. At the end of the day, it's a simple
process:

> When presented data, ask yourself: why is that?

Ask questions all the time. You hear data points and you automatically ask
yourself why is that. What is the explanation behind it? You need to transform
all the data points you hear into information. I believe this should be the
process backing up your roadmap. It's a three steps process:

1. Look at data
2. Ask yourself why
3. Extract information

And I think it should be a big chuck of the product discovery phase. Most of
the time the answer to the question "what's next?" is already there, well
hidden in your data points. You don't know the answer because you're not
systematically asking yourself why.

Now, I'm thinking a lot about how to craft a small process around these steps
we have just discussed. Probably, that is a good topic for another article.
I did not have to chance to design a process and test it.

## Say no to CEO features

I define "CEO features" as features we builds because someone says so or just
because it sounded cool building them. According to this definition, those
features do not always come from the CEO. The key mistake is fast tracking
features without the necessary scrutiny (you need a "definition of ready",
something I should have done better too). It was very tricky for me to figure
how to handle those specifically coming from the CEO. Here is the problem:

- My CEO sets up the vision of the company
- My job was execute that vision translating it into a product vision
- My team and I translated that vision into a product roadmap
- We build things from the roadmap

The problem lies in the tiny border between vision and roadmap. I think they
need to overlap, they must compliment each other. And that's exactly why this
has been so tricky for me. I struggled a lot with the concept as I could
correlate with my CEO saying "we should do this because it's the right thing".
It happened to me often while leading developers to struggle between giving
people enough room for decision and needing to do what I believed was the
right thing. So how do I say no to a "CEO feature" and keeping the overlap
between his vision and the product vision?

This was hard for me but, still, it had a very simple solution. There isn't
the word feature in the sentence "translating the vision into a product
roadmap". It's about the vision and its implementation as a roadmap and
a roadmap is not a set of features. A crucial mistake I believe only
a newcomer like me could make. The roadmap is a visualisation of your
strategy, a high level concept. Nothing about the CEO vision and the product
roadmap is about the features you build and it took me a while to truly
understand it.

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
running my first product team we did not have enough people and experience to
say no. I struggled with it as I felt we were not saying no often enough. It
had bad consequences:

- Irrelevant features were creeping into our building cycle
- We would often build the wrong thing and only realise after roll-out
- We would build more than we needed

It was not the nicest situation and it was that rare case in which hiring was
the answer (hint: use hiring as the _last_ answer to your problems, it brings
the best out of you and the people around you). We hired more people and
brought in the necessary skills. Finally my team was saying no to feature
requests. Oh it felt good. We were saying no to things that made no sense to
us. But it had consequences for the rest of the company. People were
frustrated with this new attitude. I did expect it but I still got something
wrong. I thought it was a temporary phenomenon. I was telling myself we just
needed some time to adapt and people would understand why saying no to most
requests was the right thing to do for everyone. Here we go, it's just common
sense again: Why would people understand a no without context?

We were saying no but we were not explaining what was the benefit of saying
no. It turns out this is easy to fix: You say no to people and always give
them context about what you are going to do *instead* of what they requested.
It's as easy as that. This approach comes with benefits that go both ways from
your product team and the rest of the company:

- The rest of the company understands better how you prioritize product work.
  It's vital for you they get it.
- You have to convince people your prioritisation is correct. Great
  side-effects:
  - You learn how to express things clearly and in plain English. No jargon,
    no acronyms. It makes your communication more inclusive.
  - You can catch errors in your own prioritisation. They may be right and
    that is a *great* outcome too.

## Do not ship what you can't measure

I must confess I felt guilty while reading about [feature
factories](https://hackernoon.com/12-signs-youre-working-in-a-feature-factory-44a5b938d6a2#.wkyer1gmt).
We showed clear signs when it came about impact analysis. What I did wrong
here is realising too late how important it is to design a process around
impact. It felt especially bad to realise I was doing it wrong because I find
obvious there's value in doing impact analysis of features.

Now, I think I would be able to design a process around impact analysis but
I did not test it yet. I think it would be as easy as:

- Require all the features specs to provide an expected impact.
- Set up a recurrent meeting for evaluating expected versus reality with the
  product team.
- Share this twice: with the development teams and with the rest of the
  company.

I consider this a good start and I would love to evaluate the process itself
during retrospectives. I am curious to hear other folks opinion on the subject
as my approach is still just a theory. And that needs testing and feedback.
I like to say:

> In theory, there's no difference between theory and practise, in practise
> there is always a difference.

## Get rid of features no one uses

Deprecating features simplifies your product, simpler is better. I think
feature deprecation is strongly connected to impact analysis. We did not do
this enough because we did not know enough about some of our features. This
way our product kept growing in terms of complexity and we missed some
opportunities to make our life easier and, above all, the experience of our
customers.

Given my background as developer, I found myself thinking about this problem
as they way I think about refactoring code. It helped me realise I can
approach decommissioning of features the same way I approach a code base. My
approach is

> you should not be refactoring your code

It's more a catchy title for a short article but I think it conveys my
message. My view is that you should be improving your code base with every
single change. You should be doing it up to a point you won't need any set of
changes (developers tend to call it "pull requests" these days) consisting
only of refactored code. Applying this approach to product management can
translate loosely into:

> Simplify your product with every feature. Give more to your customers by
> having *only* the features they need and use.
