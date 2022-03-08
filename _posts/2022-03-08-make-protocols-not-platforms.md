---
layout: post
status: publish
published: true
title: "Make protocols, not platforms"
date: '2022-03-08 11:00:00 +0100'
categories:
- Decentralized Web
tags:
- decentralized-web
comments: []
---

The web is decentralized from its inception. The [TCP/IP stack](https://en.wikipedia.org/wiki/Internet_protocol_suite) assumes no central hub so computers can talk to each other. [HTTP](add link) requires no login for individuals to spin their own websites and connect to existing ones. [Email](https://en.wikipedia.org/wiki/Email_address) works by allowing users to interact with all other email providers seamlessly. [Podcasts are published in RSS feeds](https://en.wikipedia.org/wiki/Podcast#History) so podcast players can find, download, and play the newest episodes, no central service required (although Spotify is [building its walls by offering insane amounts of cash for exclusivity rights](https://www.fastcompany.com/3044956/the-new-music-streaming-war-is-about-exclusivity)).

It's interesting to contrast this with how social networks came to be. Since their beginning, creating a profile, following other profiles, and publishing content were possible only within a platform's boundaries. A Facebook user cannot follow someone on Twitter. An Instagram influencer cannot check pictures posted on Reddit.

Compare Facebook to email, for example. If emails behaved like social networks, one would expect to only be able to send and receive emails from the users of the same provider. Gmail users wouldn't be able to talk to Outlook users. Each person would have 5 different email accounts, one for each major provider, and we would need to copy data from one account to the other to make it visible to the users on the other platform. In fact, it would behave exactly like what we currently have with Direct Messaging in the major social networks (Facebook is trying to unify their products' DM systems into a single one but we still won't be able to talk to someone on Twitter, for instance).

Thankfully, email doesn't work like that. But it is interesting to think why there is such a big different in how older Internet features behave compared to newer tech products. My humble opinion is that _the web is protocol-oriented._

Email is open to anyone to create their own servers and clients by design _because it is not a service nor platform, but a protocol._ Based on the [email specification](https://datatracker.ietf.org/doc/html/rfc5321), programmers were able to create their providers. It is true that some providers are more popular than others, mainly Gmail, but no singular company _owns_ email behind closed walls.

It seems to me that if we want a better Internet, we need to **make protocols, not platforms.**

For instance, [Solid](https://solidproject.org) is a protocol that wants to be the [backbone of storing and sharing user data](https://en.wikipedia.org/wiki/Solid_(web_decentralization_project)), pioneered by [Tim Berners-Lee](https://en.wikipedia.org/wiki/Tim_Berners-Lee). With such a protocol, the user would own their data, not the social network.

It remains to be seen if decentralized protocols will become widespread on the Internet of the future, given that current technology behemoths have absolutely no incentive to use solutions that will reduce their control over people's data and will (and their profits). Legislative efforts could push them in the right direction, though, and the [day of Big Tech regulation is nearing](https://knowledge.wharton.upenn.edu/article/regulating-big-tech-is-a-day-of-reckoning-coming/).
