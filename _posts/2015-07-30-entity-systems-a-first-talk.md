---
layout: post
status: publish
published: true
title: Entity systems - a first talk
date: '2015-07-30 23:26:19 +0000'
date_gmt: '2015-07-31 02:26:19 +0000'
categories:
- Software Engineering
tags:
- entity systems
- programming patterns
- game development
- software engineering
- object-oriented programming
- object-oriented principles
comments:
- id: 6
  author: porpoisepor
  author_email: felipe.spam.spam@gmail.com
  author_url: ''
  date: '2015-08-04 02:07:16 +0000'
  date_gmt: '2015-08-04 05:07:16 +0000'
  content: "Saw this post while scrolling through the comment section at T-machine.\r\nEntity
    systems are truly magical, the whole idea seems to have so much potential.\r\nI'm
    looking forward to seeing its applications outside gamedev."
---
During the first semester of this year, I decided to take the "Introduction to Game Development" course at the [University of Brasília](http://www.unb.br) where I had to create a game engine from scratch using only [SDL](https://www.libsdl.org/) and a game using it, which we named [Poïesis](https://github.com/matheusportela/poiesis). Here, I want to share one of the most exciting findings I did while research game engine architectures.

I was the only developer in my team, so I tried to do something different. I wanted to design a game engine that was easy to extend and allowed heavy modularization in small and reusable bits.

My first trial involved a **hierarchical** game engine.The idea is intuitive and, probably, will be the first guess for anyone that try and develop games: make a parent class that implements generic methods to extend it with children classes. Usually, *GameObject* is the first class in the hierarchy tree, with essential methods for objects in the game, such as sprite rendering and updates.

Let's see an example: I want to make an alien and a penguin objects, where both are able to move around the world. In a hierarchical game, I would first implement the *MoveableObject* class, with the logic for moving objects in the game world, then I would make *AlienObject* and *PenguinObject* classes inherit from it and, finally, implement their specific methods.

<center><img src="/assets/images/entity_system_1.jpeg"/></center>

Nice, right? Well... this works for simple programs such as the example above. However, problems arise when writing larger games, which usually have dozens or hundreds of classes with several logical interdependencies. I'll illustrate it with another example.

This time, I need to expand the game so as the alien can shoot, but not the penguin. In order to do that while allowing future classes to shoot as well, I can use a programming language that allows multiple inheritance, create a *ShootBehavior* and make *AlienObject* inherit from both *ShootBehavior *and *MoveableObject*. This is a feasible but undesirable solution since, for most programmers, even reading the words "multiple inheritance" [gives them nightmares](http://stackoverflow.com/questions/225929/what-is-the-exact-problem-with-multiple-inheritance). Of course, we can move all shooting logic to *MoveableObject *or* GameObject*, but that's definitely not a reasonable OO solution since it violates the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle).

<center><img src="/assets/images/entity_system_2.jpeg"/></center>

Say I need smaller penguins in the game, which are pretty similar to the original one but with a few particularities. It is natural to create a *SmallPenguinObject* class that inherits from *PenguinObject*.

Now, I may write some AI logic for the small penguin which, curiously, I need to implement in the alien as well. The problem is: these classes are in different hierarchy branches. How can we implement the same logic in both classes without appealing to code replication?

<center><img src="/assets/images/entity_system_3.jpeg"/></center>

Tough problem, isn't it? It turns out that some people have already faced this kind of problem before and thought out a solution by modifying their idea of what constitutes a game object. Instead of implementing the game logic directly in each object class (such as *AlienObject, PenguinObject*, and *SmallPenguinObject*), this logic can be built from **components** that give the objects some behavior.

For instance, in order to make an object move, I can create a *MoveableComponent* class with the code required to move its attached object in the world. Then, all moveable objects will have an *MoveableComponent* instance that is executed by the game engine, therefore, moving it in the game.

In order to achieve the behavior I want, all that is needed is to create the *MoveableComponent*, *ShootComponent*, and *AIComponent* classes, instantiating them to the objects I want to. In this example, all objects have the a *MoveableComponent* instance. *AlienObject* would also have the *ShootComponent* and *AIComponent* instances, and *SmallPenguinObject* has a *AIComponent* instance.

<center><img src="/assets/images/entity_system_4.jpeg"/></center>

The approaching of building objects by attaching components into it is, roughly speaking, an **entity system**. In fact, in a true entity system, game entities (objects) are simply ID numbers which have components attached to it. Components just hold data that is processed by systems, the place where behaviors are implemented. An entity manager is responsible for providing query methods that select entities and components according to the desired criteria, as well as managing addition, deletion, and attaching of entities and components. Finally, a system manager runs the systems, executing the game indeed.

<center><figure><img src="/assets/images/entity_system_representation.png" alt="entity_system_representation" width="350" height="192" /><figcaption>Representation of an entity and its attached components. Source: <a href="http://gamedev.stackexchange.com/questions/31473/role-of-systems-in-entity-systems-architecture">Stack Exchange</a>.</figcaption></figure></center>

What are the benefits of this an entity system? Well, components are generic enough to be inserted in any future game object I may think of. Suppose I decide, months from now, to introduce ants to the game that require the same AI logic used by the alien. With an entity system, I don't need to change anything in the inheritance tree. An ant needs only to contain an *AIComponent* instance and, *voilá*, it's done! See? Full code reuse with minor modifications. Virtually, an object can have any kind of behavior by just attaching more components to it.

Moreover, in an entity system, the game object simply becomes a container of components, whom are responsible for behaviors and implement the game *de facto*. Therefore, game object classes don't grow with time anymore and can respect the Single Responsibility Principle.

Clearly, this approach introduces some complexity into the project and it isn't recommended for really simple games. However, I found that my productivity when developing Poïesis drastically increased by using an entity system. It was also a truly enjoyable experience.

Got interested in learning more about entity systems? Me too! Although this game was the first project where I applied this theory, this architecture definitely isn't restricted to game development and can be applied in network systems or cloud computing. Below, I put the main references that influenced me while developing my game engine. I strongly recommend to read them in order to get a better grasp on the power of entity systems.

* [T-machine.org: Entity Systems are the future of MMOG development - Part 1](http://t-machine.org/index.php/2007/09/03/entity-systems-are-the-future-of-mmog-development-part-1/)
* [Game Programming Patterns - Decoupling patterns - Components](http://gameprogrammingpatterns.com/component.html)
* [Entity Systems Wiki](http://entity-systems.wikidot.com/)
* [Stack Exchange - Game Development - Role of systems in entity systems architecture](http://gamedev.stackexchange.com/questions/31473/role-of-systems-in-entity-systems-architecture)
* [Poïesis source code](https://github.com/matheusportela/poiesis)
