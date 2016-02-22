# Sistemas Distribuidos (en Erlang)

Este material está basado en el excelente material de Johan Morellius.

Estos son una serie de trabajos usados en diversos cursos en Sistemas Distribuidos. Los mismos fueron usados para ejemplificar diferentes sistemas, algoritmos o aspectos como performance y fault tolerance.

La modalidad del curso será la de taller y duarante el recorrido del curso los alumnos irán estudiando los diversos aspectos de los sistemas distribuidos a medida que resuelven los problemas que se van presentando y experimentan en el laboratorio. Una vez finalizado el trabajo se pide a los alumnos que escriban un reporte para ser discutido en clase sobre los allazgos, problemas que se presentaron y posibles extensiones.

Los trabajos asumen cierto connocimiento básico de Erlang, pero se ha limitado el uso a un conjunto de funcionalidades básicas. Se omitió el uso de OTP, dado que se piensa que esconde la complejidad subyacente de muchos de los trabajos. Tampoco que usan librerías que manejan comunicación de grupos o registro global. EL objetivo es que los alumnos desarrollen las soluciones a estos problemas entendiendo mejor los pros y contras de las diferentes estrategias. Sin embargo, se recomienda a aquellos interesados al promediar el curso o posterior al mismo aparender los servicios y beneficios de OTP, base fundamental del desarrollo de sistemas altamente escalables y tolerantes a falla en Erlang.

Los trabajos están licenciados bajo Creative Commons Attribution.

## Una Introducción a Erlang [x]

Esto no es un curso rápido de Erlang dado que hay muchos tutoriales disponibles en la web. Sin embargo en se describirán las herramientas que se necesitan para tener un ambiente andando. Se da por sentado que tienen una cierta experiencia en lenguajes de programación y programación funcional y particularmente recursión.

-   [01-crash](./01-crash.pdf)

## El Conjunto de  Mandelbrot (Opcional)

Calcular un conjunto de Mandelbrot es una tarea que puede ser hecha en paralelo si se tienen varios cores o varias máquinas. La implementación brindada no es la más rápida pero sirve con el propósito de ser una tarea para comenzar; puede ser facilmente mejorarda.

-   [02-mandel](./02-mandel.pdf)

## Primy: encontrando números primos grandes (Opcional)

En esta tarea hay que implementar un sistema distribuido que encuentre números primos grandes. El sistema debe tener un server que se encarga de controlar el cálculo y un conjunto dinámico de workers a los que se asigna testear si un número dado es primo o no.

-   [03-primy](./03-primy.pdf)

## Rudy: un pequeño web server [x]

En esta tarea se debe implementar un pequeño web server. El objetivo de este ejercicio es ser capaces de: describir el procedimiento para usar la API de __sockets__, describir la estructura de un proceso server y describir el protocolo __HTTP__. Como efecto secundario se aprenderá a utilizar algunas caraterísticas de Erlang.

-   [04-rudy.pdf](./04-rudy.pdf)

## Namy: un name server distribuido [x]

La tarea es implementar un _name server_ distribuido similar a DNS. En lugar de guardar direcciones vamos a guardar identificadores de _hosts_. Nuestro servidor de DNS no podrá interoperar con servidores de DNS reales pero nos mostrará los principios de caching de información en una estructura de árbol.

-   [05-namy.pdf](./05-namy.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 13: Name Services.

## Routy: un pequeño protocolo de ruteo [x]

La tarea es implementar un protocolo de ruteo __link-state__ en Erlang. El protocolo link-state es usado por ejemplo en OSPF, el protocolo más usado por los routers de Internet. El objetivo de este ejercicio es ser capaces de: describir la estructura general del un protocolo de ruteo link-state, describir como se mantiene una vista consistente y reflejar los problemas relacionados a fallos de red.

-   [06-routy.pdf](./06-routy.pdf)

## Detector [x]

Los detectores de fallas son el corazón de los sistemas distribuidos. En este pequeño tutorial se mostrará como funcionan en Erlang y sus limitaciones.

-   [07-detector.pdf](./07-detector.pdf)

## Casty (Opcional)

En esta tarea construiremos una red de media streaming. Jugaremos con streams de _shoutcast_ y construiremos proxies, distributors y clientes peer-to-peer. Usaremos la __bit-syntax__ de Erlang para implementar el protocolo de comunicación sobre HTTP. El parser será implementado usando funciones de alto orden para esconder la interfaz de sockets. Aprenderemos como decodificar un stream de audio mp3 y ponerlo disponible para la conexión de reproductores de audio.

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
