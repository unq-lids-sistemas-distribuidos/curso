# Sistemas Distribuidos (en Erlang)

Este curso está basado en el excelente material de **Johan Montelius**  (https://people.kth.se/~johanmon/dse.html).

Estos son una serie de trabajos usados en diversos cursos en Sistemas Distribuidos. Los mismos fueron usados para ejemplificar diferentes sistemas, algoritmos o aspectos como performance y fault tolerance.

La modalidad del curso será la de taller y durante el recorrido del curso los alumnos irán estudiando los diversos aspectos de los sistemas distribuidos a medida que resuelven los problemas que se van presentando y experimentan en el laboratorio. Una vez finalizado el trabajo se pide a los alumnos que escriban un reporte para ser discutido en clase sobre los hallazgos, problemas que se presentaron y posibles extensiones.

Los trabajos asumen cierto connocimiento básico de Erlang, pero se ha limitado el uso a un conjunto de funcionalidades básicas. Se omitió el uso de OTP, dado que se piensa que esconde la complejidad subyacente de muchos de los trabajos. Tampoco que usan librerías que manejan comunicación de grupos o registro global. EL objetivo es que los alumnos desarrollen las soluciones a estos problemas entendiendo mejor los pros y contras de las diferentes estrategias. Sin embargo, se recomienda a aquellos interesados al promediar el curso o posterior al mismo aparender los servicios y beneficios de OTP, base fundamental del desarrollo de sistemas altamente escalables y tolerantes a falla en Erlang.

Los trabajos están licenciados bajo Creative Commons Attribution.

## Una Introducción a Erlang [x]

Esto no es un curso rápido de Erlang dado que hay muchos tutoriales disponibles en la web. Sin embargo en se describirán las herramientas que se necesitan para tener un ambiente andando. Se da por sentado que tienen una cierta experiencia en lenguajes de programación y programación funcional y particularmente recursión.

-   [01-crash](./labs/01-crash.pdf)

## El Conjunto de  Mandelbrot (Opcional)

Calcular un conjunto de Mandelbrot es una tarea que puede ser hecha en paralelo si se tienen varios cores o varias máquinas. La implementación brindada no es la más rápida pero sirve con el propósito de ser una tarea para comenzar; puede ser facilmente mejorarda.

-   [02-mandel](./labs/02-mandel.pdf)

## Primy: encontrando números primos grandes (Opcional)

En esta tarea hay que implementar un sistema distribuido que encuentre números primos grandes. El sistema debe tener un server que se encarga de controlar el cálculo y un conjunto dinámico de workers a los que se asigna testear si un número dado es primo o no.

-   [03-primy](./labs/03-primy.pdf)

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

-   [06-routy.pdf](./labs/06-routy.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 3: Networking and Internetworking.

## Detector [x]

Los detectores de fallas son el corazón de los sistemas distribuidos. En este pequeño tutorial se mostrará como funcionan en Erlang y sus limitaciones.

-   [07-detector.pdf](./labs/07-detector.pdf)

## Casty (Opcional)

En esta tarea construiremos una red de media streaming. Jugaremos con streams de _shoutcast_ y construiremos proxies, distributors y clientes peer-to-peer. Usaremos la __bit-syntax__ de Erlang para implementar el protocolo de comunicación sobre HTTP. El parser será implementado usando funciones de alto orden para esconder la interfaz de sockets. Aprenderemos como decodificar un stream de audio mp3 y ponerlo disponible para la conexión de reproductores de audio.

-   [08-casty.pdf](./labs/08-casty.pdf)

## Loggy: un time logger lógico [x]

En este ejercicio vamos a aprender a usar tiempo lógico de forma práctica. La tarea es implementar un sistema de logging que reciva eventos de log de un conjunto de workers. Los eventos estarán tageados con un timestamp de Lamport del worker y deben ser ordenados antes de ser mostrados en pantalla (stdout). Es un poco más complicado de lo que uno podría pesar en primer lugar.

-   [09-loggy.pdf](./labs/09-loggy.pdf)

__Ref:__

-   Distributed Systems and Concepts - Section 14.4 Logical time and logical clocks.

## Goldy: un juego distribuido (Opcional)

Este curso sirve a 2 propósitos; aprender a programar aplicaciones distribuidas en Erlang y entender por qué las aplicaciones distribuidas no son tan fáciles de controlar como podría pensarse en primer lugar.

-   [10-goldy.pdf](./labs/10-goldy.pdf)

## Toty (Opcional)

La tarea es implementar un servicio multicast con orden total usando un algoritmo distribuido. El algoritmo es el usado por el sistema __ISIS__ y está basado en pedir propuestas a todos los nodos de un grupo.

-   [11-toty.pdf](./labs/11-toty.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 6.2 Group communication.
  - Distributed Systems and Concepts - Chapter 18.2 System model and the role of group communication.

## Muty (Opcional)

La tarea es implementar un lock que provea exclusión mutua distribuido. El lock va a usar una estrategia de multicast y trabajar en una red asincrónica donde no tenemos acceso a un reloj sincronizado. Vamos a hacer la implementación en 3 versiones: la propensa a deadlock, la unfair y la basada en relojes de Lamport. Antes de empezar deberíamos tener una buena base teórica de multicast y como funcionan los relojes de Lamport.

-   [12-muty.pdf](./labs/12-muty.pdf)

## Groupy: un servicio de membresía de grupo [x]

En este proyecto implementaremos un servicio de mebresía de grupo que provee multicast atómico. El objetivo es tener varias capas de aplicación con un estado coordinado, p. ej. todas deben ejecutar la misma secuencia de cambios de estado. Un nodo que desea hacer un cambio de su estado interno debe primero hacer multicast del cambio de forma tal que todos los nodos del grupo ejecuten el mismo cambio.
Dado que la capa de multicast provee orden total, todos los nodos van a estar sincronizados.

-   [13-groupy.pdf](./labs/13-groupy.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 6.2 Group communication.
  - (Algoritmo ISIS) Distributed Systems and Concepts - Chapter 15.4 Coordination and agreement in group communication 
  - Distributed Systems and Concepts - Chapter 18.2 System model and the role of group communication.

## Snapy: la búsqueda de las __bolitas__ muertas (Opcional)

En este ejercicio vamos a aprender a implementar un algoritmo de snapshot. Vamos a usar un escenario muy simple con un conjunto de workers que crean y comparten _bolitas_ entre si. EL problema es encontrar cuales bolitas están vivas así las referencias a las bolitas muertas pueden ser removidas. En cierto sentido es un problema de garbage collection simplificado. El problema está simplificado por el hecho de que la estructura de datos de las bolitas, son atómicos y que no podemos crear bolitas duplicadas. Podemos entonces resolver el problema usando una solución más simple, pero por que no jugar con un algoritmo de snapshot.

-   [14-snapy.pdf](./labs/14-snapy.pdf)

## Garby: un garbage collector distribuido (Opcional)

En este ejercicio vamos a aprender como imlementar un algoritmo de snapshot. Vamos a tratar de detectar garbage en un sistema distribuido. Vamos a ver que complejo y que además es una operación bastante costosa. No vamos a hablar de snapshots en si mismo sino como interpretar el snapshot y como hacer el mejor uso de la información recolectada.

-   [15-garby.pdf](./labs/15-garby.pdf)

## Opty: control de concurrencia optimista [x]

En esta sesión vamos a implementar un servidor de transacciones usando control de concurrencia optimista. Vamos aprender además como implementar una estructura actualizable en Erlang que puede ser accedida por procesos, posiblemente distribuidos. Antes de empezar cada uno debería conocer como funciona el control de concurrencia con validación backwards.

-   [16-opty.pdf](./labs/16-opty.pdf)

__Ref__:

  - Distributed Systems and Concepts - Chapter 16 Transactions and Concurrency Control.

## Timey: control de concurrencia basado en tiempo (Opcional)

En esta sesión vamos a implementar un servidor de transacciones usando control de concurrencia basada en tiempo. Vamos aprender además como implementar una estructura actualizable en Erlang que puede ser accedida por procesos, posiblemente distribuidos. Antes de empezar cada uno debería conocer como funciona el control de concurrencia basado en tiempo.

-   [17-timey.pdf](./labs/17-timey.pdf)

## Paxy: el protocolo Paxos (Opcional)

Este ejercicio nos va a dar la oportunidad de aprender el algoritmo de Paxos para establecer consenso en un sistema distribuido. Cada uno debería conocer las operaciones básicas del algortimo pero no todos los detalles, ya que ese es el propósito del ejercicio.

-   [18-paxy.pdf](./labs/18-paxy.pdf)

## Chordy: una tabla hash distribuida (Opcional)

En este ejercicio vamos a implementar una tabla hash distribuida siguiendo el esquema Chord. Para entender lo que estamos a punto de hacer cada uno debe tener un conocimiento básico de Chord y preferentemente leer el paper original.

-   [19-chordy.pdf](./labs/19-chordy.pdf)

## Slides

- Curso: [00-sistemas_distribuidos](./slides/00-sistemas_distribuidos.pdf)
- Intro a Erlang: [01-intro_erlang](./slides/01-intro_erlang.pdf)
