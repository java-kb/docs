---
title: Containerize Spring Boot
parent: Cloud Native Buildpacks
has_children: true
nav_order: 1
---

# Containerize Spring Boot
Cloud Native Buildpacks has been integrated natively in the Spring Boot Plugin for both Gradle and Maven, so you’re not required to install the dedicated Buildpacks CLI (pack).

The Spring Boot Plugin adopts the Paketo Buildpacks builder, an implementation of the Cloud Native Buildpacks specification that provides support for many types of applications, including Java and Spring Boot ones (https://paketo.io).

The Paketo builder component relies on a series of default buildpacks for the actual build operation. This structure is highly modular and customizable. You can add new buildpacks to the sequence (for example, to add a monitoring agent to the
application), replace existing ones (for example, to replace the default Bellsoft Liberica OpenJDK with Microsoft OpenJDK), or even use a different builder image entirely.

1. configure plugin
    ```xml
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <configuration>
                <image>
                    <name>${project.artifactId}</name>
                    <env>
                        <BP_JVM_VERSION>17</BP_JVM_VERSION>
                    </env>
                </image>
            </configuration>
        </plugin>
    ```
1. Build image
    ```console
    ./mvnw spring-boot:build-image
    ```
    // Or from root
    ```console
    mvn spring-boot:build-image -pl service1
    ```
1. Build and Publish
    
    * To GitHub Container Registry
        ```bash
        ./mvnw spring-boot:build-image \
        --imageName ghcr.io/<your_github_username>/service1 \
        --publishImage \
        -PregistryUrl=ghcr.io \
        -PregistryUsername=<your_github_username> \
        -PregistryToken=<your_github_token>
        ```
1. Run
    ```console
    docker images service1

    docker run --rm --name service1 -p 8080:8080 service1:1.0
    ```