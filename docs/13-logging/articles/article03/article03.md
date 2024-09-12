---
title: How to choose the right API Gateway
parent: Gateway Articles
nav_order: 3
---
How to choose the right API Gateway
===================================
*Source: https://dev.to/apisix/how-to-choose-the-right-api-gateway-3f9i*

Nowadays an [API Gateway](https://wikitech.wikimedia.org/wiki/API_Gateway) is an essential component in designing a distributed system’s architecture with multiple API services or microservices. This post helps you understand _what’s the API Gateway, when, and why to use it, and guides you on how to choose the best API Gateway_ solution for your applications.

[](#what-is-api-gateway)What is API Gateway?
--------------------------------------------

An **API gateway** is a service that’s the entry point into the application from the outside world. It’s responsible for request routing, API composition, and other functions, such as authentication. Like a [facade](https://en.wikipedia.org/wiki/Facade_pattern), an API gateway encapsulates the application’s internal architecture and provides an API to its clients. All API requests from external clients first go to the API gateway, which routes some requests to the appropriate service whether that be an upstream API server, a third-party application, a database, or even a serverless.

One of the main use cases of API gateways is that they introduce an API-as-a-service abstraction to allow API providers to abstract API implementations and evolve backend architecture without impacting API consumers.

[![What is API Gateway](image.png)

Why use API Gateway?
--------------------------------------------

In today’s world, we usually create multiple microservices for a particular product and the client apps usually need to consume functionality from more than one microservice. And for each of these services, we will have different endpoints accessing these services from the external world it doesn't make sense to expose multiple URLs we should have a single-entry point to all our services, and based on the different paths we should be doing the routing.

[![Why use API Gateway](image-1.png)

As it is shown in the above picture, a client can retrieve the order details from the monolithic online sample shopping web application with a single request. But the client must make multiple requests to retrieve the same information in a microservice architecture. In this design, the mobile application is playing the role of API composer. It invokes multiple services and combines the results. Although this approach seems reasonable, it has several serious problems.

_The first problem_ is poor user experience due to the client making multiple requests to retrieve the data it wants to display to the user. _The second issue_ is that it requires the mobile developer to write potentially complex API composition code. This work is a distraction from their primary task of creating a great user experience. _What is more challenging_ with a mobile application directly calling services is that some services could use protocols that aren’t easily consumed by a client. _Yet another drawback_ of a mobile application directly accessing the services is the lack of encapsulation. As an application evolves, the developers of a service sometimes change an API in a way that breaks existing clients. You can also add API design issues for other kinds of clients to this list.

As you understand, there are numerous drawbacks with services accessing services directly. It’s often not practical for a client to perform API composition over the internet. Therefore, a much better approach is to use **an API gateway**.


[![API Gateway as a single entry point](image-2.png)

[](#why-not-develop-your-own-api-gateway)Why not develop your own API Gateway
-----------------------------------------------------------------------------

Developing an API gateway on your own is _NOT extremely difficult_ if you have enough resources and unlimited time (it will take longer than you expect). It’s basically a web application that proxies requests to other services. You can build one using your favorite web framework with the most important features such as implementing a mechanism for defining routing rules in order to minimize the complex coding or correctly implementing the HTTP proxying behavior, including how HTTP headers are handled and so on. There are, however, many design, security and maintenance problems that you’ll need to solve.

You need to apply proper security concerns (unless you have a staff of security experts on hand), test each new feature, monitor the API Gateway performance, document each change, scale, maintain, and upgrade internal libraries continuously as a part of the development workload.

If you have no special custom needs, it might be easier to use what’s available on the market (especially if you need to use a gateway quickly). As a result, a better starting point for developing an API gateway is to use a ready solution designed for that purpose. Its built-in functionality significantly reduces the amount of code you need to write.

[](#10-top-api-gateways-and-management-tools)10 Top API Gateways and Management Tools
-------------------------------------------------------------------------------------

As there are various types of gateways available, and numerous features are provided by each.

Below, I have shared the **10 top API gateways and API management solutions** (both open-source and SaaS) and note that they are not in the specific order of popularity or use.

1.  [Kong Gateway](https://konghq.com/products/api-gateway-platform).
2.  [Apache APISIX](https://apisix.apache.org/).
3.  [Tyk](https://tyk.io/open-source-api-gateway/).
4.  [KrakenD](https://www.krakend.io/).
5.  [Gravitee.io](https://www.gravitee.io/).
6.  [Apigee](https://cloud.google.com/apigee).
7.  [Amazon API Gateway](https://aws.amazon.com/api-gateway/).
8.  [Azure API Management](https://learn.microsoft.com/en-us/azure/api-management/api-management-key-concepts).
9.  [Ambassador](https://www.getambassador.io/).
10.  [Gloo](https://www.solo.io/products/gloo/).

Let’s have a look at how to choose the right API Gateway in the next section based on best practices.

[](#how-to-select-your-api-gateway)How to select your API Gateway
-----------------------------------------------------------------

Here are some characteristics to consider when you choose **an API Gateway or API Management solution** that perfectly fits your need. Note that the following list of attributes is not organized in order of priority:

1.  Primary edge functionalities.
2.  Security.
3.  Simple Logging.
4.  Installation and deployment Options.
5.  Self-hosted vs Cloud-hosted.
6.  Customization.
7.  Integration.
8.  Performance.
9.  Features.
10.  Community.
11.  Price.

Now we can break down each attribute and understand why we should consider each.

### [](#primary-edge-functionalities)Primary edge functionalities.

Although an API gateway’s primary responsibilities are API routing and composition, it should also implement what are known as edge functions. An _edge function_ is, as the name suggests, a request-processing function implemented at the edge of an application. Examples of edge functions that an application might implement include the following:

*   _Authentication_ — Verifying the identity of the client making the request.
*   _Authorization_ — Verifying that the client is authorized to perform that particular operation.
*   _Rate limiting_ — Limiting how many requests per second from either a specific client and/or from all clients.
*   _Caching_ — Cache responses to reduce the number of requests made to the services.
*   _Metrics collection_ — Collect metrics on API usage for billing analytics purposes.
*   _Request logging_ — Log requests.
*   _Payload transformation_ — An API Gateway should be able to provide the capabilities to modify requests/response payloads. An API gateway might also perform protocol translation. It might provide a RESTful API to external clients, even though the application services use a mixture of protocols internally, including REST and gRPC.

You need to make sure that above mentioned basic _cross-cutting concerns_ are supported out of the box by chosen API Gateway.

### [](#security)Security

API Gateway is yet another highly available component that must be developed, deployed, and managed. There’s also a risk that the API gateway becomes _a security bottleneck_. Before choosing it, you need to be sure of its security. It should have policies that make using [SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security) (Secure Sockets Layer) obligatory and compliant with some data protection regulations. Also, you need to verify if the tool has strong authentication enabled when you interact with the admin Logging.

Because the Logging is a highly critical feature, we need to authenticate via an API key or by means of other auth methods. For example, most API Gateway providers such as [Apache APISIX](https://apisix.apache.org/) enabled token-based access to [Admin API](https://apisix.apache.org/docs/apisix/admin-api/#:~:text=Note%3A%20Mentions%20of%20X%2DAPI%2DKEY%20in%20this%20document%20refers%20to%20deployment.admin.admin_key.key%E2%80%94the%20access%20token%20for%20Admin%20API%E2%80%94in%20your%20Logging%20file.) and they highly advise generating your own token and regularly changing it. Or [Azure API Management](https://azure.microsoft.com/en-us/products/api-management/) relies on [Azure Active Directory](https://azure.microsoft.com/en-us/products/active-directory/) (Azure AD), which includes optional features such as [multifactor authentication](https://support.microsoft.com/en-us/topic/what-is-multifactor-authentication-e5e39437-121c-be60-d123-eda06bddf661) (MFA), and [Azure RBAC](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview) to enable fine-grained access to the API Management service and its entities including APIs and policies.

[](#simple-Logging)Simple Logging
---------------------------------------------

It’s important that the process for _configuring the API gateway_ be as lightweight as possible. Otherwise, developers will be forced to wait in line in order to configure the gateway. The Logging required for routing can become complex when the number of microservices and their API scope increases. Make sure that how fast updates on the API Gateway Logging get affected without any downtime when you add/remove routes and upstream services. For example, [APISIX plugins](https://apisix.apache.org/plugins/) support hot reloading means that you do not have to restart the running service by calling a special HTTP interface.

Check what Logging language (`JSON/Yaml`) and style (`Declarative/Imperative`) chosen API Gateway support. It is not so crucial but sometimes you might ask: Does it have a user-friendly GUI and drag&drop easy config option? Some open-source projects like [Tyk](https://tyk.io/), [Krakend.io](https://www.krakend.io/), and [Apache APISIX](https://apisix.apache.org/docs/dashboard/USER_GUIDE/) have built-in no-code possibly visual editing dashboards. You can even import all your APIs descriptions from a `JSON`.

[](#installation-and-deployment-options)Installation and deployment Options
---------------------------------------------------------------------------

Another point to consider is how difficult is it to install the API Gateway or redeploy the gateway when changes are made. Check what installation options are offered. Most modern API Gateways can be installed in many different ways(Package based, [Docker](https://www.docker.com/), [Helm](https://helm.sh/), [RPM](https://rpm.org/)) in any environment (Linux, Windows, macOS). For example, one of the biggest advantages of [Kong](https://konghq.com/) is its wide range of installation choices, with pre-made containers such as Docker and [Vagrant](https://www.vagrantup.com/) so you can get a deployment running quickly.

Next, review deployment complexity such as DB-less versus database-backed deployments. For example, [Kong](https://konghq.com/) does require running [Cassandra](https://cassandra.apache.org/_/index.html) or [Postgres](https://www.postgresql.org/). [Apigee](https://cloud.google.com/apigee) requires Cassandra, [Zookeeper](https://zookeeper.apache.org/), and Postgres to run, while other solutions like [Express Gateway](https://www.express-gateway.io/) and [Tyk](https://tyk.io/) only require [Redis](https://redis.io/). [Apache APISIX](https://apisix.apache.org/) uses [etcd](https://etcd.io/) as its data store, it stores and manages routing-related and plugin-related Loggings in etcd in the [Data Plane](https://apisix.apache.org/docs/apisix/architecture-design/apisix/).

### [](#selfhosted-vs-cloudhosted)Self-hosted vs Cloud-hosted

When you choose an API Gateway, you need to take into consideration hosting options for your API Gateway service like [on-premise](https://en.wikipedia.org/wiki/On-premises_software), [SaaS](https://en.wikipedia.org/wiki/Software_as_a_service) (Software As Service), or a hybrid gateway deployment. All SaaS offerings for API platforms include an embedded API gateway capability and most people just use it that way. Because they get the benefits of a SaaS environment (Availability guarantees, automatic scaling, and operational security provided) and it is easy to integrate with the cloud provider's other services.

Here is a list of some popular API Management solutions in the cloud:

*   [AWS API Gateway](https://aws.amazon.com/api-gateway/)
*   [Google Cloud API Gateway](https://cloud.google.com/api-gateway)
*   [Azure API Management](https://azure.microsoft.com/en-us/services/api-management/)
*   [IBM API Connect](https://www.ibm.com/cloud/api-connect)

However, it may be more difficult to integrate with third-party services if it is running in the cloud provider that you use and the greater control that comes with running API Gateway on-premise or there is also another choice of deploying a specific open-source or enterprise API Gateway to the cloud provider where your other applications (Web or API services) are running.

For example, it is very straightforward to deploy Kong or Apache APISIX instance to any cloud of your choice as you can still host it let’s say on [Microsoft Azure](https://azure.microsoft.com/en-us/) or [AWS](https://aws.amazon.com/), and use features of the free open-source projects instead of spending additional cost for their build-in API Management tool. On the other hand, [Tyk](https://tyk.io/), [APiGee](https://cloud.google.com/apigee), or [API7](//API7.ai) offer both cloud-hosted SaaS and on-premise deployment solutions.

### [](#customization)Customization

In addition to deployment requirements, API gateways also have requirements for customization. So, another factor to look at is how chosen API Gateway makes custom development easier when you can not use the API Gateway directly to satisfy your need. Sometimes you need to implement new custom plugins to extend the gateway with additional functionality if your system’s technical requirements are currently not supported by built-in plugins.

Kong offers an open-sourced [Plugin Developer Kit](https://docs.konghq.com/gateway/latest/plugin-development/) (or “PDK”) in various languages. You can build a Kong plugin with [Go](https://go.dev/), [Javascript](https://www.javascript.com/), [Python](https://www.python.org/), and [Lua](https://www.lua.org/). In Apache APISIX, you can use different [Plugin Runners](https://apisix.apache.org/) to develop plugins using the programming languages you are familiar with. They also embedded [Wasm](https://webassembly.org/) into APISIX, and you can utilize Wasm to compile Wasm bytecode to run in APISIX.

### [](#integration)Integration

Next characteristic of a good API Gateway is effortless integration with more ecosystems. You need to check if it is integrated with other products, tools, platforms, and services. For example, you can investigate if supports several application protocols, and compatibility with third-party identity providers for authentication, and if it provides pre-built connectors that you can easily integrate with Most observability platforms like ([Prometheus](https://prometheus.io/), [Skywalking](https://skywalking.apache.org/), [ElasticSearch](https://www.elastic.co/), [Opentelemetry](https://opentelemetry.io/), and so on).

### [](#performance)Performance

Speed – it’s key in today’s digital landscape, where consumers can easily switch to a competitor if your app’s performance is too slow. An API gateway is the application’s front door and all external requests must first pass through the gateway which means it should be fast enough to respond quickly to these requests from the external world. But not all API gateways perform at the same level. If your application requires to be fast and responsive in real-time, you need to review the performance benchmark of each API Gateway provider.

Although most companies don’t operate at a large scale that handles billions of requests per day, the performance and scalability of the API gateway are usually very important. For example, Apache APISIX Gateway uses radix tree-route-matching and etcd under the hood to provide you the ability to create high-speed synchronized systems.

As well as being scalable, an API gateway must also be reliable. One way to achieve reliability is to run multiple instances of the gateway behind a load balancer. If one instance fails, the load balancer will route requests to the other instances. Some API Management solutions from cloud vendors provide auto-scaling out of the box and no need to integrate with Services that provide this capability.

### [](#features)Features

Every API Gateway has various features that sometimes differ from each other. The feature can be limited depending on the open-source or enterprise edition of your choice and some plugins/extensions are available for free. During the investigation, you may know that some paid plugins or functionalities from the enterprise can be found in the most widely open-source project without any cost.

[IBM API Connect](https://www.ibm.com/products/api-connect) provides automated, model-driven tools for API creation and analytics on API usage that can be available to API providers as well as consumers. Kong out of the box provides many expected features of API Management with enterprise plugins, a developer portal, an analytics platform, security features, enhanced performance, GUIs, 24/7 support, and more.

### [](#community)Community

In case chosen API Gateway extends the open-source gateway and you need to carefully analyze if it has a license file, they have an active community, look for the number of contributors, who are the community users, how often people make commits and they release the new versions, well-written documentation, and answered questions on forums.

### [](#price)Price

Last but not least, one of the important aspects can be the cost of the usage of API management solution. If it is a 100% production-ready open-source version already practiced by many companies, you can opt for it. In the case of the enterprise edition, check if they have a suitable free tier to experiment with features before you pay and does the company have the full support that you require. Some open-source API Gateway providers (Such as [Tyk](https://tyk.io/) or [API7.ai](https://api7.ai/) which is built on the top of Apache APISIX) deliver the same set of functionalities whether you are a Community Edition user or an enterprise user, you get the same API Gateway.

[](#conclusion)Conclusion
-------------------------

API gateways are essential parts of modern cloud-native microservices APIs architectures. However, choosing the proper API gateway solution is not so straightforward. You can find many open-source and enterprise tools on the market both on-premise and SaaS. There's no one-size-fits-all solution, and the correct choice depends on many aspects as listed above, and also each organization's unique needs.