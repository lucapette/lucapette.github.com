---
title: "What I think about when programmers talk about speed"
description: Some random thoughts about development and its relationship with speed
keywords: developers, speed, career
layout: articles
---

A couple of weeks ago I had an interesting conversations with one of my team
members. She confessed me she felt slow. I was pretty surprised but before
moving on let me make a small premise. I hate the word performance. I'm not
sure how this word feels to native speakers or to people that didn't work for
Accenture. But to me, it sounds like "oh the gigantic pile of bullshit coming
from the manager that has no clue, again." That's my usual reaction to the
word and I don't like to use it at all because of this reason. I must confess
I tried to find a better word for a long time and ended up settling down for
programmers performances when it comes about measuring our job.

With this premise in mind, I told her I was surprised and then she asked me to
tell her more. And that conversation lead me to write this. Our conversation
had two main topics:

- Three steps from the idea to the feature.
- Forget the code, no one cares about that.

# Three steps from the idea to the feature

I'm trying to abstract how programmers think and what are the steps that make
them write the code they write. Of course, this is going to be a complete
failure if you expect me to get it right and come up with a general solution.
There are so many other ways of looking at this that I don't even try to be
right, furthermore everyone has an opinion anyway. I'm just trying to abstract
a bit from the actual programming process to talk about speed and performances.
So here we go:

- Trying to figure out what to do
- Writing the actual code that does that
- Putting that code in production

Let's focus on the speed now. A programmer may be very sharp in understanding
what to do. She knows the system very well, she has enough context to ask the
right questions to product managers, she doesn't miss details and so on. This
generally takes time and I honestly haven't seen much people being fast at
this stage. And generally the speed at this stage is deeply connected with
your own workflow. How involved are product managers in this step? Do you have
a checklist for it?
The second step is the one where I've seen the most different results. Some
people are very fast at writing the code, some others aren't. In this step
what matters is your review culture. Are programmers helping each other? Are
they moving code to staging environments before/after a review? How does the
review process work? I focus on those questions because, from what I've seen,
most programmers that are "really fast" write code that's not ready to go
anywhere. They miss the details, their code has a lot of "one time
workarounds", there are typical startup comments everywhere ("#TODO Fix
this").
The last step is the boring/painful one and giving the qualities it has it's
obvious that's the most important one as only what comes out of this step does
actually something for your company, your product and your customers. Speed at
this step is a mere consequence of the previous two. There's not actual work
at this step in the ideal word right? The code you wrote at step 2 is perfect
and the job you've done at step 1 made your code bug-free and perfectly
complaint to the requirements. Now, tell me, how many times have you seen
this happening? Code gets merged and you forget about it for ever. I'm not
sure about your answer. I'd say it's going to be close to "ehm... never!"
though.

From what I've seen in my career people have very different ways of dealing
with those steps. I met a lot of people that changes the order (like in: let's
write the code who cares about the details of step one), people that
skips/don't understand/don't care about step 3. And that's interesting,
especially because most IT managers focus too much on one of the steps and so
do the programmers managed by them. My opinion is: none of them count as long
as they're all there and the result is actually helping. It's important to see
this: what matters is the end result. And most managers I've met don't get
they have to be patient. To actually see the results you have to wait for
days. Don't stop at "oh I love this programmer, she finishes stories in no
time". I suggest patience. That's all I suggest, look at her code one month
after it's there. Wait for bugs to come back, wait for other programmers to
have to change her code.
In the end, what I'm trying to say is that we focus on the wrong metrics and
we have to pay more attention to the whole process. I call it artifact. I have
no clue if that actually works in English and what I use artifact to stress
the point I'll try to make in the next topic.


# Forget the code, no one cares about that.

I like to troll, and that's why this section is called like this. Of course,
as a technologist, I perfectly know the code matters, the language you use
influences the results, the frameworks you use will make your life easier next
year. But that doesn't change the fact, we (the programmers) are the only ones
caring about those topics and I'm fine with this. No one else cares. Your
customers don't. They want the button to work and let them do the things they
want to do with your product. That's a point I never stress enough. We forget
a fundamental property your code has to have: it has to work. That's it.
That's hard to keep in mind when it comes about speed. The programmer that
generated this discussion forgot about this too when she felt slow. She told
me: "oh this guy opens pull requests all the time, that's super fast". Pull
requests don't go to production the way they're opened. And even if they do,
you'll have to fix the bugs that come out of that code. And that's a cost,
that has an impact on your customers and it's impacting your _real_ speed.

I think this topic is strictly connected to what we decided to call "shipping
culture". I see two kind of attitudes about the shipping culture:

- people justify shit going to production in name of the shipping culture
- I see people spends hours getting blown by the next hipster language
  features and how that will make them more productive.

Now, there must be a third way right? It's the one where I say I'm right and I
try to convince you to go my way. Well, sorry. I'm going to disappoint you a
bit. I think there isn't a third way. And I like that. I like that our job as
managers has to be finding a moving stable equilibrium between the two sides
of the spectrum.  This balance between "ship this shit" and "oh wait let's
make this perfect first" dictates your speed on the short and on the long run.
Focusing too much on the "ship this shit" will produce too much debt and
focusing too much on "let's make it perfect" won't produce enough. A few
paragraphs before I said we focus on the wrong metrics. And I really believe
so. Seeing this balance I'm talking about here it meant forgetting to measure
how many features a dev ships in a week or how fast she goes from starting the
feature to open the pull request. Writing the code is the fun part, writing
the code is the easy part. And no one cares but you about the code. I'm not
sure I can propose metrics that work better for your team, in the end metrics
are context dependent. I can tell you I focus more on questions like "how
ready is the code I get from this developer?" "do we have always to review all
the lines?" "Are the features really bugged when they get on
staging/production?". Your mileage may vary and those questions won't apply,
all I'm trying to say is: focus on the value you add to your customers.

Being able to keep in mind that what we do isn't writing code but adding a
feature on your website so your customers can enjoy more your product is very
important. It kills a lot of discussions around technology. It keeps
priorities focused on what matters for your company and your product. This
discussion plays a major role in "developers' speed".  I'm not looking at
their code, I'm looking at features they write. And that's what I told to the
developer who left slow. She does the first two steps kinda "slow" but we
don't need to do almost anything in the third step. I like that and while
explaining to her I feel she's pretty fast I figure out I could share those
ideas I have as other people may benefit and figure out they're not as slow as
they think. Or even better, they're not as fast as they think.
