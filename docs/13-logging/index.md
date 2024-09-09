---
title: Logging
has_children: true
nav_order: 13
---

# Logging
To properly maintain a distributed system like your microservice architecture, 
you need a central place where you can access all the aggregated logs and search across them.

Basically, the idea is to send all the log outputs from your applications to another 
component in your system, which will consume them and put them all together. Besides, 
you want to persist these logs for some time, so this component should have data 
storage. Ideally, you should be able to navigate through these logs, search, and filter out 
messages per microservice, instance, class, and so on. To do this, many of these tools 
offer a user interface that connects to the aggregated logs storage

A common best practice when implementing the centralized logging approach is 
to keep the application logic unaware of this pattern. The services should just output 
messages using a common interface (e.g., a Logger in Java). The logging agent that 
channels these logs to the central aggregator works independently, capturing the output 
that the application produces.