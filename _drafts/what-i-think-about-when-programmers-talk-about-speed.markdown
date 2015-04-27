---
title: "What I think about when programmers talk about speed"
description: Some random thoughts about development and its relation to speed
keywords: developers, speed, career
layout: articles
---

A couple of weeks ago I had an interesting conversations with one of my team
members. She confessed to me that she felt slow. I was pretty surprised but
before moving on let me make a small premise: I hate the word performance. I'm
not sure how this word feels to native speakers or to people who didn't work
for Accenture. But to me, it sounds like "oh the gigantic pile of bullshit
coming from the manager that has no clue, again." That's my usual reaction to
the word and I don't like to use it at all because of this reason. I must
confess I tried to find a better word for a long time but I ended up settling
down for programmers' performance when it comes about measuring our job.

With this premise in mind, I told her I was surprised and then she asked me to
tell her more. And that conversation lead me to write this article, it had two
main topics:

- Three steps from an idea to the feature.
- Forget about the code, no one cares about it.

# Three steps from an idea to the feature

I'm trying to abstract from how programmers think and what the steps that make
them write the code they write are. Of course, this is going to be a complete
failure if you expect me to get it right and come up with a general solution.
There are so many other ways of looking at it that I don't even try to be
right, furthermore everyone has an opinion anyway. I'm just trying to abstract
a bit from the actual programming process to talk about speed and performance.
So here we go:

- Trying to figure out what to do
- Writing the actual code that does that
- Putting that code in production

## Step 1: Trying to figure out what to do

A programmer may be very sharp in understanding what to do. She knows the
system very well, she has enough context to ask product managers the right
questions, she doesn't miss details and so on. This generally takes time and I
honestly haven't seen many people being fast at this stage. Generally the
speed here is deeply connected with your own workflow. How involved
are product managers at this point? Do you have a checklist for it?

## Step 2: Writing the actual code that does that

This step is the one where I've seen most different results. Some people are
very fast at writing code, others are not. What matters here is your review
culture. Are programmers helping each other? Are they moving code to staging
environments before/after a review? How does the review process work? I focus
on those questions because, from what I've seen, most programmers that are
"really fast" write code that is not ready to go anywhere.  They miss the
details, their code has a lot of "one time workarounds", there are typical
startup comments everywhere ("#TODO Fix this").

## Step 3: Putting that code in production

Here comes the boring/painful step. Given its qualities, it is obvious we are
talking about the most important one as only what comes out of this step
actually does something for your company, your product and your customers.
Speed at this point is a mere consequence of the previous two stages. No
actual work needs to be done at this point in the ideal world, right? The job
you've done at step 1 is perfect and it made the code you wrote at step 2
bug-free and perfectly compliant with the requirements. Now, tell me: how many
times have you seen this happening? How often code gets merged and you forget
about it forever? I'm not sure what your answer is. I'd say it's going to be
close to "ehm... never!" though.

From what I've seen in my career people have very different ways of dealing
with those steps. I met a lot of people that change the order (like in: let's
write the code who cares about the details of step one), people who skip/don't
understand/don't care about step 3. And here it gets interesting, as most IT
managers focus too much on one of the steps and so do the programmers they
manage. My opinion is: none of them count as long as they're all there and the
result is actually helping. It's important to understand that what matters is
the actual result. And most managers I've met don't get they have to be
patient. You have to wait for days to actually see the results. Don't stop at
"oh I love this programmer, she finishes stories in no time". I suggest to be
patient: look at her code one month later. Wait for bugs to come up, wait for
other programmers to have to change her code.
The bottomline: we focus on the wrong metrics and we have to pay more attention to
the entire process.

# Forget about the code, no one cares about it

I like to troll, that's why this section has this title. Of course,
as a technologist, I perfectly know the code matters, the language you use
influences the results, the frameworks you use will make your life easier next
year. But that doesn't change the fact that we (the programmers) are the only ones
caring about those topics and I'm fine with this. No one else cares. Your
customers don't. They expect the button to work and they want to do whatever
they please with your product. That's a point I never emphasize enough. We forget
the fundamental property your code has to have: it has to work. That's it.
That's hard to keep in mind when it comes to speed. The programmer that
generated this discussion forgot about this too when she felt slow. She told
me: "Oh this guy opens pull requests all the time, that's super fast". Pull
requests don't go to production the way they're opened. And even if they do,
you'll have to fix the bugs that come out of that code. And that is a cost
that has an impact on your customers and on your _real_ speed.

I think this topic is strictly connected to what we decided to call "shipping
culture". I see two kind of attitudes about the shipping culture:

- people justify shit going to production in name of shipping culture
- I see people spend hours getting blown away by the next hipster language
  features and how that will make them more productive.

Now, there must be a third way right? It's the one where I say I'm right and I
try to convince you to go my way. Well, sorry. I'm going to disappoint you a
bit. I think there isn't a third way. And I like that. I like that our job as
managers is to find a moving stable equilibrium between the two sides of the
spectrum. The balance between "ship this shit" and "oh wait let's make this
perfect first" dictates your speed on the short and on the long run.  Focusing
too much on the "ship this shit" will produce too much debt and focusing too
much on "let's make it perfect" won't produce enough. A few paragraphs before
I said we focus on the wrong metrics. And I really believe so. The balance I'm
talking about here means forgetting to measure how many features a developer
ships in a week or how fast she goes from starting to work on the feature to
opening the pull request. Writing the code is the fun part, writing the code
is the easy part. And no one cares but you about the code. I'm not sure I can
propose metrics that work better for your team, in the end metrics are
context-dependent. I can tell you I focus more on questions like "how ready is
the code I get from this developer?" "do we always have to review all the
lines?" "Are the features really bugged when they get on staging/production?".
Your mileage may vary and those questions may not apply, all I'm trying to say
is: focus on the value you add to your customers.

It is important to keep in mind that what we do it is not writing code but
adding a feature on your website so your customers can enjoy your product
more. This attitude kills a lot of discussions around technology. It keeps
priorities focused on what matters for your company and your product. This
discussion plays a major role in "developers' speed".  I'm not looking at
their code, I'm looking at the features they write. And that's what I told to
the developer who felt slow. She might be kinda "slow" in the first two steps
but we don't need to do almost anything in the third step. I like that and
while explaining to her I feel she is pretty fast I figured out I could share
these ideas. Other people may benefit and realise they are not as slow as they
think. Or better yet: they are not as fast as they think.
