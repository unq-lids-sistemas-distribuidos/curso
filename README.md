# Sistemas Distribuidos (en Erlang)

Este curso está basado en el excelente material de **Johan Morellius**  (https://people.kth.se/~johanmon/dse.html).

Estos son una serie de trabajos usados en diversos cursos en Sistemas Distribuidos. Los mismos fueron usados para ejemplificar diferentes sistemas, algoritmos o aspectos como performance y fault tolerance.

La modalidad del curso será la de taller y durante el recorrido del curso los alumnos irán estudiando los diversos aspectos de los sistemas distribuidos a medida que resuelven los problemas que se van presentando y experimentan en el laboratorio. Una vez finalizado el trabajo se pide a los alumnos que escriban un reporte para ser discutido en clase sobre los hallazgos, problemas que se presentaron y posibles extensiones.

Los trabajos asumen cierto connocimiento básico de Erlang, pero se ha limitado el uso a un conjunto de funcionalidades básicas. Se omitió el uso de OTP, dado que se piensa que esconde la complejidad subyacente de muchos de los trabajos. Tampoco que usan librerías que manejan comunicación de grupos o registro global. EL objetivo es que los alumnos desarrollen las soluciones a estos problemas entendiendo mejor los pros y contras de las diferentes estrategias. Sin embargo, se recomienda a aquellos interesados al promediar el curso o posterior al mismo aparender los servicios y beneficios de OTP, base fundamental del desarrollo de sistemas altamente escalables y tolerantes a falla en Erlang.

Los trabajos están licenciados bajo Creative Commons Attribution.

## Una Introducción a Erlang [x]

Esto no es un curso rápido de Erlang dado que hay muchos tutoriales disponibles en la web. Sin embargo en se describirán las herramientas que se necesitan para tener un ambiente andando. Se da por sentado que tienen una cierta experiencia en lenguajes de programación y programación funcional y particularmente recursión.

-   [01-crash](./labs/01-crash.pdf)

## El Conjunto de  Mandelbrot (Opcional)

Calcular un conjunto de Mandelbrot es una tarea que puede ser hecha en paralelo si se tienen varios cores o varias máquinas. La implementación brindada no es la más rápida pero sirve con el propósito de ser una tarea para comenzar; puede ser facilmente mejorarda.

-   [02-mandel](./02-mandel.pdf)

## Primy: encontrando números primos grandes (Opcional)

En esta tarea hay que implementar un sistema distribuido que encuentre números primos grandes. El sistema debe tener un server que se encarga de controlar el cálculo y un conjunto dinámico de workers a los que se asigna testear si un número dado es primo o no.

-   [03-primy](./03-primy.pdf)

## Rudy: un pequeño web server [x]

En esta tarea se debe implementar un pequeño web server. El objetivo de este ejercicio es ser capaces de: describir el procedimiento para usar la API de __sockets__, describir la estructura de un proceso server y describir el protocolo __HTTP__. Como efecto secundario se aprenderá a utilizar algunas caraterísticas de Erlang.

-   [04-rudy.pdf](./labs/04-rudy.pdf)

## Namy: un name server distribuido [x]

La tarea será implementar un _name server_ distribuido similar a _DNS_. En lugar de direcciones vamos a almacenar identificadores de procesos a hosts. No va a poder inter-operar con servidores de DNS reales pero nos mostrará los principios de caching en una estructura de árbol.

-   [05-namy.pdf](./labs/05-namy.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 13: Name Services.

## Routy: un pequeño protocolo de ruteo [x]

La tarea es implementar un protocolo de ruteo __link-state__ en Erlang. El protocolo link-state es usado por ejemplo en OSPF, el protocolo más usado por los routers de Internet. El objetivo de este ejercicio es ser capaces de: describir la estructura general del un protocolo de ruteo link-state, describir como se mantiene una vista consistente y reflejar los problemas relacionados a fallos de red.

-   [06-routy.pdf](./06-routy.pdf)

## Detector [x]

Los detectores de fallas son el corazón de los sistemas distribuidos. En este pequeño tutorial se mostrará como funcionan en Erlang y sus limitaciones.

-   [07-detector.pdf](./labs/07-detector.pdf)

## Casty (Opcional)

En esta tarea construiremos una red de media streaming. Jugaremos con streams de _shoutcast_ y construiremos proxies, distributors y clientes peer-to-peer. Usaremos la __bit-syntax__ de Erlang para implementar el protocolo de comunicación sobre HTTP. El parser será implementado usando funciones de alto orden para esconder la interfaz de sockets. Aprenderemos como decodificar un stream de audio mp3 y ponerlo disponible para la conexión de reproductores de audio.

-   [08-casty.pdf](./08-casty.pdf)

## Loggy: un time logger lógico [x]

En este ejercicio vamos a aprender a usar tiempo lógico de forma práctica. La tarea es implementar un sistema de logging que reciva eventos de log de un conjunto de workers. Los eventos estarán tageados con un timestamp de Lamport del worker y deben ser ordenados antes de ser mostrados en pantalla (stdout). Es un poco más complicado de lo que uno podría pesar en primer lugar.

-   [09-loggy.pdf](./09-loggy.pdf)

## Goldy: un juego distribuido (Opcional)

Este curso sirve a 2 propósitos; aprender a programar aplicaciones distribuidas en Erlang y entender por qué las aplicaciones distribuidas no son tan fáciles de controlar como podría pensarse en primer lugar.

-   [10-goldy.pdf](./10-goldy.pdf)

## Toty (Opcional)

La tarea es implementar un servicio multicast con orden total usando un algoritmo distribuido. El algoritmo es el usado por el sistema __ISIS__ y está basado en pedir propuestas a todos los nodos de un grupo.

-   [11-toty.pdf](./11-toty.pdf)

## Muty (Opcional)

La tarea es implementar un lock que provea exclusión mutua distribuido. El lock va a usar una estrategia de multicast y trabajar en una red asincrónica donde no tenemos acceso a un reloj sincronizado. Vamos a hacer la implementación en 3 versiones: la propensa a deadlock, la unfair y la basada en relojes de Lamport. Antes de empezar deberíamos tener una buena base teórica de multicast y como funcionan los relojes de Lamport.

-   [12-muty.pdf](./12-muty.pdf)

## Groupy: a group membership service [x]

En este proyecto implementaremos un servicio de mebresía de grupo que provee multicast atómico. El objetivo es tener varias capas de aplicación con un estado coordinado, p. ej. todas deben ejecutar la misma secuencia de cambios de estado. Un nodo que desea hacer un cambio de su estado interno debe primero hacer multicast del cambio de forma tal que todos los nodos del grupo ejecuten el mismo cambio.
Dado que la capa de multicast provee orden total, todos los nodos van a estar sincronizados.

-   [13-groupy.pdf](./13-groupy.pdf)

## Snapy: the search for dead marbles (Opcional)

In this exercise you will learn how to implement a snap-shot algorithm. We will use a very simple scenario with a set of workers that create and share _marbles_ with each other. The problem is to find out which marbles are alive so that references to dead marbles can be removed. It's in a sense a simplified garbage collection problem. The problem is simplified by the fact that the data structures, the marbles, are atomic and that we do not create duplicates of marbles. We could have solved the problem using a simpler solution but why not
play around with a snap-shot algorithm.

-   [14-snapy.pdf](./14-snapy.pdf)

## Garby: a distributed grabage collector (Opcional)

In this exercise you will learn how to implement a snap-shot algorithm. As an example we will try to detect garbage in a distributed computing. This is tricky and as you will see, a quite expensive operation. Not taking the snap-shot in itself but how to interpret the snap-shot and how to make the most use of the gained information.

-   [15-garby.pdf](./15-garby.pdf)

## Opty: optimistic concurrency control [x]

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


## Slides

- Curso: [00-sistemas_distribuidos](./slides/00-sistemas_distribuidos.pdf)
- Intro a Erlang: [01-intro_erlang](./slides/01-intro_erlang.pdf)
