---
title: Testcontainers
parent: Spring Testing
grand_parent: Spring Framework
nav_order: 1
---

# Testcontainers
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
When the integration profile is enabled, Spring Boot will use the PostgreSQL container instantiated by Testcontainers. 