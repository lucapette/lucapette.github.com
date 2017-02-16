---
title: Improving IRB history
description: Improving IRB history. Some ways to improve your interaction with IRB history
keywords: ruby, irb, console
category: ruby
layout: articles
---

I’ve started to work on IRB
[configurations](/why-you-should-spend-some-time-configuring-irb/)
as a way to improve my productivity. Following this path I got some nice
stuff in my [irbrc](https://github.com/lucapette/dotfiles/blob/master/irbrc).
Recently, I was thinking about how to make irb history closer to the way bash
handles it. I thought there was a need for the following features:

- History command
- History execute
- History grep

Ignoring duplicated lines on irb exit would be also great.

## The methods

This is the code I wrote:

{% highlight ruby %}
def history_a(n=Readline::HISTORY.size)
    size=Readline::HISTORY.size
    Readline::HISTORY.to_a[(size - n)..size-1]
end

def decorate_h(n)
    size=Readline::HISTORY.size
    ((size - n)..size-1).zip(history_a(n)).map {|e| e.join(" ")}
end

def h(n=10)
    entries = decorate_h(n)
    puts entries
    entries.size
end

def hgrep(word)
    matched=decorate_h(Readline::HISTORY.size - 1).select {|h| h.match(word)}
    puts matched
    matched.size
end

def h!(start, stop=nil)
    stop=start unless stop
    code = history_a[start..stop]
    code.each_with_index { |e,i|
        irb_context.evaluate(e,i)
    }
    Readline::HISTORY.pop
    code.each { |l|
        Readline::HISTORY.push l
    }
    puts code
end
{% endhighlight %}

I don’t like the naming much but I never do. Here are some examples of how to
use the code:

{% highlight ruby %}
ruby-1.9.2-p0 > h
199 h
200 h
201 hgrep "json"
202 h
203 h
204 h "toy"
205 h
206 hgrep "toy"
207 h! 197
208 h
 => 10
ruby-1.9.2-p0 > hgrep "toy"
89 a=Arra.toy
97 a=Array.toy
189 a=Arra.toy
197 a=Array.toy
204 h "toy"
206 hgrep "toy"
209 hgrep "toy"
 => 7
ruby-1.9.2-p0 > h! 197
a=Array.toy
 => nil
ruby-1.9.2-p0 > a=Array.toy
 => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
{% endhighlight %}

I wanted a bash like history and none of the solutions I found had a working
re-execute command. I found some solutions but all of them used eval to
execute code and did not replace the re-executed command in the history. The
h! method I wrote uses `irb_context` to evaluate the input lines. The issue
with the eval version is easy to explain with an example:

{% highlight ruby %}
ruby-1.9.2-p0 > eval("a=Array.toy")
 => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
ruby-1.9.2-p0 > a
NameError: undefined local variable or method `a' for main:Object
    from (irb):2
    from /home/lucapette/.rvm/rubies/ruby-1.9.2-p0/bin/irb:17:in `<main>'
ruby-1.9.2-p0 > a=Array.toy
 => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
ruby-1.9.2-p0 > a="l"
 => "l"
ruby-1.9.2-p0 > h 5
200 eval("a=Array.toy")
201 a
202 a=Array.toy
203 a="l"
204 h 5
 => 5
ruby-1.9.2-p0 > h! 202
a=Array.toy
 => nil
ruby-1.9.2-p0 > a
 => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
{% endhighlight %}

Not a big deal but I really prefer my implementation of the re-execute
command. However, I can’t explain the difference between the two
implementations. I think it may be a scope problem, please let me know if I’m
wrong.

## Erasing duplicates

The last feature I wanted to have in my irb history is the equivalent to this
bash feature:

{% highlight bash %}
export HISTCONTROL=erasedups
{% endhighlight %}

It means erasing your duplicates commands from your history and I came up with
the following:

{% highlight ruby %}
# Don't save duplicates
IRB.conf[:AT_EXIT].unshift Proc.new {
    no_dups = []
    Readline::HISTORY.each_with_index { |e,i|
        begin
            no_dups << e if Readline::HISTORY[i] != Readline::HISTORY[i+1]
        rescue IndexError
        end
    }
    Readline::HISTORY.clear
    no_dups.each { |e|
        Readline::HISTORY.push e
    }
}
{% endhighlight %}

Not the most beautiful code but it does his job: `IRB.conf[:AT_EXIT]` is an
array of proc that IRB calls when you exit. Thus, I added a proc that rewrites
irb history without duplicates.
