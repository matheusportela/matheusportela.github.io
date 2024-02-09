---
layout: post
status: publish
published: true
title: 'Worst Sorting Algorithm'
date: '2024-02-07 18:45:00 -0500'
categories:
- Culture
tags:
- programming
- hacking culture
- culture
comments: []
---

In 2010, someone decided to ask a very curious question on Stack Overflow: [Are there any worse sorting algorithms than Bogosort (a.k.a Monkey Sort)?](https://stackoverflow.com/questions/2609857/are-there-any-worse-sorting-algorithms-than-bogosort-a-k-a-monkey-sort), a classic example of [hacker culture](https://www.catb.org/~esr/faqs/hacker-howto.html#style).

I found some of the answers absolutely hilarious and I decided to reproduce them here for posterity.

---

# Intelligent Design Sort

From [David Morgan-Mar's](http://www.dangermouse.net/esoteric/) Esoteric Algorithms page: [**Intelligent Design Sort**](http://www.dangermouse.net/esoteric/intelligentdesignsort.html)

> **Introduction**
>
> Intelligent design sort is a sorting algorithm based on the theory of intelligent design.
>
> **Algorithm Description**
>
> The probability of the original input list being in the exact order it's in is 1/(n!). There is such a small likelihood of this that it's clearly absurd to say that this happened by chance, so it must have been consciously put in that order by an intelligent Sorter. Therefore it's safe to assume that it's already optimally Sorted in some way that transcends our naïve mortal understanding of "ascending order". Any attempt to change that order to conform to our own preconceptions would actually make it less sorted.
>
> **Analysis**
>
> This algorithm is constant in time, and sorts the list in-place, requiring no additional memory at all. In fact, it doesn't even require any of that suspicious technological computer stuff. Praise the Sorter!
>
> **Feedback**
>
> Gary Rogers writes:
> > Making the sort constant in time denies the power of The Sorter. The Sorter exists outside of time, thus the sort is timeless. To require time to validate the sort diminishes the role of the Sorter. Thus... this particular sort is flawed, and can not be attributed to 'The Sorter'.
>
> Heresy!

---

# Quantum Bogosort

A sorting algorithm that assumes that the many-worlds interpretation of quantum mechanics is correct:

1. Check that the list is sorted. If not, destroy the universe.

At the conclusion of the algorithm, the list will be sorted in the only universe left standing. This algorithm takes worst-case Θ(N) and average-case θ(1) time. In fact, the average number of comparisons performed is 2: there's a 50% chance that the universe will be destroyed on the second element, a 25% chance that it'll be destroyed on the third, and so on.

---

# Segments of π Sort

Assume π contains all possible finite number combinations. See math.stackexchange question

1. Determine the number of digits needed from the size of the array.
2. Use segments of π places as indexes to determine how to re-order the array. If a segment exceeds the size boundaries for this array, adjust the π decimal offset and start over.
3. Check if the re-ordered array is sorted. If it is woot, else adjust the offset and start over.

---

# Jingle Sort

Jingle Sort, as described [here](http://www.youtube.com/watch?v=kbzIbvWsDb0).

You give each value in your list to a different child on Christmas. Children, being awful human beings, will compare the value of their gifts and sort themselves accordingly.

---

# Miracle Sort

Many years ago, I invented (but never actually implemented) MiracleSort.

```
Start with an array in memory.
loop:
    Check to see whether it's sorted.
    Yes? We're done.
    No? Wait a while and check again.
end loop
```

Eventually, alpha particles flipping bits in the memory chips should result in a successful sort.

For greater reliability, copy the array to a shielded location, and check potentially sorted arrays against the original.

So how do you check the potentially sorted array against the original? You just sort each array and check whether they match. MiracleSort is the obvious algorithm to use for this step.

**EDIT:** Strictly speaking, this is not an algorithm, since it's not guaranteed to terminate. Does "not an algorithm" qualify as "a worse algorithm"?

---

# Sleep Sort

I'm surprised no one has mentioned sleepsort yet... Or haven't I noticed it? Anyway:

```
#!/bin/bash
function f() {
    sleep "$1"
    echo "$1"
}
while [ -n "$1" ]
do
    f "$1" &
    shift
done
wait
```

example usage:

```
./sleepsort.sh 5 3 6 3 6 3 1 4 7
./sleepsort.sh 8864569 7
```

In terms of performance it is terrible (especially the second example). Waiting almost 3.5 months to sort 2 numbers is kinda bad.

---

# Random Sort

I had a lecturer who once suggested generating a random array, checking if it was sorted and then checking if the data was the same as the array to be sorted.

Best case O(N) (first time baby!) Worst case O(Never)
