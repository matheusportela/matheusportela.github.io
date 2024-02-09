---
layout: post
status: publish
published: true
title: "Enigma details: it's all about wires and electrical signals"
date: '2016-06-26 20:43:00 +0000'
date_gmt: '2016-06-26 23:43:00 +0000'
categories:
- Programming
tags:
- enigma
comments: []
---

Today was a tough day understanding little details on Enigma rotors and their stepping system. I wanted to know how exactly this machine worked on communicating letter signals from the keyboard to the plugboard, rotors, the reflector, rotors again, and finally the lampboard.

Enigma is an electromechanical machine with electrical signals and mechanical parts that actually move, rotate, etc. Enigma's keyboard is similar to a computer keyboard: when pressing a key, a contact plugs the power source to the electrical circuit. This produces a current that travels through the entire machine.

One of the first questions I had was how Enigma distinguishes two letters in its circuit. It's quite simple: every component has 26 wires corresponding to alphabet letters. A letter being encoded is just a matter of one current jumping from wire to wire, starting from the keyboard until reaching the lampboard.

<img src="/assets/images/enigma_wiring_diagram.gif" style="width: 500px;">

Rotors are quite remarkable in their engineering. One side has flat contacts while the other has pins, made of conductor material, connecting the output of one rotor to the input of another.

<img src="/assets/images/enigma_rotor_pin_contacts.jpg" style="width: 250px;">
<img src="/assets/images/enigma_rotor_flat_contacts.jpg" style="width: 250px;">

Their encoding tables are defined by scrambling the wirings going from pin contacts to the flat ones.

<img src="/assets/images/enigma_wiring.gif" style="width: 250px;">

Now, when one rotor steps, the rotation simply slides the input/output connections. As a side-effect, this simple mechanical procedure changes the current encoding.

<img src="/assets/images/enigma_rotor_set.png" style="width: 450px;">

The first military Enigma model had 5 rotors available, with different wiring tables built in their scrambled wiring structure. They where named in Roman numbers - I, II, III, IV, and V - and where visible in the pin contacts side of the rotor.

Now, setting up an Enigma machine is just a matter of choosing the right rotor models, placing them in the correct order and positioning, and connecting the appropriate plugs in the plugboard.

[This video, by Dr. James Grime,](https://www.youtube.com/watch?v=mcX7iO_XCFA) is a really didactic presentation on the inner workings of Enigma. I highly recommend watching it in order to get deeper knowledge on the machine.

Are you feeling like finally connecting the pieces of Enigma's puzzle? If so, get in contact with me via my twitter account [@matheusvportela](https://twitter.com/matheusvportela). Also follow [my GitHub repository](https://github.com/matheusportela/enigma-machine) and check my developments on the Enigma simulator in JavaScript.

# References

- [Enigma Rotor Details - Wikipedia](https://en.wikipedia.org/wiki/Enigma_rotor_)details
- [Technical Details of the Enigma Machine - Dirk Rijmenants](http://users.telenet.be/d.rijmenants/en/enigmatech.htm)
