---
title: Microservices
parent: System Design
nav_order: 4
---

# Microservices
Microservices derive from SOA, but SOA is different from microservices.
This architecture involves fragmenting the application into small, autonomous services that communicate 
via APIs. It provides scalability, flexibility, and simplified maintenance, but introduces challenges in 
handling distributed systems complexities.

You can’t have ACID guarantees across microservices because you can’t achieve real transactions in a microservices architecture. They are deployed independently, so they live in different processes, and their databases should also be decoupled. Besides, to avoid interdependencies, we also concluded that you should accept eventual 
consistency.
Atomicity, or ensuring that either all related data is stored or nothing is, is hard to achieve across microservices
Modular monolithic application
If your project’s requirements are not compatible with eventual consistency across domains, a modular monolithic application might suit you better.
