---
layout: post
status: publish
published: false
title: So, Python 3.6 has better string formatting
excerpt: Differently from Python 3.5, which introduced lots of new features to the
  language, the 3.6 release is basically about enhancing performance, fixing bugs
  and deprecating stuff. Out of those modifications, the most important is the deprecation
  of async and await as variable names, since they will become language keywords due
  to the new coroutines syntax as explained in PEP 492. However, Python 3.6 presents
  the users one more way to format strings, defined in PEP 498.
date: '2016-04-19 20:52:46 +0000'
date_gmt: '2016-04-19 23:52:46 +0000'
categories:
- Software Engineering
- Python
tags:
- python
- f-string
- string interpolation
- python 3.6
comments: []
---
Differently from [Python 3.5, which introduced lots of new features to the language](/python-3-5-0-has-just-been-released/) the 3.6 release is basically about enhancing performance, fixing bugs and deprecating stuff. Out of those modifications, the most important is the deprecation of `async` and `await` as variable names, since they will become language keywords due to the new coroutines syntax [as explained in PEP 492](https://www.python.org/dev/peps/pep-0492/).

However, Python 3.6 presents the users one more way to format strings, [defined in PEP 498](https://www.python.org/dev/peps/pep-0498/). This feature is heavily inspired by string interpolation as implemented in other programming languages, such as [Ruby](https://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Literals#Interpolation), [Perl](http://perlmeme.org/howtos/using_perl/interpolation.html), [Shell Script](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html), [Scala](http://docs.scala-lang.org/overviews/core/string-interpolation.html), and [Swift](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/StringsAndCharacters.html#//apple_ref/doc/uid/TP40014097-CH7-ID292), and tries to do easier string formatting. But what's wrong with our current methods?

First, the old `%`-formatting supports only a limited number of types: integers, strings, and floats. Any other type must be casted to string to become valid. This casting presents a well-known problem when the only argument to be formatted is a tuple, since `%`-formatting uses brackets in its own syntax.

{% highlight python %}
>>> msg = ('disk failure', 32)
>>> 'error: %s' % msg
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: not all arguments converted during string formatting
{% endhighlight %}

Trying to solve some of these problems, `str.format()` provided string formatting with usual method call syntax, as well as better support for custom types, [as detailed in PEP 3101](https://www.python.org/dev/peps/pep-3101/). However, this came with the cost of verbosity and boilerplate code, specially for simple scenarios that were supposed to as small and easy as a "hello, world!".

{% highlight python %}
>>> value = 4 * 20
>>> 'The value is {}.'.format(value)
'The value is 80.'
{% endhighlight %}

In Python 3.6, we can now benefit com `f`-strings and its string interpolation magics. For instance, the previous example would simply become the following. Note that the only requirement is to precede the string with an `f`.

{% highlight python %}
>>> f'The value is {value}.'
'The value is 80.'
{% endhighlight %}

In fact, it supports even more advanced tricks, such as accessing variable attributes directly, combining with raw strings to create regular expressions, for instance, and even parsing results from lambda expressions.

{% highlight python %}
>>> date = datetime.date(1991, 10, 12)
>>> f'{date} was on a {date:%A}'
'1991-10-12 was on a Saturday'
>>> fr'{date}: \s+'
'1991-10-12 \\s+'
>>> f'{(lambda x: x*2)(3)}'
'6'
{% endhighlight %}

That's it. What are your thoughts on `f`-strings? Will you replace your preferred string formatting method by this one?
