---
title: Spring Cloud Config Server
parent: Configuration Servers
nav_order: 1
---

# Spring Cloud Config Server
With system environment variables, you can externalize your application’s configuration and follow the 15-Factor methodology. However, there are some issues they cannot handle:
* Configuration data is as important as the application code, so it should be han-
dled with the same care and attention, starting from its persistence. Where
should you store configuration data?
* Environment variables don’t provide granular access control features. How can
you control access to configuration data?
* Configuration data will evolve and require changes, just like application code.
How should you keep track of the revisions to configuration data? How should
you audit the configuration used in a release?
* After changing your configuration data, how can you make your application
read it at runtime without requiring a full restart?
* When the number of application instances increases, it can be challenging to
handle configuration in a distributed fashion for each instance. How can you
overcome such challenges?
* Neither Spring Boot properties nor environment variables support configuration
encryption, so you can’t safely store passwords. How should you manage secrets?

The Spring ecosystem offers many options to address those issues. We can categorize
them into three groups.
* **Configuration services**—The Spring Cloud project provides modules you can
use to run your own configuration services and configure your Spring Boot
applications.
  * **Spring Cloud Alibaba** provides a configuration service using Alibaba Nacos
as the data store.
  * **Spring Cloud Config** provides a configuration service backed by a pluggable
data source, such as a Git repository, a data store, or HashiCorp Vault.
  * **Spring Cloud Consul** provides a configuration service using HashiCorp Con-
sul as the data store.
  * **Spring Cloud Vault** provides a configuration service using HashiCorp Vault
as the data store.
  * **Spring Cloud Zookeeper** provides a configuration service using Apache Zoo-
keeper as the data store.
* **Cloud vendor services**—If you run your applications on a platform provided by a
cloud vendor, you might consider using one of their configuration services.
Spring Cloud provides integration with the main cloud vendor configuration
services that you can use to configure your Spring Boot applications.
  * **Spring Cloud AWS** provides integration with AWS Parameter Store and AWS
Secrets Manager.
  * **Spring Cloud Azure** provides integration with Azure Key Vault.
  * **Spring Cloud GCP** provides integration with GCP Secret Manager.
* **Cloud platform services**—When running your applications on a Kubernetes platform, you can seamlessly use **ConfigMaps** and Secrets to configure Spring Boot.

The configuration server pattern for Spring is the Spring Cloud Config Server project. This is a native implementation included in the Spring Cloud family, which allows you to keep a set of configuration files distributed in folders and exposed via a REST API

On the client side, the projects using this dependency access the config server and request the corresponding configuration resources, depending on their active profiles. The only drawback of this solution is that you need to create another microservice to act as the configuration server and expose the centralized files.

Spring Cloud Config is Spring’s client/server approach for storing and serving distributed configurations across multiple applications and environments.

This configuration store is ideally versioned under Git version control and can be modified at application runtime. While it fits very well in Spring applications using all the supported configuration file formats together with constructs like Environment, PropertySource, or @Value, it can be used in any environment running any programming language.

```java
@Configuration
@PropertySource("classpath:foo.properties")
public class PropertiesWithJavaConfig {
    //...
}

@Value( "${jdbc.url}" )
private String jdbcUrl;

@Autowired
private Environment env;
...
dataSource.setUrl(env.getProperty("jdbc.url"));
```

Spring Cloud Config provides server and client-side support for externalized configuration in a distributed system. With the Config Server you have a central place to manage external properties for applications across all environments. The concepts on both client and server map identically to the Spring Environment and PropertySource abstractions, so they fit very well with Spring applications, but can be used with any application running in any language. As an application moves through the deployment pipeline from dev to test and into production you can manage the configuration between those environments and be certain that applications have everything they need to run when they migrate. The default implementation of the server storage backend uses git so it easily supports labelled versions of configuration environments, as well as being accessible to a wide range of tooling for managing the content. It is easy to add alternative implementations and plug them in with Spring configuration.


### Features
**Spring Cloud Config Server features:**

* HTTP, resource-based API for external configuration (name-value pairs, or equivalent YAML content)
* Encrypt and decrypt property values (symmetric or asymmetric)
* Embeddable easily in a Spring Boot application using @EnableConfigServer

**Config Client features (for Spring applications):**

* Bind to the Config Server and initialize Spring Environment with remote property sources
* Encrypt and decrypt property values (symmetric or asymmetric)
  
The library relies on three parameters to identify which property file to
use to configure a specific application:
* {application}—The name of the application as defined by the spring
.application.name property.
* {profile}—One of the active profiles defined by the spring.profiles.active
property.
* {label}—A discriminator defined by the specific configuration data repository.
In the case of Git, it can be a tag, a branch name, or a commit ID. It’s useful for
identifying a versioned set of config files.

Depending on your needs, you can organize the folder structure using different com-
binations, such as these:
* /{application}/application-{profile}.yml
* /{application}/application.yml
* /{application}-{profile}.yml
* /{application}.yml
* /application-{profile}.yml
* /application.yml

Spring Cloud Config Server will always return the properties from the most specific path, using the application name, active
profiles, and Git labels.

### Usage
#### Server
Add maven package
```xml
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-config-server</artifactId>
    </dependency>
```
Enable Config server for app

*ConfigServer.java*
```java
@SpringBootApplication
@EnableConfigServer
public class ConfigServer {
  public static void main(String[] args) {
    SpringApplication.run(ConfigServer.class, args);
  }
}
```

Configure Config server
```
server.port: 8888
spring.cloud.config.server.git.uri: file://${user.home}/config-repo
```

Below are the ways to access the configurations from the config server.

* /{application}/{profile}[/{label}]
* /{application}-{profile}.yml
* /{label}/{application}-{profile}.yml
* /{application}-{profile}.properties
* /{label}/{application}-{profile}.properties
#### Client
Add maven package
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-config</artifactId>
</dependency>
```

Enable Config server for client
```yml
spring:
  application:
    name: centralized-configuration-client
  config:
    import: optional:configserver:http://localhost:8888/
management:
  endpoints:
    web:
      exposure:
        #You also want to enable the /refresh endpoint, to demonstrate dynamic configuration changes. The listing above shows how to do so via the management.endpoints.web.exposure.include property.
        include: "*"
```
Use config variables in code
```java
/*
 * By default, the configuration values are read on the client’s startup and not again. 
 * You can force a bean to refresh its configuration (that is, to pull updated values from the Config Server) 
 * by annotating the MessageRestController with the Spring Cloud Config @RefreshScope and then triggering a refresh event
 */
@RefreshScope
@RestController
class MessageRestController {

    /*
     * The client can access any value in the Config Server by using the traditional mechanisms 
     * (such as @ConfigurationProperties or @Value("${…​}") or through the Environment abstraction). 
     * Now you need to create a Spring MVC REST controller that returns the resolved message property’s value
     */
    @Value("${message:Hello default}")
    private String message;

    @Value("${message1:Hello default1}")
    private String message1;

    @RequestMapping("/message")
    String getMessage() {
        return this.message;
    }

    @RequestMapping("/message1")
    String getMessage1() {
        return this.message1;
    }
}
```

## Examples
* [Baeldung Quick Intro to Spring Cloud Configuration](https://github.com/spring-kb/baeldung-quick-intro-to-spring-cloud-config)
* [ Quick Guide to Spring Cloud Consul](https://github.com/spring-kb/baeldung-spring-cloud-consul)
## Samples
* [Multiplication Microservices Example](https://github.com/books-java/Learn-Microservices-with-Spring-Boot-3)