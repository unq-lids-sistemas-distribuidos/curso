# Sistemas Distribuidos (en Erlang)

Este material está basado en el excelente material de Johan Morellius.

These are a set of assignments that we I have used in several courses in Distributed Systems. They have been used to exemplify different systems, algorithms or aspects such as performance and fault tolerance.

The students have had a week of half-time study to complete the assignments and write a small report on their findings. After having handed in the reports each assignment is discussed during a seminar where one can also extend the system or do experiments using more computers.

The assignments do assume basic understanding of Erlang but I've deliberately used a limited set of Erlang functionality. I have not used OTP since I think that this will hide complexity or for many of the smaller assignments add too much code. Nor do I use some of the libraries that handle group communication or global registry. The aim is often for the students to develop these themself and better understand the pros and cons of different strategies.

All assignments are work in progress and are likely to change in the future. All assignments are licensed under Creative Commons Attribution.

## An Erlang primer [x]

This is not a crash course in Erlang since there are plenty of tutorials
available on the web. I will however describe the tools that you need so that you can get a programming environment up and running. I will take for granted that you know some programming languages, have heard of functional programing and that recursion is not a mystery to you.

-   [01-crash](./01-crash.pdf)

## The Mandelbrot set (Opcional)

Calculating the Mandelbrot set is an easy task that can be done in parallel if we have multiple cores or several machines. This implementation is not the fastest on earth but it serves its purpose of being a fin task to start with; it can easily be improved.

-   [02-mandel](./02-mandel.pdf)

## Primy: finding a large prime (Opcional)

Your task will be to implement a distributed system that will find large primes. The system should have one server that is in control of the computation and a dynamic set of workers that are assigned numbers to test for primarity.

-   [03-primy](./03-primy.pdf)

## Rudy: a small web server [x]

Your task is to implement a small web server in Erlang. The aim of this exercise is that you should be able to: describe the procedures for using a socket API, describe the structure of a server process and describe the HTTP protocol. As a side effect you will also learn how to use do some Erlang programming.

-   [04-rudy.pdf](./04-rudy.pdf)

## Namy: un name server distribuido [x]

La tarea es implementar un _name server_ distribuido similar a DNS. En lugar de guardar direcciones vamos a guardar identificadores de _hosts_. Nuestro servidor de DNS no podrá interoperar con servidores de DNS reales pero nos mostrará los principios de caching de información en una estructura de árbol.  

-   [05-namy.pdf](./05-namy.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 13: Name Services.

## Routy: a small routing protocol [x]

Your task is to implement a link-state routing protocol in Erlang. The link-state protocol is used in for example OSPF, the most used routing protocol for Internet routers. The aim of this exercise is that you should be able to: describe the structure of a link-state routing protocol, describe how a consistent view is maintained and reflect on the problems related to network failures.

-   [06-routy.pdf](./06-routy.pdf)

## Detector [x]

Failure detectors are the heart of distributed systems. This small tutorial will show you how the failure detectors work in Erlang and their limitations.

-   [07-detector.pdf](./07-detector.pdf)

## Casty (Opcional)

In this assignment you will build a streaming media network. We will play around with shoutcast streams and build proxies, distributors and peer-to-peer clients. You will use the Erlang bit-syntax to implement a communication protocol over HTTP. The parser will be implemented using higher order functions to hide the socket interface. You will learn how to decode a mp3 audio stream and make it available for connecting media players. Sounds fun? - Let's go!

-   [08-casty.pdf](./08-casty.pdf)

## Loggy: a logical time logger [x]

In this exercise you will learn how to use logical time in a practical example. The task is to implement a logging procedure that receives log events from a set of workers. The events are tagged with the Lamport time stamp of the worker and the events must be ordered before written to stdout. It's slightly more tricky than one might first think.

-   [09-loggy.pdf](./09-loggy.pdf)

## Goldy: a distributed game (Opcional)

This seminar will serve two purpose; learning how to program a distributed application in Erlang and understanding why distributed applications are not as simple to control as it might first seam.

-   [10-goldy.pdf](./10-goldy.pdf)

## Toty (Opcional)

The task is to implement a total order multicast service using a distributed algorithm. The algorithm is the one used in the ISIS system and is based on requesting proposals from all nodes in a group.

-   [11-toty.pdf](./11-toty.pdf)

## Muty (Opcional)

Your task is to implement a distributed mutual-exclusion lock. The lock will use a multicast strategy and work in a asynchronous network where we do not have access to a synchronized clock. You will do the implementation in three versions: the dead-lock prone, the unfair and the Lamport clocked. Before you start you should have good theoretical knowledge of the multicast algorithm and how Lamport clocks work.

-   [12-muty.pdf](./12-muty.pdf)

## Groupy: a group membership service (Opcional)

This is an assignment were you will implement a group membership service that provides atomic multicast. The aim is to have several application layer processes with a coordinated state i.e. they should all perform the same sequence of state changes. A node that wish to perform a state change must first multicast the change to the group so that all nodes can execute it. Since the multicast layer provides total order, all nodes will be synchronized.

-   [13-groupy.pdf](./13-groupy.pdf)

## Snapy: the search for dead marbles (Opcional)

In this exercise you will learn how to implement a snap-shot algorithm. We will use a very simple scenario with a set of workers that create and share _marbles_ with each other. The problem is to find out which marbles are alive so that references to dead marbles can be removed. It's in a sense a simplified garbage collection problem. The problem is simplified by the fact that the data structures, the marbles, are atomic and that we do not create duplicates of marbles. We could have solved the problem using a simpler solution but why not
play around with a snap-shot algorithm.

-   [14-snapy.pdf](./14-snapy.pdf)

## Garby: a distributed grabage collector (Opcional)

In this exercise you will learn how to implement a snap-shot algorithm. As an example we will try to detect garbage in a distributed computing. This is tricky and as you will see, a quite expensive operation. Not taking the snap-shot in itself but how to interpret the snap-shot and how to make the most use of the gained information.

-   [15-garby.pdf](./15-garby.pdf)

## Opty: optimistic concurrency control (OK)

In this session you will implement a transaction server using optimistic concurrency control. You will also learn how to implement a updatable data structure in Erlang that can be accessed by concurrent, possibly distributed, processes. Before you start you should know how optimistic concurrency control with backwards validation works.

-   [16-opty.pdf](./16-opty.pdf)

## Timey: time based concurrency control (Opcional)

In this session you will implement a transaction server using time based concurrency control. You will also learn how to implement a updatable data structure in Erlang that can be accessed by concurrent, possibly distributed, processes. Before you start you should know how time based concurrency control.

-   [17-timey.pdf](./17-timey.pdf)

## Paxy: the paxos protocol (Opcional)

This exercise will give you the opportunity to learn the Paxos algorithm for gaining consensus in a distributed system. You should know the basic operations of the algorithm but you do not have to know all the details, that is the purpose of this exercise.

-   [18-paxy.pdf](./18-paxy.pdf)

## Chordy: a distributed hash table (Opcional)

In this assignment you will implement a distributed hash table following the Chord scheme. In order to understand what you're about to do you should have a basic understanding of Chord and preferably have read the original paper.

-   [19-chordy.pdf](./19-chordy.pdf)
