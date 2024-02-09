---
layout: post
status: publish
published: true
title: 'How Enigma works'
date: '2016-06-23 22:08:00 +0000'
date_gmt: '2016-06-24 01:08:00 +0000'
categories:
- Programming
tags:
- enigma
comments: []
---

During this journey of [writing an Enigma simulator](day-1-enigma), my first challenge is to understand how it works so I can then build a simulator. With this article, I'll try and explain in simple words and images some of its components and how they relate to each other in order to encode messages.

# Keyboard and lampboard

First, let's take another look at Enigma.

<img src="/assets/images/enigma_outside.jpg" style="width: 275px;">

As you can see, there is a **keyboard** and a **lampboard** - the machine's user interface. Whenever an operator types a letter, a lamp turns on indicating the encoded output. For instance, let's consider that when the letter `A` is pressed, the letter `X` lamp in the lampboard turns on.

```
keyboard -> A -> ? -> lampboard -> X
```

# Plugboard

The first internal component for letter encoding is the **plugboard**.

<img src="/assets/images/enigma_plugboard.jpg" style="width: 450px;">

Its job is simply to mess up with everything. Connecting two letters with a wire swaps their values whenever their keys are pressed. An example: consider we connect `B` and `M` in the plugboard. If we press letter `B`, the plugboard replaces it by a `M`, whereas pressing `M` makes the plugboard outputs `B`. Letters without wire connections simply pass through the plugboard without changes.

In cryptographic words, the plugboard is a simple substitution cypher.

```
keyboard -> A -> plugboard -> A -> ? -> lampboard -> X
```

# Rotors

Then come the **rotors**.

<img src="/assets/images/enigma_rotors.jpg" style="width: 450px;">

Similarly to the plugboard, a rotor simply replaces an incoming letter by another one. The classical Enigma machine had 5 different models of rotors, enumerated from I to V, each one with different substitution routes in their electromechanical structures.

The difference between a rotor and the plugboard is that after each encoding, the rotor **steps** one position, changing the circuits that are connected to each keyboard letter. As an effect, this procedure changes the substitution mapping applied by Enigma.

Let's make this more concrete with an example. At a given moment, a rotor has the following substitution mappings:

```
A -> X
B -> Q
C -> Z
...
Y -> L
Z -> M
```

We now use it to encode an incoming letter, say `B`, which is encoded to `Q`. As soon as the encoding has finished, the rotor takes one step and change its mappings by one position. So, `A` takes the mapping from `B`, `B` takes it from `C`, `C` from `D`, and so on.

```
A -> Q
B -> Z
C -> I
...
Y -> M
Z -> X
```

Notice that if I want to encode `B` again, now Enigma outputs `Z`. Amazing, isn't it?

There are a few more details regarding rotors. The first one is that, usually, an Enigma machine uses 3 rotors at the same time, instead of only one. The output of the first rotor goes to the second rotor to be encoded and then to the last one. Since there were 5 different rotor models (with different substitution ciphers in it), the operator has to choose 3 of them to use.

Another thing is that, when using rotors in series, only the first rotor steps after an encoding, while the others remain still. If only one rotor steps, do the others keep still forever? No, the **turnover** effect prevents that. A rotor completing a full turn makes the next one execute one step. Think of it as a car odometer, which makes `09` becomes `10` whenever the rotor is crossing from `9` to `0`. A small detail is that each rotor model has a specific turnover position. For instance, rotor I will turnover when reaching letter `R`, rotor II with letter `F`, etc.

<img src="/assets/images/odometer.jpg" style="width: 450px;">

```
keyboard -> A -> plugboard -> A -> rotor 1 -> W -> rotor 2 -> L -> rotor 3 -> Q -> ? -> lampboard -> X
```

# Reflector

The last important component is the **reflector**.

<img src="/assets/images/enigma_reflector.jpg" style="width: 450px;">

The reflector, as its name insinuates, acts like a mirror, connecting pairs of letters in a symmetrical way. By symmetrical, I mean that if a letter `D` encodes to `Y`, then `Y` also encodes to `D`.

```
A -> X
B -> Q
C -> Z
D -> Y
...
Q -> B
...
X -> A
Y -> D
Z -> C
```

The reflector is also responsible to send the encoded letter *back* from where it came. The reflector output then run the inverse path through the rotors, the plugboard, until finally reaching the lampboard.

```
keyboard -> A -> plugboard -> A -> rotor 1 -> W -> rotor 2 -> L -> rotor 3 -> Q -> reflector -> I -> rotor 3 -> J -> rotor 2 -> P -> rotor 1 -> Z -> plugboard -> T -> lampboard -> X
```

# Letter pathway

Now we can finally understand the entire path of a letter being encoded by Enigma! Due to its symmetry by using a reflector, decoding a message is only a matter of typing the encoded letters through a correctly configured machine.

<img src="/assets/images/enigma_letter_path.png" style="width: 450px;">

I hope you could understand a little bit of how Enigma works with this article. If you have any questions or saw something that isn't correct, please get in contact with me through my twitter account [@matheusvportela](https://twitter.com/matheusvportela). Also, check how my implementation of Enigma is going in [my GitHub repository](https://github.com/matheusportela/enigma-machine).

## References

- [Enigma machine - Wikipedia](https://en.wikipedia.org/wiki/Enigma_machine)
- [Enigma rotor details - Wikipedia](https://en.wikipedia.org/wiki/Enigma_rotor_details)
- [How Enigma Machines Work - Louise Dade](http://enigma.louisedade.co.uk/howitworks.html)
- [Working principle of the Enigma - Crypto Museum](http://www.cryptomuseum.com/crypto/enigma/working.htm)
- [Technical Details of the Enigma Machine - Dirk Rijmenants](http://users.telenet.be/d.rijmenants/en/enigmatech.htm)
