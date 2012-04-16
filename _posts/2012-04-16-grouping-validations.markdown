---
title: 'Grouping validation'
description: 'Grouping validation'
keywords: rails, state_machine, with_options, validations
category: rails
layout: blog
---

I'm pretty satisfied with how you can achieve common tasks with Rails. I'm
thinking about Rails routing, validations, internationalization and etc. But
there is just one thing I didn't really like. And it's, of course, grouping
validations. I'm talking about the simple situations where you have a model
that needs to group validations per steps. Something that the awesome
[DataMapper](http://datamapper.org/) guys call contextual validations.
DataMapper provides the following great API:

{% highlight ruby %}
class Article
  include DataMapper::Resource

  property :id,          Serial
  property :title,       String
  property :picture_url, String
  property :body,        Text
  property :published,   Boolean

  # validations
  validates_presence_of :title,       :when => [ :draft, :publish ]
  validates_presence_of :picture_url, :when => [ :publish ]
  validates_presence_of :body,        :when => [ :draft, :publish ]
  validates_length_of   :body,        :when => [ :publish ], :minimum => 1000
  validates_absence_of  :published,   :when => [ :draft ]
end
{% endhighlight %}

Even if it's the first time you see this DataMapper API I'm pretty sure you'd
like to have the opportunity to write something like the following:

{% highlight ruby %}
article.valid?(:draft)

article.valid?(:publish)
{% endhighlight %}

Now, I'm not going to reproduce this feature using ActiveRecord, although it
would be nice to have that. I just want to share with you a recipe for doing
something similar to contextual validations in a nice and clean way.

To cook this recipe with need the following ingredients:

- a state machine

  I'm going to use
  [state\_machine](https://github.com/pluginaweek/state_machine)

- with\_options

  A very nice class macro, kindly offered by
  [ActiveSupport](http://api.rubyonrails.org/classes/Object.html#method-i-with_options).

- A fancy example

  I promised myself I won't use a blog in my examples. Unfortunately, I'm
  going to use something very similar. Sorry about that.

Let's start with the fancy example: Suppose you have a client that works with
articles. In order to publish an article, the following *fancy* requirements
must be meet:

- A draft article should have at least one page and a title.
- A article can be queued for review only if it has at least three tags and a
  short description.
- An article queued for publication can be actually published only it has a
  long description and at least two keywords for SEO fancy people.

Now that we've got the business rules we can say an article can be in the
following statuses:

- draft
- ready\_for\_review
- queued\_for\_publication
- published

I confess I don't like the naming very much. And yes, I know that naming is
hard but, for me, invent a reasonable example is probably more difficult.
Well, using the neat state\_machine gem, we can do something like the
following:

{% highlight ruby %}
class Article < ActiveRecord::Base
  has_many :pages

  state_machine :status, initial: :draft do
    event :ready do
      transition draft: :ready_for_review
    end
    event :queue do
      transition ready_for_review: :queued_for_publication
    end
    event :publish do
      transition queued_for_publication: :published
    end
  end
end
{% endhighlight %}

I have to say I really like the DSL. Basically, the event macro creates an
instance method, executing the method will transit to the proper state if any.
An example will surely explain how it works better than me:

{% highlight ruby %}
irb(main):003:0> a = Article.create! title: 'New article'
=> #<Article id: 3, title: "New article", tags: nil, short_description: nil, long_description: nil, keywords: nil, created_at: "2012-04-13 14:38:16", updated_at: "2012-04-13 14:38:16", status: "draft">
irb(main):004:0> a.status
=> "draft"
irb(main):005:0> a.ready
=> true
irb(main):006:0> a.status
=> "ready_for_review"
irb(main):007:0> a.queue
=> true
irb(main):008:0> a.status
=> "queued_for_publication"
irb(main):009:0> a.publish
=> true
irb(main):010:0> a.status
=> "published"
{% endhighlight %}

Simple and effective. If you're not familiar with state\_machine I strongly
recommend you to take a look at the README. You'll find out a lot of
interesting and useful features.

As we just saw, now we have an easily way to track the current status of an
article for our workflow. We *just* have to add the validations. Before we
start writing them, let's take a quick look at the other ingredients of this
recipe: `with_options`. This class macro gives us the opportunity of writing
less verbose code. A lot of people would say that it will help you to write
DRY code. Actually, DRY does not mean *"don't type a lot"*. It means:
*Every piece of knowledge must have a single, unambiguous, authoritative
representation within a system.*. So, I don't like very much when people
makes their code just shorter and say *"It's DRY"*.

Well, we were talking about `with_options`. In Rails, there are a lot of
methods that take an Hash as the last argument, and when you have pass several
methods the very same options you can use `with_options` to make the call
shorter. It has the nice side-effect of logically grouping calls:

{% highlight ruby %}
# before
class User
  validates :name, presence: true
  validates :surname, presence: true
  validates :password, presence: true, if: -> user { user.new_record? }
end

# after
class User
  with_options presence: true do |user|
    validates :name
    validates :surname
    validates :password, if: -> user { user.new_record? }
  end
end
{% endhighlight %}

OK, now we know how to use `with_options` and we have a nice state\_machine.
The only thing we have to do now is writing the validations. We'll proceed by
state, starting with the draft:

{% highlight ruby %}
 with_options if: -> article { article.status?(:draft) } do |article|
   article.validates :title, presence: true
   article.validates :pages, presence: true
 end
{% endhighlight %}

That's all. The `article.status?(:draft)` is a nice API kindly offered by
state\_machine. And now we can give it a try:

{% highlight ruby %}
irb(main):001:0> a = Article.new
=> #<Article id: nil, title: nil, tags: nil, short_description: nil, long_description: nil, keywords: nil, created_at: nil, updated_at: nil, status: "draft">
irb(main):002:0> a.valid?
=> false
irb(main):004:0> a.errors.full_messages
=> ["Title can't be blank", "Pages can't be blank"]
{% endhighlight %}

It seems to work as expected. Let's just save it:

{% highlight ruby %}
irb(main):006:0> a.title = 'Awesome article'
=> "Awesome article"
irb(main):007:0> a.pages.build content: 'great content'
=> #<Page id: nil, content: "great content", article_id: nil>
irb(main):008:0> a.save
=> true
irb(main):008:0> a.status
=> "draft"
{% endhighlight %}

Then we have to add validations for the second step. We have to ensure that an
article can be queued for publication only if it has a short description and
at least three tags. The first one is very simple because we can just use the
presence validation. But validating tags requires a custom validator. Let's
assume tags are stored in one string and are comma-separated values, a
reasonable approach could be the following:

{% highlight ruby %}
with_options if: -> article { article.status?(:ready_for_review) } do |article|
  article.validates :short_description, presence: true
  article.validates :long_description,  presence: true
  article.validates :tags,              presence: true
  article.validate  :at_least_three_tags, if: 'tags.present?'
end

private
def at_least_three_tags
  self.errors[:tags] = "can't be less than three" if self.tags.split(',').length < 3
end
{% endhighlight %}

Let's we should give it a try:

{% highlight ruby %}
irb(main):001:0> article = Article.last
=> #<Article id: 5, title: "Awesome article", tags: nil, short_description: nil, long_description: nil, keywords: nil, created_at: "2012-04-14 15:20:28", updated_at: "2012-04-14 15:20:28", status: "draft">
irb(main):002:0> article.ready
=> false
irb(main):003:0> article.errors.full_messages
=> ["Short description can't be blank", "Tags can't be blank"]
irb(main):004:0> article.short_description  = 'short desc'
=> "short desc"
irb(main):006:0> article.ready
=> false
irb(main):007:0> article.errors.full_messages
=> ["Tags can't be blank"]
irb(main):012:0> article.tags = 'foo, bar'
=> "foo, bar"
irb(main):013:0> article.ready
=> false
irb(main):014:0> article.errors.full_messages
=> ["Tags can't be less than three"]
irb(main):015:0> article.tags = 'foo, bar, baz'
=> "foo, bar, baz"
irb(main):016:0> article.ready
=> true
irb(main):017:0> article.status
=> "ready_for_review"
irb(main):018:0>
{% endhighlight %}

It works as expected.

Now the last step, We can queue an article if it has a long description and at
least two keywords. Quite similar to the previous step:

{% highlight ruby %}
with_options if: -> article { article.status?(:queued_for_publication) } do |article|
  article.validates :long_description,  presence: true
  article.validates :keywords,          presence: true
  article.validate  :at_least_two_keywords, if: 'keywords.present?'
end

def at_least_two_keywords
  self.errors[:keywords] = "can't be less than two" if self.keywords.split(',').length < 2
end
{% endhighlight %}

Now just some quick tests in the console:

{% highlight ruby %}
irb(main):011:0> article = Article.last
=> #<Article id: 5, title: "Awesome article", tags: "foo, bar, baz", short_description: "short desc", long_description: nil, keywords: nil, created_at: "2012-04-14 15:20:28", updated_at: "2012-04-14 17:11:00", status: "ready_for_review">
irb(main):012:0> article.queue
=> false
irb(main):013:0> article.errors.full_messages
=> ["Long description can't be blank", "Keywords can't be blank"]
irb(main):014:0> article.long_description = 'very long and boring description'
=> "very long and boring description"
irb(main):015:0> article.queue
=> false
irb(main):016:0> article.errors.full_messages
=> ["Keywords can't be blank"]
irb(main):017:0> article.keywords = 'foo'
=> "foo"
irb(main):018:0> article.queue
=> false
irb(main):019:0> article.errors.full_messages
=> ["Keywords can't be less than two"]
irb(main):020:0> article.keywords = 'foo, baz'
=> "foo, baz"
irb(main):021:0> article.queue
=> true
irb(main):022:0> article.status
=> "queued_for_publication"
irb(main):023:0>
{% endhighlight %}

It seems to work as we wanted. We grouped validations in a nice and
readable way. Let's see how the article model looks like now:

{% highlight ruby %}
class Article < ActiveRecord::Base
  has_many :pages

  state_machine :status, initial: :draft do
    event :ready do
      transition draft: :ready_for_review
    end
    event :queue do
      transition ready_for_review: :queued_for_publication
    end
    event :publish do
      transition queued_for_publication: :published
    end
  end

  with_options if: -> article { article.status?(:draft) } do |article|
    article.validates :title, presence: true
    article.validates :pages, presence: true
  end

  with_options if: -> article { article.status?(:ready_for_review) } do |article|
    article.validates :short_description, presence: true
    article.validates :tags,              presence: true
    article.validate  :at_least_three_tags, if: 'tags.present?'
  end

  with_options if: -> article { article.status?(:queued_for_publication) } do |article|
    article.validates :long_description,  presence: true
    article.validates :keywords,          presence: true
    article.validate  :at_least_two_keywords, if: 'keywords.present?'
  end

  private
  def at_least_three_tags
    self.errors[:tags] = "can't be less than three" if self.tags.split(',').length < 3
  end

  def at_least_two_keywords
    self.errors[:keywords] = "can't be less than two" if self.keywords.split(',').length < 2
  end
end
{% endhighlight %}

This technique can be a good starting point if you want to build a wizard. You
can create the `next` and the `previous` events to handle the transitions.
Regarding the controllers and the view, you can simplify your job if you use
the steps as the name of views. Actually, if you're interested I can write
about that too.
