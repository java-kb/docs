---
title: Load Balancing
has_children: true
nav_order: 8
---

# Load Balancing
To make load balancing work properly, you need some prerequisites.
* The gateway needs to know the available instances for a given service. The initial configuration points directly to a specific port 
because you assumed that there is only one instance. What would that look like with multiple replicas? You shouldn’t include a 
hard-coded list in your routing configuration since the number of instances should be dynamic: you want to bring new ones up and down transparently.
* You need to implement the concept of healthiness of a backend component. Only then will you know when an instance is not ready 
to handle traffic and switch to any other healthy instance.
