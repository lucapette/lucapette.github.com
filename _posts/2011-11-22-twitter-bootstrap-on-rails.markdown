---
title: Twitter Bootstrap on Rails
description: How you can easily integrate the twitter bootstrap framework and Ruby on Rails
keywords: rails, twitter bootstrap, simple_form, show_for
category: rails
layout: articles
---

In the past weeks I saw a lot of interest for the [twitter
bootstrap](http://twitter.github.com/bootstrap/) framework, and for good
reasons. If you're not familiar with it, go straight to the site. I guess
you'll like it. As for me I'm very enthusiastic about it because I'm neither a
design guru nor a good one. So having a framework that gives nice results in
such a little time is like watching a small dream come true. Now, as I said, I
witnessed a lot of interest for the framework in Rails community, I also read
a couple of good articles about how to play with the framework and the shiny
new asset pipeline we recently got. But I have found little information on the
aspect I find most interesting about this framework and the Rails community.
It works great with the Rails ecosystem. So here I am to write down a couple
of things I learnt while integrating twitter bootstrap into my recent
projects.

First of all, I focused a little on a simple layout that I've used as the base
of some projects. I've just adopted an
[example](http://twitter.github.com/bootstrap/examples/container-app.html)
from the site and modified the application layout of a fresh new rails 3.1.1
app in the following way:

{% highlight erb %}
<!DOCTYPE html>
<html>
  <head>
    <title><%= content_for?(:title) ? yield(:title) : "Twitter Bootstrap" %></title>
    <link rel="stylesheet" href="http://twitter.github.com/bootstrap/1.3.0/bootstrap.min.css">
    <%= stylesheet_link_tag "application" %>
    <%= javascript_include_tag "application" %>
    <%= csrf_meta_tag %>
    <%= yield(:head) %>
  </head>
  <body>
    <div class="topbar">
      <div class="fill">
        <div class="container">
          <%= render :partial => 'common/menu' %>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="content">
        <div class="page-header">
          <%= render :partial => 'common/header' %>
        </div>
        <div class="row">
          <div class="span12">
            <%= render :partial => 'common/flashes' %>
            <%= yield %>
          </div>
        </div>
        <footer>
        <%= render :partial => 'common/footer' %>
        </footer>
      </div>
    </div>
  </body>
</html>
{% endhighlight %}

The partials contain just a paragraph to say what they are but the flashes one
is interesting:

{% highlight erb %}
<% unless flash[:notice].blank? %>
  <div class="alert-message info">
    <%= content_tag :div, flash[:notice] %>
  </div>
<% end %>

<% unless flash[:error].blank? %>
  <div class="alert-message error">
    <%= content_tag :div, flash[:error] %>
  </div>
<% end %>

<% unless flash[:alert].blank? %>
  <div class="alert-message warning">
    <%= content_tag :div, flash[:alert] %>
  </div>
<% end %>
{% endhighlight %}

Now the flashes use nice styles kindly provided by the framework. I know I
could have been more DRY here but I prefer it this way.

Well, I've got a nice layout within the application but let's focus on forms
and show pages. I use two wonderful gems to simplify my work with this kind of
stuff. And it turned out that they both play wonderfully with twitter
bootstrap:

- simple\_form

  I don't think [simple_form](https://github.com/plataformatec/simple_form)
  needs a presentation. By the way take a look at the README to understand how
  this gem can help you in case you're not familiar with it. Well, there is
  even a wiki page on how to integrate the gem with twitter bootstrap.

- show_for

  Citing the [README](https://github.com/plataformatec/simple_form) "ShowFor
  allows you to quickly show a model information with I18n features". And the
  nice thing is that the default output already works well with twitter
  bootstrap. I've just added the css for making links like twitter buttons.

When I got shows and forms, I had just the index page remaining. I modified
the page a bit to include buttons and pagination. In order to make kaminari
and twitter bootstrap play well together I used
[https://github.com/gabetax/twitter-bootstrap-kaminari-views](https://github.com/gabetax/twitter-bootstrap-kaminari-views).

To wrap up the work done, here's the list of crucial commits:

- [Initial commit](https://github.com/lucapette/twitter-bootstrap-on-rails-demo/commit/e147eaebd8c56df1ee89aa8ea0c7774a7879c8c4)

  Just the rails `new twitter-bootstrap-on-rails-demo` command

- [Add gems](https://github.com/lucapette/twitter-bootstrap-on-rails-demo/commit/b01a4fc06e132a3c416b174bd1efc6736fdf1086)

  I added the simple_form and the show_for gems

- [copy https://gist.github.com/1299857](https://github.com/lucapette/twitter-bootstrap-on-rails-demo/commit/f426b60dc66d2dbccefa33e1995837d4d7afa28b)

  I created a [gist](https://gist.github.com/1299857) to make simple the process of starting a twitter bootstrap project.

- [Add pagination](https://github.com/lucapette/twitter-bootstrap-on-rails-demo/commit/fe559cb545ccba3058a19ed41143462efe88bb33)

  I simply copied the kaminari views into the project.

Furthermore, if you use the twitter
[tabs](http://twitter.github.com/bootstrap/javascript.html#tabs) in a form,
you would like to open the tab with fields with errors when the model you're
trying to save is not valid. Well, I wrote a little chunk of CoffeeScript
(with jQuery) to solve this problem:

{% highlight javascript %}
$ ->
  if $('.help-inline, .field_with_errors').length
    $id=$('.help-inline, .field_with_errors').first().closest('.tab-pane').attr('id')
    $('.active').removeClass('active')
    $('a[href=#'+$id+']').click()
{% endhighlight %}

As you can see from this [demo](http://twitter-bootstrap-on-rails.heroku.com/)
with a minimum effort I was able to get a very nice integration with the
twitter bootstrap framework and the Rails ecosystem. Obviously, this is just a
way of doing it and I'd like to read about other ways of getting twitter
bootstrap on Rails.
