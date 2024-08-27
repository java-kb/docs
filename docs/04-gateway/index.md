---
title: Gateway
has_children: true
nav_order: 4
---

# Gateway
The Gateway pattern helps abstracting the internal architecture from the outside by routing external requests to the corresponding microservice.
The gateway pattern centralizes the HTTP access and takes care of proxying
requests to other underlying services. Usually, the gateway decides where to route a request
based on some configured rules (aka, predicates). Additionally, this routing service can
modify requests and responses as they pass through, with pieces of logic that are called
filters.

Also, if you add user authentication to your system, you would be required to validate the security credentials in every backend microservice, which can be cumbersome. A more sensible approach is to place this logic at the edge of your backend, validating API calls and forwarding simple requests to other microservices. As long as you ensure the rest of the backend services are not externally reachable, you don’t need to worry about security concerns.

## Servers
### Spring Cloud Gateway
For the gateway pattern, Spring Cloud offers two options
* Spring Cloud Netflix(In maintenance mode)
* Spring Cloud Gateway

### Nginx
A powerful and lightweight web server, reverse proxy, and load balancer. Its high performance
and low resource usage makes it an excellent choice as a reverse proxy in front of microservices for load balancing, SSL termination,caching and serving static content.

### HAProxy 
is an open-source loadbalancer and proxy server that provides high availability for TCP-and HTTP-based applications. It also improves the performance
and reliability of applications by distributing network traffic acrossmany servers.

### Kong Gateway
is a lightweight, cloudnative, fast, and flexible distributed API gateway. It is built on the NGINX platform, and you can extend it through modules and
plugins to deliver advanced features like advanced security, traffic management, observability, and administration. It is available in both open-source and enterprise versions to cater to the different needs of small to large organizations.
