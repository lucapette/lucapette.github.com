---
title: "My experience with Kanban"
description: How I think Kanban works and what I like about it
keywords: kanban, management, productivity, team, development
layout: articles
---

I wanted to write about Kanban for a long time. I consider sharing our own
views about the way we organise our processes vital to the development of the
techniques themselves. In the end, we try things out and see what works and
what does not. Most of times, this process is pretty slow as we do not share
as much as we could with the people trying to solve the same problems. Or,
even more dangerously, we tend to things by the book since we believe there's
a true way.
I believe there's no such thing as true way when it comes about trying to put
more than one brain in the same room and trying to get things done. Not to
mention the fact most books tend to generalise a lot as they want to reach a
broad audience and the result is most of the time an unusable, unapplicable
set of rules. I do not think what I am saying is controversial. Quite the
contriary: I give for granted we have to adapt whatever process to the team we
work with. So I am talking about this because I want to stress the fact all I
am trying to do is my experience with what I think it is kanban and in no way
you should do what I am discussing in this article. My team is not your team,
so there are high chances our workflow would not work for you.

# What is Kanban, btw?

Well, this is a good question actually. I have no idea what "we use Kanban" is
supposed to mean. I know what I think it means and all I can do is sharing my
"we use kanban" key points:

### Everone owns everything, everyone does everything at every stage

In my view, every version of Kanban is a variation of the sequential stages:
todo, doing, done. As we are talking specifically about development is likely
to imagine having a stage for QA processes (we have two) and a lot of teams I
know would give different people in their team different roles. Each role
would move things from a stage to another or have a special right or duty at a
specific stage. In my version of Kanban this is not a thing. Everyone does
everything at every stage and I have a lot of reasons for "gently forcing" my
teams to work this way. I do not like "special rights". I worked for companies
where developers can't access production machines (which is a bad sign), I
even worked for a company where developers could not access staging machines.
Everyone does everything means everyone can help improving every stage,
everyone gets the full picture, everyone feels the pleasure and the pain of
what works and what does not in your process.

### Focus on what is in progress

One aspect of kanban I like a lot is people gets used to the fact a lot of
work in progress is not a good thing. Being 100% busy is not a good thing and
old school managers shakes when they can ear me advising your team should not
be fully utilised. On my teams everyone runs out of work almost daily. By
design, our process let people run of things they can start working on. And I
love it. The reason is pretty simple: writing the code is the fun part. Code
needs to be reviewed, tested and validated in different envirnments. The rule
I come up with in order to be sure we would focus on what is actually
important (aka shipping code that makes your customers happy) is very simple
and very strict: you cannot start working on anything new unless something
else you did not write the cod for can be moved further in the process
(testing, review, deployment or whatever, it does not really matter). This
rule "forces" people to think about the process itself. Starting working on
something new is exciting, writing code to solve a problem as well. No one
cares about that until it is realeased though. And that is what matters for
the focus.

### No batching, everything is done just in time

This aspect is particularly tricky as it needs help from outside. Generally,
product managers have to really understand the benefits of forgetting to plan
in batches. It is pretty hard and I am lucky enough to be able to work this
way at the moment. No batching means no recurrent meetings about what we are
going to work on the next week (two weeks or whatever). Batching is typical of
SCRUM (at leats in my view) and it has two things I do not like: it lets your
managers relax as it is easier for them to manage teams in strict cycles so
they end up not helping improving processes for the people that are actually
working. It slows reaction time a lot, you cannot easily start working on a
feature that was completely unplanned two days ago and it is now high prio
because your business demands it. And if you work for a startup you really
want to be be able to respond to whatever kind of request comes from the rest
of your company.
The obvious problem is a completely just in time process requires a lot of
daily work from all the parts involves in order to check if things are being
worked on accordingly to priorities or to check if thigns are actually ready
to be worked on.

# Good for starters
# Bend your tool not your workflow
# Make the WIP obvious
# Estimate anyway
# Get graphs about your work
# Our current implementation
