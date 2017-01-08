---
title: "My experience with Kanban"
description: How I think Kanban works and what I like about it
keywords: kanban, management, productivity, team, development
category: leading
layout: articles
---

I've wanted to write about Kanban for a long time. I consider sharing our
views about the way we organise processes vital to the development of the
techniques themselves. In the end, we try things out and see what works and
what does not. Most of the time this process is pretty slow as we do not share
as much as we could with the people trying to solve similar problems. Or, even
more dangerously, we do things by the book since we believe there is a true
way. I believe there is no such thing as "the true way" when it comes to
putting more than one brain in the same room to build something. Not to
mention the fact that most books tend to generalise a lot as they want to
reach a broader audience and in many cases the result is an unusable,
unapplicable set of rules. I do not think what I am saying is controversial
either. Quite the opposite: I give for granted we have to adapt whatever
process to the team we are working with.  I want to stress the fact that all I
am trying to do is sharing my experience with what I think Kanban is and in no
way you should do what I am discussing in this article. My team is not your
team, so there are high chances our workflow would not work for you. I would
just take everything with a grain of salt and consider this article just food
for thought.

# By the way, what is Kanban?

Well, this is a good question. I have no idea what "we use Kanban" means for
other people. I know what it means for me and here are my key points:

### Everone owns everything, everyone does everything at every stage

I consider every version of Kanban is a variation of the sequential stages: to
do, doing, done. As we are talking specifically about development it is likely
to imagine there is a stage for QA processes (we have two, for example). A lot
of teams I know assign different people in their team different roles.  Each
person in a specific role would move things from a stage to another or have a
special right or duty at a stage. In my view, this is not a thing.  Everyone
does everything at every stage and I have a lot of reasons for "gently
forcing" my teams to work this way. I do not like "special rights". I worked
for companies where developers could not access production machines (which is
a bad sign), I even worked for a company where developers could not access
staging machines. Everyone does everything means everyone can help improving
every stage, everyone gets the full picture, everyone feels the pleasure and
the pain of what works and what does not in the process. The great side-effect
of forcing a no-roles policy is that it helps forming a team quicker and to
introduce new members to an existing team. The reason is quite obvious but
most people seem to overlook it: if everyone does everything people need to
talk to each other more to get or give help about specific tasks they're
trying to accomplish. You are not creating sub-teams inside your teams, good
communication is a key factor.

### Focus on what is in progress

I like this aspect of Kanban: after some time people get used to the fact that
a lot of work in progress is not a good thing. Being 100% busy is not a good
thing and old school managers shake when they hear me advising your team
should never be fully busy. I like when everyone runs out of work almost
daily. By design, our process lets people run out of things they can start
working on. And I love it.  The reason is pretty simple: writing the code is
the fun part. Code needs to be reviewed, tested and validated in different
environments. The rule I came up with in order to be sure we would focus on
what is actually important (aka shipping code that makes your customers happy)
is very simple and very strict: you cannot start working on anything new
unless something else you did not write the code for can be moved further in
the process (testing, review, deployment or whatever, it does not really
matter). This rule "forces" people to think about the process itself. Starting
to work on something new is exciting, writing code to solve a problem as well.
No one cares about that until it is released though. And that is what matters
for the focus. I have to admit it is not always easy to work this way.
Everything comes with trade-offs and the downside of being always about to run
out of work is that managers have to work more than usual. This process requires
constant attention.

### No batching, everything is done just in time

This aspect is particularly tricky as it needs help from outside. Generally,
product managers have to really understand the benefits of forgetting to plan
in batches. It is pretty hard and I am lucky enough to be able to work this
way at the moment. No batching means no recurrent meetings about what we are
going to work on the next week (two weeks or whatever). Batching is typical of
Scrum (at least in my experience) and it has two things I do not like:

- It lets your managers relax as it is easier for them to manage teams in
  strict cycles so they end up not helping to improve processes for the people
  that are actually working.
- It slows reaction time a lot, you cannot easily start working on a feature
  that was completely unplanned two days ago and it is now high prio because
  your business demands it. And if you work for a startup you really want to
  be able to respond to whatever kind of request comes from the rest of
  your company.

A completely just-in-time process requires a lot of daily work from all the
parts involved in order to check if things are being worked on accordingly to
priorities or they are actually ready to be worked on. Which, in this specific
case, requires product help.

### Kaizen is not just a fancy word

[Kaizen](https://en.wikipedia.org/wiki/Kaizen) sounds like a fancy word to me
so I generally do not even mention it in discussions about Kanban. I do prefer
the simple "continuous improvement". There is no need to have read a Kanban
book to know what you mean with it. I think this point is vastly
underestimated, at least that's the feeling I get when I talk to people about
Kanban. The key here is making sure everyone feels comfortable to propose a
change in the workflow. Staying humble and asking everyone to be involved in
the process of improving your own processes is the very core of Kanban in my
opinion. A good benchmark would be: how often do you tweak your workflow? The
answer will tell you how kaizen you are as if you are not changing anything I
assume your team thinks there is nothing left to improve. Which I really
doubt.
Trying to continuously improve your workflow is one of the few cases that
justifies recurring topic-bound meetings and I have seen very good meetings
about improving details of the workflow. Those meetings, if well run, have a
great impact on your team: they will start owning the workflow which should be
your final goal.

# Good for starters

Despite the variance of personal interpretations, I think we can agree on the
fact a Kanban workflow is a variation of the "to do, doing, done" sequential
stages. And that's the very reason why I think it is good for starters. Having
junior people in your team is necessary so the workflow you use should not be
a barrier, the less new-comers have to learn the better. I do not think I have
to explain why you need junior people or why you need a diverse team, in case
you do not have any of those two features you may want to stop reading and fix
that instead. I think I have to write about this topic too at some point.  In
my experience, Kanban is easy to use but hard to understand and that is the
reason why I like it for starters. It is a bit like Ruby. You can start being
productive with Ruby in a few hours, in the end it is almost English but it
takes some time to actually understand more advanced concepts like the object
model. With Kanban it is really the same, you can start using it your first
day at work. You just move things to the right of your board but it takes a
long time to understand the benefits of this approach.

# Bend your tool not your workflow

Before starting to work at my current company, I evaluated all the Kanban
tools I could find. I created something like 50 accounts on different
applications trying to figure out what was the tool that would fit better what
I had in mind. The journey was quite frustrating, all the tools I found did
too much or had a very strong opinion (divergent from mine of course) about
how you should run your teams. Even though I really did not like this journey
it made me realise something crucial I had always done wrong until then. I had
always tried to adapt my tools around the workflow I was using. Trying to
adapt the tools around your actual workflow will likely have negative
consequences. They will be a set of workarounds that makes harder for people
to actually stick to the process you use since the tool is not really meant to
be used that way. Not to mention that starters will have to learn all the
non-written workarounds you use in order to work with your team.
Tooling is important but never crucial for the success of a team so I was about
to give up and just use one (probably trello). Then I kept thinking about what
I mean by Kanban and I figured out one thing I was never able to implement
with tooling until then: "the kaizen principle". The very core of the
philosophy behind Kanban is the fact you continuously improve your workflow
and even when I think I was doing that, the tool was a limiting factor and I
ended up bending my workflow a bit around the limitation of the tool I was
using. I figured out it is not true that tooling is not that
important. In the end the design of my workflow was always limited by the
limitations of my tooling. And this is the main reason why I decided to write
a small tool (the very joy of Rails, from the idea to a working application in
hours). I am very happy now with this decision, it was not that easy for me
to reinvent the wheel and write a Kanban application but the side-effect of
this initial decision is something I never want to give up again. When we want
to change something in our workflow, we just do it and our tooling reflects
exactly what we do and there are no workarounds. Furthermore, I have seen
people being more aware of the way we work as they know they can change it
from whatever angle. They can even change the tools we use everyday. They own
everything, even the tooling they use. In the end, I started considering
having internal tooling as a meta tool for building teams.

# Make the WIP obvious

This is the hardest part in my experience. Making work in progress obvious to
all the people involved and helping them to understand why we want to limit
the working in progress has been always very challenging for me. Of course, it
may be my own limitation, I do not exclude that.
I think there are a lot of different ways you can make sure you know what is
really being worked on. Once again your tooling makes a difference. Our Kanban
application is very colourful and each colour tells us a different thing. What
happens often is we have too many cards of a specific colour. There is no hard
threshold, it is our common sense to tell us "hey, there are a lot of things
we could deploy to production today, it does not make much sense to start
working on new stories". Generally, standups help keeping an eye on the WIP. I
am not a big fan of standups (it is just a personal preferences and you should
never go for your personal preference: it is a team decision) but I have
learnt how to appreciate the time it gives me and my teams to look at how
things are going every morning.
As I said, I find it hard to make WIP obvious to everyone and sometimes I find
my teams with a huge WIP. Now, this is the part of "we use Kanban" I am trying
to focus more on. I have not found a solution that satisfies me yet and I
would like to hear other people's opinion on this topic. Of course, a
satisfying answer is a trick that lets the teams figure out on their own that
there is too much going on.

# Estimate anyway

I think the traditional game of estimates makes no sense at all. You know the
game: developers say something is bigger than it is in order to protect
themselves from unplanned work and stakeholders try to "steal" from those
estimates. Things take the time they take and I do not really understand why
there is this dancing madness everywhere. Of course, business still needs
estimates, right? That is a legit question. And my answer is: trade estimates
with flexibility. The benefit of being always able to change what we are going
to work on in a few days is a lot more than "accurate estimates", if such a
thing exists.
Having said that, I still prefer developers to give estimates. We use t-shirt
sizes, letters are not that easy to sum and your managers will not try to be
clever and batch things together. The main reason I ask for estimates are:

- Common understanding. If one developer says S and another says XL there are
  high chances one of them did not understand the requirements. There are
  chances none of them did.
- Retrospectives. If you plot graphs that show you how big the stories you
  shipped over the past weeks are, you will find surprising answers. At least
  that is what happens to me all the time.
- Keep WIP in sync. If you keep the rule that people will have to estimate
  stories anyway, they will ask in a chat or in person about estimating the
  given story. That helps people say "Umm, you know, I wouldn't start this
  story now. There are a lot of things we can test or review". It is a well
  worth benefit.

# Get graphs about your work

I have just mentioned I am always surprised when I plot graphs about what we
do. And that is a quite good reason to get graphs. Sometimes simple graphs
like a breakdown of the story size or the story type (bug, feature, IT feature
and so on) will tell things you really did not know about your work. Recently
I have started showing those graphs to my workmates and I noticed something
very important I have always ignored so far. They care about the insights,
they care a lot. I often found myself in situations where my manager would
tell me "we need more developers for your team" or "we need another QA person"
and I would not be able to explain the reasoning on my own.  Graphs help
people understand why you want to change something and help them see things
that are not obvious.

# Kanban does not matter

This process is serving us very well but I do prefer to warn people once
again: this is not a silver bullet. And I do not think it is the main reason
for the success of a team. In the end, every technique you end up using to
organise your day is a set of trade-offs, a specific set of limitations you
give to yourself in order not to lose control completely. They all work this
way and Kanban is not special. As of today I am fully convinced the key of
good management is communication. It is the hard part, the challenging one.
And probably the starting point of my next article. Thank you very much for
reading!
