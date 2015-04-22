---
title: "A simple postgresql window function with Rails"
description: How I ended up using postgresql window function at work for a simple piece of code
keywords: postgresql, ruby, rails
layout: articles
---

Postgresql is a pretty amazing database system and I started using in
production way too late in my career. At my company we use posgres for all
our relational needs and when I joined the company I spent a few hours reading
the online documentation. I used it mostly to try to orient myself with the
new "toy". In the end, we're still a small company and I didn't really expect
to use any of this amazing features postgres provides. Since I'm writing a
small blog post about a specific features posgresql provide you can guess I
set wrong expecations.

## A simple example

To illustrate how postgres helped us with a window function, I'd like to start
with a small example as I think it will make clearer for me (and I hope for
you) how we ended up simplifing a tiny part of our system. Let's assume we
have recipes and you want to show a list of recipes that are available this
week. We have something like the following:

class Recipe < ActiveRecord::Base
  has_many :delivery_dates
end

class DeliveryDate < ActiveRecord::Base
end

Naming may suck but I'm sure you know naming is hard and you'd be tollerant
about it. To fetch recipes for the current week something like this kinda
works:

Recipe.includes(:delivery_dates).where(delivery_dates:
Date.today.beginning_of_weeek..Date.today.end_of_week)

So far so good, but now we need to extract info from the system. What we are
asked for is a report that has the following format:

|1|awesome recipe|
|2|super awesome recipe|

The first column acts as an index for the recipes ordered by recipe name.
I can imagine a lot of ways to solve this problem and one solution can look
like this:

Recipe.order(:name).each_with_index do |i, r|
  puts "#{i},#{r}"
end

This worked for a couple of months and then we got a new requirement for a
different part of the system. We needed the same information we just extracted
as part of a bigger report that contained data of different nature. What we
did at the time was using the `each_with_index` tecnique and then calculate
the rest of the information in a different way. At first this worked fine but
there was a small subtle bug we run into when we had to order this new report
by a new criteria. Of course, the `each_with_index` tecnique stopped working
from a business perspective because the indexes of the new report and the one
from the existing one were not in sync anymore so our users couldn't really
use it anymore.

## We'll use a window function

When we got a bug report about indexes in different reports going out of sync,
@damireh and I decided to pair for a while on the problem (pairing helps when
you have to explore solutions). Honestly, I don't really remember how we
decided to `rank()`

It doesn't work with joins
but there's dense_rank
It's nothing special but it actually helps to understand windows functions
