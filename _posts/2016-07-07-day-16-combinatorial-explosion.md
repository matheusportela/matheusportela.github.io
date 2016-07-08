---
layout: post
status: publish
published: true
title: "Combinatorial explosion - Day 16 #100DaysOfCode"
date: '2016-06-30 18:40:00 +0000'
date_gmt: '2016-06-30 21:40:00 +0000'
categories:
- Programming
tags:
- 100DaysOfCode
- enigma
- cryptanalysis
comments: []
---

By now, I'm working on building an Enigma simulator for a while and the more I study about this amazing piece of technology, the more fascinated I become by the minds that built it. In fact, I can't even imagine how much effort the ones at Bletchley Park put to break Enigma.

If you actually think it through, breaking any code requires two elements: knowing the algorithm and the key. The former can be easily done by intercepting an Enigma machine from the enemy, whereas the later is about figuring out which configuration was used to encode the message.

As we know by watching [The Imitation Game](http://www.imdb.com/title/tt2084970/), the Allies could get an Enigma in their hands and profoundly study it, equipping them with the algorithm. Hence, decoding German messages is only a matter of knowing the exact Enigma configuration used. However, how many possible configurations are there in Enigma?

Let's analyze it using good old [combinatorics](https://en.wikipedia.org/wiki/Combinatorics)!

# Rotor selection

First, we must select our rotors and place them into the three available positions inside the machine. How many combinations of selections do we have? Since there are 5 rotor types for 3 places, it will be:

$$C_r = 5 \cdot 4 \cdot 3 = 60$$

# Rotor settings

Each rotor has 26 different starting positions that may be selected when we start using Enigma. That means the number of possible starting positions, taking all rotors into acount, is:

$$C_s = 26 \cdot 26 \cdot 26 = 17,576$$

# Plugboard

The plugboard - exclusive for military Enigma machines - was a brilliant idea. Their operators would use 10 cables to connect pairs of letters and swap them in the encoding process. Can you figure out how many combinations it provides?

Let's make this calculation step-by-step.

First, we need to select 26 letters from the alphabet. When choosing the first letter, we have 26 candidates. For the second, there are 25 candidates, For the third letter, 24, and so on. This gives us $$26!$$ possible ways to select 26 letters.

However, we only have 10 cables, right? Since each cable connects two letters, our cables are able to connect only 20 letters out of 26 and we must remove from out combinations the 6 idle letters. Hence, the number of possible connections is $$\frac{26!}{6!}$$.

Note that it doesn't matter in what order the connections are made. For example, if we connect a cable from `A` to `Q` and next from `B` to `M`, it'll be the same configuration of connecting first `B` to `M` and then `A` to `Q`. Removing these ordering effects leaves us with $$\frac{26!}{6! 10!}$$ combinations.

Finally, connecting `A` to `Q` is the same as connecting `Q` to `A`: our plugboard is reflexive. Since we don't care about the ordering of the combinations, we must remove these repetitions. We have 10 pairs and there are 10 repetitions to remove, thus $$\frac{26!}{6! 10! 2^{10}}$$.

That's it. The number of possible settings for the plugboard is:

$$C_p = \frac{26!}{6! 10! 2^{10}} = 150,738,274,937,250$$


# Number of possible configurations

The total number of possible configurations for the Enigma machine, considering rotors selection, rotors starting positions, and plugboard configuration, is incredible:

$$C_t = C_r \cdot C_s \cdot C_p = 158,962,555,217,826,360,000$$

<center><img src="/assets/images/not_bad.gif"></center>

Now we understand what Enigma represents. Even if we consider that a modern computer could make one configuration guess in $$1 \mu s$, which is very optimistic (not taking GPUs into account), it would take more than 4 years to try all possible configurations! When comparing with older substitution and polyalphabetic ciphers, Enigma is orders and orders and orders of magnitude better.

This mathematical development is based on the following video, where Dr. James Grime provides a beautiful and didactic mathematical proof. I strongly recommend everyone to watch it.

<iframe width="560" height="315" src="https://www.youtube.com/embed/G2_Q9FoD-oQ" frameborder="0" allowfullscreen></iframe>

That's it for today, folks.

This you like this post? If so, get in contact with me via my twitter account [@matheusvportela](https://twitter.com/matheusvportela) and follow [my GitHub repository](https://github.com/matheusportela/enigma-machine), where I'm developing a Enigma simulator in JavaScript.