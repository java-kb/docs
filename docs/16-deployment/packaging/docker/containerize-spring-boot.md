---
title: Containerize Spring Boot
parent: Docker
has_children: true
nav_order: 1
---

# Containerize Spring Boot
Cloud native applications are self-contained. Spring Boot lets you package your applications as standalone JARs, including everything they need to run except the runtime environment. That makes the containerization very straightforward, since all you need in a container image besides the JAR artifact is an operating system and a JRE.

## Packaging Spring Boot applications as container images
### Containerizing Spring Boot with Dockerfiles
```docker
FROM openjdk:17

WORKDIR /workspace 

ARG JAR_FILE=./target/*.jar

COPY ${JAR_FILE} catalog-service.jar 

ENTRYPOINT ["java", "-jar", "catalog-service.jar"]
```
```bash
cd app-service
mvn clean package spring-boot:repackage
docker build -t app-service .
```
### Containerizing Spring Boot using layered-JAR mode
When building container images, you should consider performance at build time and
at run time. The layered architecture characterizing OCI images enables the caching
and reusing of unchanged layers when building an image. Container registries store images by layers, so that when you pull a new version, only the changed layers are
downloaded. That is quite an advantage in a cloud environment, considering the time
and bandwidth you’ll save for all your application instances.

In the above dockerfile section, the standalone JAR file copied into a layer in the image. As a result, whenever you change something in your application,
the whole layer must be rebuilt. Consider the scenario where you just add a new REST
endpoint to your application. Even if all the Spring libraries and dependencies are
unchanged, and the only difference is in your own code, you must rebuild the whole
layer, since everything is together. 

Spring Boot can package applications as JAR artifacts: the layered-JAR mode. which is the default mode, so you don’t need any extra configuration to use the new functionality.

Applications packaged using the layered-JAR mode are made up of layers, similar to
how container images work. This new feature is excellent for building more efficient
images. When using the new JAR packaging, we can expand the JAR artifact and then
create a different image layer for each JAR layer. The goal is to have your own classes
(which change more frequently) on a separate layer from the project dependencies
(which change less frequently).
 By default, Spring Boot applications are packaged as JAR artifacts made up of the
following layers, starting from the lowest:
* dependencies—For all the main dependencies added to the project
* spring-boot-loader—For the classes used by the Spring Boot loader component
* snapshot-dependencies—For all the snapshot dependencies
* application—For your application classes and resources

We’ll divide the work into two stages. In the first stage we extract the layers from
the JAR file. The second stage is where we place each JAR layer into a separate image layer. In the end, the result of the first stage is discarded (including the original JAR file), while the second stage will produce the final container image.

```docker
FROM openjdk:17 AS builder

WORKDIR /workspace

ARG JAR_FILE=./target/*.jar

COPY ${JAR_FILE} catalog-service.jar

RUN java -Djarmode=layertools -jar catalog-service.jar extract

FROM openjdk:17

RUN useradd spring

USER spring

WORKDIR /workspace

COPY --from=builder workspace/dependencies/ ./
COPY --from=builder workspace/spring-boot-loader/ ./
COPY --from=builder workspace/snapshot-dependencies/ ./
COPY --from=builder workspace/application/ ./

ENTRYPOINT ["java", "org.springframework.boot.loader.JarLauncher"]
```
