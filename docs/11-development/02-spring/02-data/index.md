---
title: Spring Data
parent: Spring Framework
grand_parent: Development
nav_order: 2
---

# Spring Data
## In Brief
 Spring Data provides common abstractions and patterns for accessing data,
making it straightforward to navigate the different modules dedicated to rela-
tional and non-relational databases.
* The main elements in Spring Data are database drivers, entities, and repositories.
* Spring Data JDBC is a framework that supports integrating Spring applications
with relational databases relying on a JDBC driver.
* Entities represent domain objects and can be managed by Spring Data JDBC as
immutable objects. They must have the field hosting the primary key annotated
with @Id.
* Spring Data lets you capture audit metadata whenever an entity is created or
updated. You can enable this feature with @EnableJdbcAuditing.
* Data repositories grant access to entities from the database. You need to define
an interface, and then Spring Data will generate the implementation for you.
* Depending on your requirements, you can extend one of the available
Repository interfaces provided by Spring Data, such as CrudRepository.
* In Spring Data JDBC, all mutating custom operations (create, update, delete)
should run in transactions.
* Use the @Transactional annotation to run operations in a single unit of work.
* You can run integration tests for the Spring Data JDBC slice using the @Data-
JdbcTest annotation.
* Environment parity is essential for the quality and reliability of your tests and
deployment pipeline.
* You can test the integration between your application and backing services
defined as containers by using the Testcontainers library. It lets you use light-
weight, throwaway containers in your integration tests.
* Database schemas are critical for applications. In production, you should use a
tool like Flyway, which provides version control for your database.
* Flyway should manage any database changes to ensure reproducibility, trace-
ability, and reliability.
## Spring Data JDBC or Spring Data JPA?
Spring Data offers two main options for integrating applications with a relational database over the JDBC driver: Spring Data JDBC and Spring Data JPA. How to choose
between the two? As always, the answer is that it depends on your requirements and
specific context.

**Spring Data JPA** (https://spring.io/projects/spring-data-jpa) is the most-used module in the Spring Data project. It’s based on the Java Persistence API (JPA), a standard specification included in Jakarta EE (previously known as Java EE). Hibernate is the most popular implementation. It’s a robust and battle-tested object-relational mapping (ORM) framework for managing data persistence in Java applications. Hibernate provides many useful features, but it’s also a complex framework. If you’re not aware of aspects like persistence context, lazy loading, dirty checking, or sessions, you might face issues that will be hard to debug without a sound familiarity with JPA and Hibernate. Once you know the framework better, you’ll appreciate how much Spring Data JPA simplifies things and boosts your productivity.

**Spring Data JDBC** (https://spring.io/projects/spring-data-jdbc) is a more recent addition to the Spring Data family. It integrates with relational databases following the domain-driven design (DDD) concepts like aggregates, aggregate roots, and reposi-
tories. It’s lightweight, simpler, and an excellent choice for microservices where
domains are usually defined as bounded contexts (another DDD concept). It gives
developers more control over SQL queries and allows the use of immutable entities.
Being a simpler alternative to Spring Data JPA, it’s not a drop-in replacement for every scenario, since it doesn’t provide all the features offered by JPA. 

You should considering your requirements, and then deciding which module suits the specific scenario better.

*  Spring Data offers a feature to initialize a data source at startup time. By default, you can use a schema.sql file to create a schema and a data.sql file to insert data in the newly created tables. Such files should be placed in the src/main/resources folder.
* Spring Data loads the schema.sql file only when using an embedded, in-memory database.FOr other DB, we need to enable the functionality explicitly.
    ```yml
    spring:
        sql:
            init:
                mode: always
    ```
* Hibernate, the foundation for Spring Data JPA, offers automatically generating schemas from the entities defined in Java. 

## Testing data persistence with Spring and Testcontainers
Testcontainers (https://testcontainers.org) is a Java library for testing. It supports
JUnit and provides lightweight, throwaway containers such as databases, message brokers, and web servers. It’s perfect for implementing integration tests with the actual backing services used in production. The result is more reliable and stable tests, which lead to higher-quality applications and favor continuous delivery practices.
1. Adding dependency on Testcontainers
    ```xml
    <properties>
        <testcontainersVersion>1.17.3</testcontainersVersion>
    </properties>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.testcontainers</groupId>
                <artifactId>testcontainers-bom</artifactId>
                <version>${testcontainersVersion}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.testcontainers</groupId>
            <artifactId>postgresql</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
    ```
2. Create a new application-integration.yml file in src/test/resources, and add the
following configuration.
    ```yml
    spring:
        datasource:
            url: jdbc:tc:postgresql:14.12:///
    ```
When the integration profile is
enabled, Spring Boot will use the PostgreSQL container instantiated by Testcontain-
ers. 