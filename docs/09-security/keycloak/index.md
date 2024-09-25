---
title: Keycloak
parent: Security
has_children: true
nav_order: 1
---

# Keycloak

# Installing and running Keycloak
## Development
### Using Docker
**run for the first time**
```console
docker run -d --name Keycloak1 -p 8080:8080 \
        -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
        quay.io/keycloak/keycloak:24.0.5 \
        start-dev --import-realm
```
**import config**
```console
docker run -d --name Keycloak1 -p 8080:8080 \
        -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin \
        -v ./docker/keycloak/export:/opt/keycloak/data/import \
        quay.io/keycloak/keycloak:24.0.5 \
        start-dev --import-realm
```
**start container**
```console
docker start Keycloak1
```
### Kubernetes
### Using the Keycloak Kubernetes Operator
### Locally
On Linux or macOS, start Keycloak with the following command:
```console
export KEYCLOAK_ADMIN=admin
export KEYCLOAK_ADMIN_PASSWORD=admin
cd $KC_HOME
bin/kc.sh start-dev
```
 on Windows, execute the following command:
 ```console
set KEYCLOAK_ADMIN=admin
set KEYCLOAK_ADMIN_PASSWORD=admin
cd %KC_HOME%
bin\kc.bat start-dev
 ```
## Production
## Examples

* [Spring Cloud Gateway with OpenID Connect and Token Relay](https://github.com/spring-kb/spring-cloud-gateway-oidc-tokenrelay)