---
title: Architecture
parent: System Design
nav_order: 1
---

# Architecture
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Monolithic

## Microservices
You can’t have ACID guarantees across microservices because you can’t achieve real transactions in a microservices architecture. They are deployed independently, so they live in different processes, and their databases should also be decoupled. Besides, to avoid interdependencies, we also concluded that you should accept eventual 
consistency.
Atomicity, or ensuring that either all related data is stored or nothing is, is hard to achieve across microservices
Modular monolithic application
If your project’s requirements are not compatible with eventual consistency across domains, a modular monolithic application might suit you better.


