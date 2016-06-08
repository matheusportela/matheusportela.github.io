---
layout: post
status: publish
published: true
title: Message queues for distributed systems
date: '2016-06-06 21:55:00 +0000'
date_gmt: '2016-06-07 00:55:00 +0000'
categories:
- Software Engineering
tags:
- programming
- message queues
comments: []
---

I've been working at [Simbiose Ventures](http://www.simbioseventures.com) for the past six months in some projects that deals with huge amounts of data and that experience has driven me to always think on how the systems will scale in order to accommodate all incoming data without performance degrading as well. For the first time, I had to start thinking in [distributed systems](https://en.wikipedia.org/wiki/Distributed_computing). Soon I noticed that, when creating a distributed system, the first barrier we meet is to define some way to distribute the workload across many processes and computers. This article is on how we use message queues to achieve workload distribution and system decoupling.

The concept of message queues isn't new in the computing world. In fact, I heard this name for the first time when studying Operating Systems at the university. Quoting the book ["Operating System Concepts"](http://www.amazon.com/Operating-System-Concepts-Abraham-Silberschatz/dp/0470128720), we can notice how message queues (a.k.a. message passing) was born for distributed computing.

> Message passing provides a mechanism to allow processes to communicate and to synchronize their actions without sharing the same address space. It is particularly useful in a distributed environment, where the communicating processes may reside on different computers connected by a network. For example, an Internet chat program could be designed so that chat participants communicate with one another by exchanging messages.

Let's make things more concrete by giving an example. When I need to communicate with a friend, I just get my phone and send her a WhatsApp message or an e-mail so I don't have to disturb the person at that exact moment. I can send as many messages as needed as they will be buffered in her phone until she is able to get it and read the messages, taking any action required. This is a message queue between two people communicating with each other, but the same pattern applies to distributed systems.

First, I have a process called **producer** that generates messages to be processed. Then, we have the **message queue** that stores messages in a **queue** - acting as a buffer - and route them to a **consumer**, some process that will process messages. Since a single queue is shared between virtually any number of producers and consumers, we can easily design systems to be scaled up quite easily by simply spawning more processes on more machines as far as they communicate through the same queue.

<center><img src="/assets/images/message_queue.png"></center>

Queues provide asynchronous communication: each process controls its own flow and get messages when **they** are ready. As a consequence, message queues inherently enhance workload distribution given that computers will keep retrieving one more message and processing it until all incoming messages have been processed. Imagine the other scenario where we pre-assign messages to consumers before hand. It might happen that one process has finished processing all of its data whereas another one is struggling with its own workload. Since messages were assigned exclusively to the slow process, the quick one cannot jump over and help it finishing its job. We have idle resources even though there is work to be done. Point for message queues.

Need to create a fail-proof system that gracefully handles machine failures? Message queues can also help you with that. For instance, [Amazon SQS](https://aws.amazon.com/sqs/) has a [visibility timeout](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/AboutVT.html): a period during which the consumer need to process the message and delete it from the queue. In case the message isn't deleted in viable time - such as when the process is stalled or has died - the message queue automatically routes the message to another consumer. You may even protect yourself from the machine hosting the message queue failing by using queues with replication capabilities, such as [Apache Kafka](https://cwiki.apache.org/confluence/display/KAFKA/Kafka+Replication).

The last point I would like to write about message queues is about system decoupling. Queues are language-agnostic. A process written in Go can produce messages that will be consumed by a Python process without many troubles. Simply use the appropriate libraries and packages and you are ready to go. In fact, even different versions of the system can live happily side-by-side (but don't give yourself headache without reason).

With these points in mind, message queues are my newest friends for designing and implementing distributed systems. I'll leave you with some suggestions of message queue systems to take a look.

* [RabbitMQ](https://www.rabbitmq.com/)
* [ZeroMQ](http://zeromq.org/)
* [StormMQ](https://en.wikipedia.org/wiki/StormMQ)
* [Apache ActiveMQ](https://en.wikipedia.org/wiki/Apache_ActiveMQ)
* [Apache Kafka](http://kafka.apache.org/)
* [Amazon SQS](http://aws.amazon.com/documentation/sqs/)

Consider using one of them in your next project and please get in touch with me and share your thoughts on the experience.
