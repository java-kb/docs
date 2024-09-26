---
title: Tracing
has_children: true
nav_order: 15
---

# Tracing
In this pattern we record information (e.g. start time, end time) about the work (e.g. service requests) performed when handling the external request in a centralized service. This can be done by:
* Assigns each external request a unique external request id.
* Pass this external request id to all services that are involved in handling the request.
* Include the external request id while logging.
* Records information (e.g. start time, end time) about the requests and operations performed when handling a external request in a centralized service.

This instrumentation might be part of the functionality provided by a Microservice Chassis framework.

The drawback is aggregating and storing traces can require significant infrastructure.