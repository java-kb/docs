---
title: Spring AMQP
has_children: true
nav_order: 1
---

# Spring AMQP
Spring AMQP module contains two dependencies: 
* spring-rabbit, a set of utils to work with a RabbitMQ broker.
* spring-amqp, which includes all the AMQP abstractions, so that you can make your implementation vendor-independent.
* Currently, 
Spring Boot provides a starter for AMQP with extra utilities such as autoconfiguration: spring-boot-starter-amqp. This starter uses both dependencies described earlier, so it implicitly assumes that you’ll use a RabbitMQ 
broker (since it’s the only implementation available).
