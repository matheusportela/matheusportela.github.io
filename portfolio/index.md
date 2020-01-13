---
layout: page
title: Portfolio
---

## Professional Projects

###  Justworks (May 2019 - Present)
_Technologies: `Web Development`, `Ruby`, `Rails`, `JavaScript`, `React`, `Sidekiq`, `TDD`, `Third-Party APIs`_

_Site: [justworks.com](https://justworks.com)_

###  Control and Network Lab - New York University (Sep 2018 - May 2019)
_Technologies: `Optimization`, `MATLAB`, `Neural Networks`, `Research`_

###  Bxblue (Mar 2017 - Jul 2018)
_Technologies: `Ruby`, `Rails`, `JavaScript`, `React`, `TDD`, `Third-party APIs`_

_Site: [bxblue.com.br](https://bxblue.com.br)_

###  Simbiose Ventures (Nov 2015 - Feb 2017)
_Technologies: `Python`, `NoSQL`, `Scikit-learn`, `Web Crawlers`, `Big Data`, `API Design`, `Third-party APIs`_

_Site: [slicingdice.com](https://slicingdice.com)_

## Top 5 Projects

### Black Hole Ray Tracing (Nov 2019 - Dec 2019)
_Technologies: `C++`, `Eigen`, `TBB`, `Multi-Threading`_<br>

As my final project for the Computer Graphics course at NYU, I implemented a non-linear Black Hole ray tracer algorithm from scratch in C++, using piecewise linear approximation and simulating gravitational lensing effects, besides implementing texture mapping and ray-disk intersection. My project closely followed the approach developed by [Antonelli](https://rantonels.github.io/starless/) and [Brant](https://dmitrybrant.com/2018/12/11/ray-tracing-black-holes). The following images were rendered using my project.

<div style="display: flex;">
    <img src="/assets/images/black-hole-0.gif" style="width: 350px; height: 350px;" />
    <img src="/assets/images/black-hole-1.gif" style="width: 350px; height: 350px;" />
    <img src="/assets/images/black-hole-2.gif" style="width: 350px; height: 350px;" />
</div>


### Web Search Engine (Sep 2019 - Nov 2019)
_Technologies: `C++`, `Python`, `Web Crawling`, `Multi-Threading`, `Data Compression`, `Inverted Index`, `Data Structures`_<br>

In the Web Search Engines course at NYU, I had to implement a web search engine from scratch. First, I developed a multi-threaded web crawler in Python able to crawl at least 100 pages/minute while prioritizing new and important domains and avoiding visiting the same domain concurrently. Then, I implemented a web search engine in C++ from scratch, without using third-party libraries. In doing so, I created an inverted index mapping all words to the documents containing them, implemented data compression using the variable-byte technique, wrote Okapi BM25 as the ranking function, and optimized the code in order to process more than 6.7 million web pages, containing almost 28 million unique terms, in about 3 hours and using less than 3 GB of RAM. The inverted index file size is 17 GB before compression and 6 GB after.

### Distributed Twitter Clone (Nov 2018 - Dec 2018)
_Technologies: `Go`, `Raft`, `Protobuf`, `JavaScript`, `Web Components`, `Microservices`, `Consensus Algorithms`_<br>
_Code: [GitHub](https://github.com/mds796/CSGY9223-Final)_

In the Distributed Systems course at NYU, our team implemented a Twitter clone in a Microservices Architecture. By using Raft as a consensus algorithm, we replicated our microservices in at least 3 machines with inherent fault tolerance, so even if a machine halted, the service would still be available. Our project received the highest grade in the class.

### Reinforcement Learning for Stochastic Multiagent Systems (Jan 2015 - Dec 2015)
_Technologies: `Python`, `Numpy`, `OpenAI Gym`, `Reinforcement Learning`, `Q-learning`, `Multiagent Systems`, `Bayesian Programming`_<br>
_Code: [GitHub](https://github.com/matheusportela/Multiagent-RL)_

My undergraduate thesis was on **Artificial Intelligence** applied to **Robotics**, in which I studied how to apply Reinforcement Learning algorithms to stochastic multiagent systems. Techniques such as Q-learning with function approximation, Bayesian Programming and Steering Behaviors were applied to Pac-Man ghosts using the [UC Berkeley Pac-Man simulator](http://ai.berkeley.edu/home.html). During the work I published two papers, a peer-reviewed and a non peer-reviewed one, and developed a **Python** system. Moreover, my thesis received the maximum grade.

### UnBall Robot Soccer Team (Mar 2014 - Dec 2015)
_Technologies: `C++`, `Python`, `Assembly`, `Arduino`, `ROS`, `OpenCV`, `Microsoft Kinect`, `Xbee`, `Electronics`, `Control Systems`_<br>
_Code: [GitHub](https://github.com/unball/ieee-very-small)_

In 2010, I joined the [UnBall Robot Soccer Team](http://equipeunball.com.br/), a university student team with one goal: build robots that can play soccer. I helped developing the AI and Computer Vision systems initially and, in 2014, I became the team Coordinator. My responsibilities included restructuring the team, which had been shut down at the time, and rebuild the project from scratch. I have worked in all technical areas, including AI, Computer Vision, Firmware, Communication, Control Systems, Electronics and 3D Printing, besides other areas such as Management, Recruitment and Finances. Since 2014, the team has participated in several national and international competitions and acquired financial stability and a sustainable recruitment process. In 2016, I assisted the UnBall Coordinator by being a Counselor, overseeing the future of the team.

## Other Personal Projects

### Ray Tracing Rendering (Oct 2019)
_Technologies: `C++`, `Eigen`, `TBB`, `Multi-Threading`_<br>

In the Computer Graphics course at NYU, I implemented a ray tracing algorithm from scratch in C++, i.e. rendering multiple primitives (spheres and triangles), simulating light (diffuse, specular, and ambient), reflection, colors, shadows, and perspective. I also implemented parallel pixel processing using [Intel TBB](https://github.com/intel/tbb) to speed up computations. The following images were rendered using my project.

<div style="display: flex;">
    <img src="/assets/images/ray_tracing_1.png" style="width: 350px; height: 350px;" />
    <img src="/assets/images/ray_tracing_2.gif" style="width: 350px; height: 350px;" />
</div>

### Lispy (Feb 2018 - May 2018)
_Technologies: `Python`, `Lisp`, `TDD`, `Compilers`_<br>
_Code: [GitHub](https://github.com/matheusportela/lispy)_

Since I had never taken a Compilers course and I am truly interested in Lisp, I started making my own Lisp interpreter for didactic purposes. Using Python and applying TDD techniques, it currently works executing a script from a file or as a REPL interpreter many functional capabilities, such as recursive functions and functions as first-order citizens.

### Magic Chain (Nov 2016)
_Technologies: `Blockchain`, `Ethereum`, `Solidity`, `JavaScript`, `jQuery`, `HTML`, `CSS`_<br>
_Code: [GitHub](https://github.com/matheusportela/magic-chain)_

During the [Cotidiano Hackathon on Blockchain technology](https://guiadobitcoin.com.br/aceleradora-de-startups-promovera-hackathon-com-o-tema-blockchain-em-brasilia/), I and two friends developed a [Magic: The Gathering](https://magic.wizards.com/en) marketplace so players could sell, buy and trade cards. Using the Ethereum Blockchain as the underlying technology was an interesting idea since the platform had its own token for exchanges, a built-in user rating system and audit trails to third-parties. We we awarded with the **2nd place** among about 10 teams due to our finished prototype and the good fit between Blockchain and our product.

### Collatz Conjecture (Aug 2016)
_Technologies: `Haskell`_<br>
_Code: [GitHub](https://github.com/matheusportela/collatz)_

After watching a video on the [Collatz Conjecture](https://www.youtube.com/watch?v=5mFpVDpKX70), if decided to implement it in Haskell.

### Control Your Laptop (Jul 2016)
_Technologies: `Python`, `Arduino`, `Infrared Sensors`, `Digital Communication`_<br>
_Code: [GitHub](https://github.com/matheusportela/control-your-laptop)_

During my [#100DaysOfCode initiative](http://matheusportela.com/day-29-control-your-laptop), I realized it was a shame for a programmer to get out of my bed in order to play, pause and stop videos when my laptop was connected to my TV. Then, I reverse engineered my TV remote control protocol and built a simple receiver, using Arduino and an Infrared Receiver, to make my remote control transmit commands to my computer. You can check this prototype working [here](http://matheusportela.com/day-29-control-your-laptop).

### Enigma Machine Simulator (Jun 2016 - Jul 2016)
_Technologies: `JavaScript`, `Node.js`, `TDD`, `Simulators`_<br>
_Code: [GitHub](https://github.com/matheusportela/enigma-machine/)_

As part of my [#100DaysOfCode initiative](/day-1-enigma), I developed an [Enigma machine](https://en.wikipedia.org/wiki/Enigma_machine) simulator from the ground up. For about three weeks, I've studied the machine technical details, wrote the simulator code in JavaScript and Node.js using a Test-Driven Development approach, created a web interface, and documented the steps in blog articles. You can check the simulator [here](/enigma).

### Cipher Algorithms (May 2016 - Jun 2016)
_Technologies: `C`, `Python`, `Python Extensions`_<br>
_Code: [Vigenere Cipher](https://github.com/matheusportela/vigenere-cipher) and [Caesar Cipher](https://github.com/matheusportela/caesar-cipher)_

I started studying cryptography in 2016 with a hands-on approach by implementing some of the most common cryptographic algorithms and learn how to combine C code to Python modules. Thus I implemented the Vigenère and Caesar cipher algorithms.

### Distributed Computing with Intel Galileo Boards (Sep 2015)
_Technologies: `Distributed Systems`, `IoT`, `C`_<br>
_Code: [GitHub](https://github.com/matheusportela/teemeteam)_

In the "Se Vira II" Hackathon, on the topic of IoT, that took place at the University of Brasília, I and two friends wanted to play with distributed computing. We used 3 Intel Galileo boards, connected using Ethernet cables, to calculate the minimum and maximum values of large lists of numbers in a distributed fashion, using an approach similar to Map-Reduce implemented from scratch. All boards ran exactly the same software, which means they could operate either as a node or as the coordinator.

### Maestro (Sep 2015)
_Technologies: `C`, `C++`, `Python`, `Node.js`, `Arduino`, `3D Printers`, `Servomotors`, `Myo`, `GoPro`_<br>
_Code: [GitHub](https://github.com/matheusportela/maestro)_

During the Hackathon Globo, one of the largest hackathons in Brazil whose topic was "How technology can change the way we produce and consume media?", my team developed Maestro: a prototype of a hands-free control for TV cameras. Using Myo, a sensor capable of detecting movements of the arm, a journalist would be able to control pan and tilt of cameras and select which camera to broadcast. That a look at the working prototype:

<center><iframe width="420" height="315" src="https://www.youtube.com/embed/bSnN2MHOCd4" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></center>

### Poïesis (Mar 2015 - Jun 2015)
_Technologies: `C++`, `SDL`, `Game Development`, `Particle Physics Simulation`, `Entity System`, `Spatial Partitioning`_<br>
_Code: [GitHub](https://github.com/matheusportela/Poiesis)_

During the first semester of 2015, I took the **Game Development class** at my university where we had to develop a game in a group with artists and musicians. The result was **Poïesis**, a **C++** game where you are a cell trying to survive in a hostile environment. The game engine was completely developed from scratch using and **SDL** for low-level OS integration. During this work, I decided to use an Entity System approach, Quad-tree spatial partitioning and developed a Particle and Physics System, which led me to an **Honorable Mention** among the 12 games evaluated.

### Counting Cars (Jan 2015 - Mar 2015)
_Technologies: `C#`, `XAML`, `.NET`_

As a freelancer, I worked with a friend to develop a GUI that helped collecting human input to count cars from traffic cameras. We used Microsoft technologies to create a desktop application which received input from a joystick and buttons.

### The A*maze*ing Experience (Jan 2015)
_Technologies: `C#`, `Unity 3D`, `Game Development`_<br>
_Code: [GitHub](https://github.com/imota/aMAZEing-experience)_

In 2015, I was a participant of the [**Global Game Jam**](http://globalgamejam.org/): a worldwide event where developers, artists, and musicians meet in their cities to produce an entire computer game in 48 hours. In Brasília, the event took place at the [Behold Studios](http://beholdstudios.com.br/) HQ, under the theme "What do I do now?". Without sleeping, me and 3 more friends could finish our game, [**the aMAZEing experience**](http://globalgamejam.org/2015/games/amazeing-experience), using **C#** and **Unity 3D**. It was my first game ever and I am really proud of it.

### Simpletable (Aug 2014)
_Technologies: `Python`, `HTML`_<br>
_Code: [GitHub](https://github.com/matheusportela/simpletable)_

Simpletable is a lightweight **Python** module for generating simple HTML tables without requiring the installation of any third-party libraries.

### Network Security (Jun 2014 - Dec 2014)
_Technologies: `Python`, `Numpy`, `Third-party APIs`, `Network Security`, `Computer Networks`, `Routes`, `Switches`, `Web Application Firewalls`_

In 2014, I had the opportunity to work with network security at IPe - Network Engineering. During this period, I could work with some cutting-edge technology, such as Web Application Firewalls and Advanced Persistent Threats. I could also develop a project to provide **Machine Learning** capabilities to automatically detect intrusion and hacker attacks (with cutting edge academic knowledge), using **Python** and **Numpy**, as well as **Python scripts** to communicate with third-party appliances. I have also substantially improved business skills, such as competition analysis, benchmarking, development of vulnerability assessment methodologies and selling and buying products.

### Didactic Assembler (Apr 2014 - Jul 2014)
_Technologies: `C`, `Assembly`, `Compilers`_<br>
_Code: [GitHub](https://github.com/matheusportela/sb-assembler)_

As a student in Systems Software course, we had the task of writing our own assembler, which would translate a source file written in didactic assembly language to binary output, the last should run in our own simulator. The code was written in pure **C** language.

### Gaze Enhanced Voice Recognition (Dec 2012 - Feb 2013)
_Technologies: `Python`, `Qt`, `PyQt`, `Win32 API`, `Microsoft Speech Recognition`, `Human-Computer Interfaces`, `Research`_

During my internship at the [CSIRO](http://www.csiro.au), in Australia, I could develop a great project: using gaze trackers to enhance voice recognition systems. Supervised by David Rozado, a great friend, we created a GUI using **Python** (with PyQt) and **Microsoft Speech Recognition** and designed user tests to prototype an idea of how to integrate these systems and make hands-free voice recognition possible. Since a picture is worth a thousand words, check out the video below to have an idea of our system. You can also read our [paper](/publications), published at OZCHI 2014.

<center><iframe width="420" height="315" src="https://www.youtube.com/embed/xdBoNsMthr8" frameborder="0" allowfullscreen></iframe></center>

## Peer-Reviewed Papers

### State Estimation and Reinforcement Learning for Behavior Selection in Stochastic Multiagent Systems
**Authors:**
Matheus Vieira Portela - University of Brasilia, Brasilia, Brazil
Guilherme Novaes Ramos - Department of Computer Science, University of Brasilia, Brasilia, Brazil

**Published at:** XIV Brazilian Symposium of Digital Games and Entertainment - 2015 - Proceedings of SBGames 2015 - Computing Track - Short Papers

**Publisher:** SBC - Brazilian Computing Society

**Publication date:** November 11-13, 2015

**Download:** [PDF](http://www.sbgames.org/sbgames2015/anaispdf/computacao-short/147936.pdf)

**Abstract:** Intelligent agents can act based on sensor measurements in order to fulfill their goals. In dynamic systems, agents must adapt its behavior selection processes to reflect the changing system state since behaviors that previously were considered the best choice may become sub-optimal. Multiple agents that co-exist in the environment is one example of such a dynamic system. The problem is even greater when stochastic systems are considered, since the states the agents are actually in are unknown. This work proposes a learning algorithm for stochastic multiagent systems, in which Bayesian programming is used for state estimation and Q-learning provides learning capabilities to the agents. An experimental setup using electronic games is described to evaluate the effectiveness of this approach.

### Gaze Enhanced Speech Recognition for Truly Hands-Free and Efficient Text Input During HCI
**Authors:**
Matheus Vieira Portela - University of Brasilia, Brasilia, Brazil
David Rozado - CSIRO, QLD, Brisbane, Australia

**Published at:** OzCHI '14 Proceedings of the 26th Australian Computer-Human Interaction Conference on Designing Futures: the Future of Design

**Publisher:** ACM [http://dl.acm.org/citation.cfm?id=2686679](http://dl.acm.org/citation.cfm?id=2686679)

**Publication date:** December 2, 2014

**Download:** [PDF](/assets/files/portela-gaze-enhanced-speech-recognition.pdf)

**Abstract:** The performance of current speech recognition algorithms is well below that of human speech recognition, with high number of misrecognized words in quiet environments and degrading even further in noisy ones. Therefore, hands-free interaction remains a deeply frustrating experience. In this work, we present an innovative form of correcting misrecognized words during a speech recognition task by using gaze tracking technology in a multimodal approach. We propose to employ the user's gaze to point at misrecognized words and select appropriate alternatives. We compare the performance of this multimodal approach with traditional modalities of correcting words: usage of mouse and keyboard and usage of voice alone. The results of the user study show that whereas the proposed system is not as fast as using mouse and keyboard for correction, gaze enhanced correction significantly outperforms voice alone correction and is preferred by the users, offering a truly hands-free means of interaction.

## Non Peer-Reviewed Papers

### Bayesian Programming and Reinforcement Learning in Stochastic Multiagent Systems
**Authors:**
Matheus Vieira Portela - University of Brasilia, Brasilia, Brazil
Guilherme Novaes Ramos - Department of Computer Science, University of Brasilia, Brasilia, Brazil

**Published at:** Graduate School Workshop at the Department of Computer Science - University of Brasilia

**Publication date:** October 16-17, 2015

**Download:** [PDF](/assets/files/wpos-2015.pdf)

**Abstract:** Intelligent agents act based on sensor measurements in order to fulfill their goals. When the environment is dynamic, such as a multiagent system, agents must adapt its actions selection processes to reflect the ever changing system state since behaviors that previously were considered the best choice may becomes sub-optimal. The problem is even greater when stochasticity is taken into account, since the environment true state is unknown to the agents. This work proposes a learning algorithm for stochastic multiagent systems, in which Bayesian programming is used for state estimation and Q-learning with function approximation provides learning capabilities so as agents can select the appropriate behaviors. An experimental setup to evaluate the effectiveness of this approach using electronic games is described, as well as the preliminary results.

## Undergraduate Thesis (Portuguese)

### Seleção de Comportamentos em Múltiplos Agentes Autônomos com Aprendizagem por Reforço em Ambientes Estocásticos
_Behavior selection for multiple autonomous agents with reinforcement learning in stochastic environments_

**University of Brasília**

**Date:** December 4, 2015

**Download:** [PDF](http://bdm.unb.br/bitstream/10483/15302/1/2015_MatheusVieiraPortela_tcc.pdf)

**Abstract (Portuguese):** Agentes inteligentes agem baseados nas suas medições sensoriais a fim de alcançar seus objetivos. Em ambientes dinâmicos, como sistemas multiagentes, agentes devem adaptar seus processos de seleção de ações de acordo com o estado do sistema mutável, uma vez que comportamentos anteriormente considerados adequados podem tornar-se sub-ótimos. Tal problema é ainda maior se o ambiente é estocástico, forçando os agentes a lidarem com incertezas. Esse trabalho propõe um algoritmo de aprendizado por reforço para sistemas multiagentes estocásticos, utilizando programação bayesiana para estimação de estados e Q-learning com aproximação de funções para prover aos agentes a capacidade de aprender a selecionar os comportamentos mais adequados. Experimentos indicam resultados positivos para a abordagem, onde agentes aprenderam a cooperar, de forma autônoma, em um jogo eletrônico estocástico multiagente.
