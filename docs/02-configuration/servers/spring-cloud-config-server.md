---
title: Configuration Servers
parent: Configuration Servers
nav_order: 1
---

# Spring Cloud Config
## Profiles
one of the main advantages of Spring Boot is its ability 
to configure profiles. A profile is a set of configuration properties that you can enable 
depending on your needs. For example, you could switch between connecting to a 
local RabbitMQ server while testing locally and the real RabbitMQ server running on 
production when you deploy it to that environment.

To introduce a new rabbitprod profile, create a file named application-
rabbitprod.properties. Spring Boot uses the application-{profile} naming 
convention (for both properties and YAML formats) to define profiles in separate files. 

If you use this profile for the production environment, you may want to use different credentials, a cluster of 
nodes to connect to, a secure interface, and so on.
```yml
spring.rabbitmq.addresses=rabbitserver1.tpd.network:5672,rabbitserver2.tpd.
network:5672
spring.rabbitmq.connection-timeout=20s
spring.rabbitmq.ssl.enabled=true
spring.rabbitmq.username=produser1
```

You have to make sure you enable this profile when you start the application in the 
target environment. To do that, you use the spring.profiles.active property. Spring 
Boot aggregates the base configuration (in application.properties) with the values 
in this file. In this case, all extra properties will be added to the resulting configuration. 
You can use a Spring Boot’s Maven plugin command to enable this new profile

```bash
./mvnw spring-boot:run -Dspring-boot.run.arguments="--spring.profiles.active=rabbitprod"
```

## Spring Cloud Config Server
The configuration server pattern for Spring is the Spring Cloud Config Server project. This 
is a native implementation included in the Spring Cloud family, which allows you to 
keep a set of configuration files distributed in folders and exposed via a REST API. On 
the client side, the projects using this dependency access the config server and request 
the corresponding configuration resources, depending on their active profiles. The only 
drawback of this solution is that you need to create another microservice to act as the 
configuration server and expose the centralized files.

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