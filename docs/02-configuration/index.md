---
title: Configuration
has_children: true
nav_order: 2
---

# Configuration
Traditional applications were usually packaged as a bundle, including the
source code and a series of configuration files containing data for different environments, with the appropriate configuration being selected through a flag at runtime. The implication was that you had to make a new application build every time
you needed to update the configuration data for a specific environment. A variant of this process was to create a different build for each environment, meaning that you
had no guarantee whether what you ran in a staging environment would work the
same way in production because they were different artifacts.

Configuration is defined as everything likely to change between deployments (as per the 15-Factor methodology), like credentials, resource handles, and URLs to backing services. An application deployed in multiple locations will likely have different needs in each location and require different configurations. A key aspect of cloud native applications is that the application artifact will stay immutable across environments. No matter which environment you deploy it to, the application build will not be changed.

Each release you deploy is a combination of build and configuration. The same
build can be deployed to different environments with different configuration data.
![Each release you deploy is a combination of build and configuration, which is different for each environment](image-1.png)

Anything that might need to change across deployments should be configurable. For
example, you’ll probably want to change feature flags, credentials for accessing back-
ing services, resource handles for databases, or URLs to external APIs, all depending
on the environment to which you’re deploying the application. Cloud native applications favor externalized configuration so that you can replace it without having to
rebuild your code.

Unlike a monolithic app in which everything runs within a single instance, a cloud-native application consists of independent services distributed across virtual machines, containers, and geographic regions. Managing configuration settings for dozens of interdependent services can be challenging. Duplicate copies of configuration settings across different locations are error prone and difficult to manage. Centralized configuration is a critical requirement for distributed cloud-native applications.

the Twelve-Factor App recommendations require strict separation between code and configuration. Configuration must be stored externally from the application and read-in as needed. Storing configuration values as constants or literal values in code is a violation. The same configuration values are often be used by many services in the same application. Additionally, we must support the same values across multiple environments, such as dev, testing, and production. The best practice is store them in a centralized configuration store.

all your microservices could have a lot of common configuration values per environment.A better approach is to put this configuration in a common place in your system and make the applications sync its contents before they start. Then, you keep a centralized configuration per environment, so you need to adjust the values only once. this is a well-known pattern, known as externalized
(or centralized) configuration, so there are out-of-the-box solutions to build a centralized configuration server.
![Centralized configuration: overview](image.png)

The idea of centralized configuration is built around two main components:
* A data store for configuration data, providing persistence, versioning, and pos-
sibly access control
* A server sitting on top of the data store to manage configuration data and serve
it to multiple applications

No matter how the configuration data is stored(i.e Git repository for storing non-sensitive data, HashiCorp Vault to store your secrets), a configuration server will deliver it to different applications through a unified interface.

![A centralized configuration server manages external properties for many applications across all environments.](image-2.png)

the configuration server becomes a backing service
for all the applications, which means it’s at risk of being a single point of failure. If it’s
suddenly unavailable, all the applications will probably fail to start up. This risk can be
easily mitigated by scaling the config server, as you would with other applications
requiring high availability. When using a configuration server, it’s fundamental to
deploy at least two replicas.

The three main strategies for defining configuration data for cloud native applications are:
<table>
<tr>
<td>Configuration strategy</td>
<td>Characteristics</td>
</tr>
<tr>
<td>Property files packaged with the application</td>
<td>

* These files can act as specifications of what configuration data the applica-
tion supports.
* These are useful for defining sensible default values, mainly oriented to 
the development environment.

</td>
</tr>
<tr>
<td>Environment variables</td>
<td>

* Environment variables are supported by any operating system, so they are 
great for portability.
* Most programming languages allow you access to the environment vari-
ables. In Java you can access them with the System.getenv() method. 
In Spring you can also rely on the Environment abstraction.
* These are useful for defining configuration data that depends on the infra-
structure and platform where the application is deployed, such as active 
profiles, hostnames, service names, and port numbers.
</td>
</tr>
<tr>
<td>Configuration service</td>
<td>

* Provides configuration data persistence, auditing, and accountability.
* Allows secrets management by using encryption or dedicated secret vaults.
* This is useful for defining configuration data specific to the application, such 
as connection pools, credentials, feature flags, thread pools, and URLs to 
third-party services.
</td>
</tr>
</table>

A configuration server handles aspects like secret encryption, configuration
traceability, versioning, and context refreshing at runtime with no restart.

## Samples
* [Multiplication Microservices Example](https://github.com/books-java/Learn-Microservices-with-Spring-Boot-3)