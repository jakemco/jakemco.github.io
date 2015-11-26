---
layout: post
title: Python vs. Ruby
subtitle: and why I prefer Ruby
---

At this week's CTF team meeting, one of our members was explaining how he solved
[a particular problem from RCTF last week][nginx]. It was an interesting problem
that involved looking through an nginx log of a sqlmap session and determining
the flag based on the queries that sqlmap made.

At the end, once he had figured the problem out, pulling out the flag involved
taking a list of numbers in string form, and turning them into the ascii string
they represented. For instance, the array `['74', '97', '107', '101']` would
become the string `Jake`. He did this in python:

{% highlight python %}
	''.join(map(chr, map(int, list)))
{% endhighlight %}

where `list` was the list of number strings. This piece of code didn't feel
particularly intuitive to me. In order to understand what's going on, you have
to start at the right and work your way backwards through the line to see what
operations are being performed on the list. If you try to read it in natural
language from left to right it says "Join together the result of mapping into
ascii characters the result of mapping into integers the list."

In Ruby, this same operation would look something like this:

{% highlight ruby %}
	list.map(&:to_i).map(&:chr).join
{% endhighlight %}

This version reads from left to right, like natural language "First take the
list; then map across it turning elements into integers; then map across it
turning integers into their ascii characters; then join them together."

Of course, which of these is more readable depends about how you think about
operations. The python approach reads as composition of functions, i.e.
`g(f(x))`, whereas the ruby version reads as a chain of actions, similar to the
way pipes work in bash, i.e. `x | f | g`.

Personally, I find the latter more intuitive, but as I watched my friend type
his solution into the python console, I realized another thing that bothered me
about python's syntax.

<!--more-->

![typing into python](/img/python.gif)

As you think about the process and are writing out the code, you have to spiral
around the variable adding operations and wrapping everything in parentheses.
Since you don't necessarily have all the steps planned ahead of time, you add
operations as you get to them, causing your cursor to zig-zag back and forth
around your code.

Ruby, on the other hand, prototypes in a much more straightforward manner.

![typing into ruby](/img/ruby.gif)

In this case, Ruby's left to right style not only makes the code easier to read,
but also makes it easier and faster to write in the first place. If you read
from left to right, you can simply type out the operations as you think of them.
This is one reason among many that I prefer Ruby to Python.

[nginx]: https://github.com/ctfs/write-ups-2015/tree/master/rctf-quals-2015/misc/analysis-nginxs-log
