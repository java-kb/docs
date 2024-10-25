---
title: Spring Development
parent: Spring Framework
grand_parent: Development
nav_order: 11
---

# Spring Development
## Gradle and Maven
a table mapping Gradle commands to Maven so that you can easily follow along.

Gradle | Maven
------ | ------
`./gradlew clean` | `./mvnw clean`
`./gradlew build` | `./mvnw install`
`./gradlew test` | `./mvnw test`
`./gradlew bootJar` | `./mvnw spring-boot:repackage`
`./gradlew bootRun` | `./mvnw spring-boot:run`
`./gradlew bootBuildImage` | `./mvnw spring-boot:build-image -DskipTests`