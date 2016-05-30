---
layout: post
status: publish
published: true
title: Python 3.5.0 has just been released
date: '2015-09-17 18:36:03 +0000'
date_gmt: '2015-09-17 21:36:03 +0000'
categories:
- Software Engineering
- Python
tags:
- python
- python 3.5.0
- coroutines
- numerical calculation
- matrix multiplication
comments:
- id: 10
  author: So, Python 3.6 have better string formatting | Matheus Vieira Portela
  author_email: ''
  author_url: http://www.matheusportela.com/so-python-3-6-have-better-string-formatting/
  date: '2016-04-19 20:55:18 +0000'
  date_gmt: '2016-04-19 23:55:18 +0000'
  content: '[...] from Python 3.5, which introduced lots of new features to the
    language, the 3.6 release is basically about enhancing performance, fixing
    bugs and deprecating [...]'
---
Last Sunday, the [Python Software Foundation released the last update for the Python language](https://www.python.org/downloads/release/python-350/). This afternoon, I finally had time to read the PEPs corresponding to the major new features and some of them are really exciting. Check out my compilation of nice features that Python 3.5.0 provides.

## % formatting to bytes and bytearray
[PEP 0461](https://www.python.org/dev/peps/pep-0461/): In Python 3, `bytes` became a new type completely separated from `str`. Some areas of computer programming work constantly with mixed binary and ASCII data, such as in network and systems development, so this new formatting allows `bytes` and `bytearray` to use the same % formatting that exists for strings.

Attention: numeric codes are automatically encoded in ASCII format. For instance:

{% highlight python %}
>>> b'%4x' % 10
b'   a'

>>> b'%04X' % 10
'000A'
{% endhighlight %}

## @ operator for matrix multiplication
[PEP 0465](https://www.python.org/dev/peps/pep-0465/): Numerical computation is an area where Python usage is growing day after day. In fact, packages such as [`numpy`](http://www.numpy.org/), [`scikit-learn`](http://scikit-learn.org/), and [`theano`](http://deeplearning.net/software/theano/) are [some of the most used Python packages](https://www.python.org/dev/peps/pep-0465/#but-isn-t-matrix-multiplication-a-pretty-niche-requirement), among standard and third-party packages.

Up to now, Python had only one multiplication operator - the star `*` - that has been used for two different purposes: element-wise and matrix multiplication. As we all know, duplication can lead to confusion and unreadable code, given that we always need to check how multiplication is implemented according to our data structures. Anyone who has written some numerical calculation in [MATLAB](http://www.mathworks.com/products/matlab/) realized that the offering of two multiplication operators avoid this confusion: `*` stands for vector and matrix multiplication and `.*` is element-wise multiplication.

Historically, Python packages used the `*` operator for one kind of multiplication and a `dot` method for the other one. However, complex expressions with a large number of matrix multiplications suffer from poor syntax and need to the be split in several intermediary steps in order to preserve its legibility, [which is known as a code smell](http://refactoring.com/catalog/replaceTempWithChain.html).

By introducing the `@` operator for matrix multiplication, numerical calculations in Python have their legibility greatly improved. For instance, the following expressions, using `numpy`, are equivalent, except that the last one is much more readable.

{% highlight python %}
>>> S = (H.dot(beta) - r).T.dot(inv(H.dot(V).dot(H.T))).dot(H.dot(beta) - r)
>>> S = (H @ beta - r).T @ inv(H @ V @ H.T) @ (H @ beta - r)
{% endhighlight %}

## isclose(a, b)
[PEP 0485](https://www.python.org/dev/peps/pep-0485/): Still in the numeric computation realm, calculating whether a value is close enough to another value is extremely common. So common that a `isclose` method has just been added to the `math` module. This method also accepts a relative tolerance - the percentage in which `a` is considered to be close to `b` - or an absolute tolerance.

{% highlight python %}
>>> x = 10
>>> y = 10.000001
>>> isclose(x, y, abs_tol=0.1)
True
{% endhighlight %}

## coroutines with async and await
[PEP 0492](https://www.python.org/dev/peps/pep-0492/): Concurrent programming is huge and trending since the industry demands responsive and scalable code. Although Python introduced some coroutines capabilities earlier, they shared their implementation with common generator expressions, the only difference being that coroutines used the `yield from` expression. This was unclear and error prone.

In Python 3.5.0, coroutines are introduced as a standalone concept, with their own syntax and low-level implementation. PEP 0492 provides the following example of coroutine with the new syntax.

{% highlight python %}
async def read_data(db):
    data = await db.fetch('SELECT ...')
    ...
{% endhighlight %}

These are my favorite features in Python 3.5.0 and I will definitely update my version just to check them out and play with coroutines and matrix multiplication.

Tell me, what features have caught your eyes?
