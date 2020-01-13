---
layout: post
status: publish
published: true
title: 'TDD in Javascript - Day 2 #100DaysOfCode'
date: '2016-06-22 23:33:00 +0000'
date_gmt: '2016-06-23 02:33:00 +0000'
categories:
- Programming
tags:
- 100DaysOfCode
- javascript
- tdd
comments: []
---

Before starting build my [Enigma](https://en.wikipedia.org/wiki/Enigma_machine) simulator, I decided to use a [Test-Driven Development (TDD)](http://agiledata.org/essays/tdd.html) approach. Why? Because I believe that with TDD every programmer - including you - can produce more robust software, do easier refactoring, and meet the software specifications.

For those who never heard about TDD, it pretty much a different style of programming advocated by [Kent Beck](https://en.wikipedia.org/wiki/Kent_Beck) and [David Astels](http://daveastels.com/), some really influential guys in the wild. Instead of writing your classes and methods and then testing it - either manually or with auxiliary scripts - to ensure it's working, TDD states that we must write tests in the first place. TDD, can be resumed in three steps:

1. Write the specifications of what you want in the format of an automated test and verify it **fails**
2. Implement the functionality to make the test **pass** in the easiest possible way (as baby steps that are small but takes you there)
3. **Refactor** the code to make it more simple, elegant, performatic, readable, reusable...

<img src="/assets/images/tdd.png" style="width: 30%;">

To apply TDD to my JavaScript code, I decided to use two libraries with names of drinks: [**mocha**](https://mochajs.org/) and [**chai**](http://chaijs.com/). Let me explain them.

`mocha` is a test framework that runs on [Node.js](https://nodejs.org/). It basically runs over your code looking for test functions, execute them in parallel, and output the passing and failing tests in a pretty output format. On the other hand, `chai` is an assertion library. It pretty much offers three functions for asserting inside tests: `should`, `expect`, and `assert`. You can find more information on these assertion styles in their [docs](http://chaijs.com/api/).

After writing some code, that's how I execute them:

```bash
$ mocha enigma.js
```

<img src="/assets/images/mocha_output.png" style="width: 50%;">

That's it. With `mocha` and `chai`, I'm all set for writing JavaScript using TDD. What do you use in your programming environment for TDD? Please, let me know by sending me tweet to my twitter account [@matheusvportela](https://twitter.com/matheusvportela). You can also check all the tests I've written so far by following [my GitHub repository](https://github.com/matheusportela/enigma-machine).
