---
title: Cloud Native Development
parent: Cloud Native
nav_order: 6
---

> TODO Add doc from https://12factor.net/
# Cloud Native Development
# 12 Factors 
the 12 defines best practices for building web applications with the following characteristics:
* Suitable to be deployed on cloud platforms
* Scalable by design
* Portable across systems
* Enablers of continuous deployment and agility

## 1 One codebase, one application
The 15-Factor methodology establishes a one-to-one mapping between an application
and its codebase, so there’s one codebase for each application. Any shared code
should be tracked in its own codebase as a library that can be included as a dependency or service that can be run in standalone mode, acting as a backing service for
other applications. Each codebase can optionally be tracked in its own repository.
 
 A deployment is a running instance of the application. Many deployments are possible in different environments, all sharing the same application artifact. There is no
need to rebuild the codebase to deploy an application to a specific environment: any
aspect that changes between deployments (such as configuration) should be outside
the application codebase. 
## 2 API first
A cloud native system is usually made up of different services that communicate
through APIs. Using an API first approach while designing a cloud native application encourages you to think about fitting it into a distributed system and favors the
distribution of the work across different teams. By designing the API first, another
team using that application as a backing service could create their solution against
that API. By designing the contract up front, integration with other systems will be
more robust and testable as part of the deployment pipeline. Internally, the API
implementation can be changed without affecting other applications (and teams)
depending on it. 
## 3 Dependency management
All application dependencies should be declared explicitly in a manifest and be available for the dependency manager to download from a central repository. In the context of Java applications, we are usually well-equipped to follow this principle using
tools like Maven or Gradle. The only implicit dependencies an application can have
on the surrounding environment are the language runtime and the dependency manager tool. This means that private dependencies should be resolved via the dependency manager. 
## 4 Design, build, release, run
A codebase goes through different stages in its journey from design to deployment in
production:
* Design stage—Technologies, dependencies, and tools needed by a specific application feature are decided.
* Build stage—The codebase is compiled and packaged together with its dependencies as an immutable artifact called a build. The build artifact must be uniquely
identified.
* Release stage—The build is combined with a specific configuration for the deployment. Each release is immutable and should be uniquely identifiable, such as by
using semantic versioning (for example, 3.9.4) or a timestamp (for example,
2022-07-07_17:21). Releases should be stored in a central repository for easy
access, like when a rollback to a previous version is required.
* Run stage—The application runs in the execution environment from a specific
release.
The 15-Factor methodology requires a strict separation of these stages and doesn’t
allow changes to the code at runtime, since that would result in a mismatch with the
build stage. The build and the release artifacts should be immutable and labeled with
a unique identifier to guarantee reproducibility. 
## 5 Configuration, credentials, and code
The 15-Factor methodology defines configuration as everything likely to change
between deployments. Whenever you need to change the configuration for an application, you should be able to do so without any changes in the code, and without
building the application again.
 The configuration might include resource handles to backing services like a database or a messaging system, credentials to access third-party APIs, and feature flags.
Ask yourself if any credential or environment-specific information would be compromised should your codebase suddenly become public. That will tell you whether you
have correctly externalized the configuration.
 To be compliant with this factor, the configuration can’t be included in the code or
tracked in the same codebase. The only exception is the default configuration, which
can be packaged with the application codebase. You can still use configuration files for
any other type of configuration, but you should store them in a separate repository.
 The methodology recommends storing configuration as environment variables. By
doing so, you can have the same application deployed in different environments but
with different behaviors depending on the environment’s configuration. 
## 6 Logs
A cloud native application isn’t concerned with routing and storage of logs. Applications should log to the standard output, treating logs as events emitted in a sequence ordered by time. Log storage and rotation are not application responsibilities anymore. An external tool (a log aggregator) will fetch, collect, and make logs available for
inspection.
## 7 Disposability
In a traditional environment, you would take much care of your applications, ensuring they stay up and running and never terminate. In a cloud environment, you don’t
need to care that much: applications are ephemeral. If a failure happens and the
application doesn’t respond anymore, you terminate it and start a new instance. If you
have a high-load peak, you can spin up more instances of your applications to sustain
the increased workload. We say that an application is disposable if it can be started or
stopped at any time.
 To handle application instances in such a dynamic way, you should design them
to start up quickly whenever you need a new instance and gracefully shut down
when you don’t need them anymore. A fast startup enables the elasticity of the system, ensuring robustness and resilience. Without a fast startup, you will have performance and availability issues.
 A graceful shutdown is when an application, on receiving a signal to terminate, stops
accepting new requests, completes the ones already in progress, and finally exits. In
the case of web processes, that is straightforward. In other cases, such as with worker
processes, the jobs they were responsible for must be returned to the work queue, and
only afterward can they exit. 
## 8 Backing services
Backing services can be defined as external resources that an application uses to
deliver its functionality. Examples of backing services are databases, message brokers,
caching systems, SMTP servers, FTP servers, or RESTful web services. Treating them as
attached resources means that you can easily change them without modifying the
application code.
 Consider how you use databases throughout the software development life cycle.
Chances are that you’ll use a different database depending on the stage: development, testing, or production. If you treat the database as an attached resource, you
can use a different service depending on the environment. The attachment is done
through resource binding. For example, resource binding for a database could consist
of a URL, a username, and a password. 
## 9 Environment parity
Environment parity is about keeping all your environments as similar as possible. In
reality, there are three gaps that this factor tries to address:
* Time gap—The period between a code change and its deployment can be
quite large. The methodology strives to promote automation and continuous deployment to reduce the period between when a developer writes code to
when it’s deployed in production.
* People gap—Developers build applications, and operators manage their deployment in production. This gap can be resolved by embracing a DevOps culture,
improving collaboration between developers and operators, and embracing the
“you build it, you run it” philosophy.
* Tools gap—One of the main differences between environments is how backing
services are handled. For example, developers might use the H2 database in
their local environment but PostgreSQL in production. In general, the same
type and version of backing services should be used in all environments. 
## 10 Administrative processes
Some management tasks are usually needed to support applications. Tasks like database migrations, batch jobs, or maintenance jobs should be treated as one-off processes. Just like application processes, the code for administrative tasks should be
tracked in revision control, delivered with the application they support, and executed
in the same environment as the application.
 It’s usually a good idea to frame administrative tasks as small standalone services
that run once and then are thrown away or as functions configured in a stateless platform to be triggered when certain events happen, or you can embed them in the
application itself, activating them by calling a specific endpoint. 
## 11 Port binding
Applications following the 15-Factor methodology should be self-contained and
export their services via port binding. In production, there might be some routing services that translate requests from public endpoints to the internal port-bound services.
 
 An application is self-contained if it doesn’t depend on an external server in the
execution environment. A Java web application would probably run inside a server
container like Tomcat, Jetty, or Undertow. A cloud native application, in contrast,
would not require the environment to have a Tomcat server available; it would manage it itself as any other dependency. Spring Boot, for example, lets you use an
embedded server: the application will contain the server rather than depending on
one being available in the execution environment. One of the consequences of this
approach is that there is always a one-to-one mapping between application and
server, unlike the traditional method where multiple applications are deployed to the
same server.

 The services provided by the application are then exported via port binding. A web
application would bind HTTP services to a specific port and potentially become a
backing service for another application. That’s what usually happens in a cloud native
system. 
## 12 Stateless processes
In the previous chapter, you saw that high scalability is one reason why we move to the
cloud. To ensure scalability, we design applications as stateless processes and adopt
a share-nothing architecture: no state should be shared among different application
instances. Ask yourself if any data would be lost should an instance of your application
be destroyed and recreated. If the answer is affirmative, then your application is not
stateless.
 No matter what, we will always need to save some state, or our applications will be
useless in most cases. As a result, we design applications to be stateless and then only
handle the state in specific stateful services like data stores. In other words, a stateless
application delegates the state management and storage to a backing service. 

> The methodology was revised and expanded by Kevin Hoffman in his book
Beyond the Twelve-Factor App, refreshing the contents of the original factors and adding
three extra ones.

## 13 Concurrency
Creating stateless applications is not enough to ensure scalability. If you need to scale,
that means you need to serve more users. Therefore, your applications should allow
concurrent processing to serve many users at the same time.
 The 15-Factor methodology defines processes as first-class citizens. Those processes
should be horizontally scalable, distributing the workload across many processes on
different machines, and this concurrent processing is only possible if the applications
are stateless. In JVM applications, we handle concurrency through multiple threads,
available from thread pools.
 Processes can be classified according to their types. For example, you might have
web processes that handle HTTP requests and worker processes that execute scheduled jobs in the background. 
## 14 Telemetry
Observability is one of the properties of cloud native applications. Managing a distributed system in the cloud is complex, and the only way to manage such complexity is by
ensuring that every system component provides the correct data to monitor the system’s behavior remotely. Examples of telemetry data are logs, metrics, traces, health
status, and events. Hoffman uses a very catchy image to stress the importance of telemetry: treat your applications like space probes. What kind of telemetry would you need
to monitor and control your applications remotely?
## 15 Authentication and authorization
Security is one of the essential qualities of a software system, but it often doesn’t get
the necessary attention. Following a zero-trust approach, we must secure any interaction
within the system at any architectural and infrastructural levels. There is undoubtedly
more to security than just authentication and authorization, but those are a good
starting point.

 With authentication, we can keep track of who is using the application. Knowing
that, we can then check the user permissions to verify whether the user is allowed to
perform specific actions. A few standards are available for implementing identity and
access management, including OAuth 2.1 and OpenID Connect. 