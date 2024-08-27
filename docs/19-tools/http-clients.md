---
title: Testing Http Requests
parent: Tools
nav_order: 1
---


## http
### Install
sudo apt install httpie
### Usage
#### Get
```bash
http :8080/get
```
#### Post
```bash
http POST :8000/post hello=world
```
```bash
http --ignore-stdin POST :8000/attempts factorA=15 factorB=20 userAlias=test-gamification-service-down guess=300
```
#### Put
#### Delete
```bash
http DELETE http://localhost:8090/delete
```
#### Authenticate
```bash
http -a username:password pie.dev/basic-auth/username/password
```
#### Headers
```bash
http pie.dev/headers User-Agent:Bacon/1.0 'Cookie:valued-visitor=yes;foo=bar' \
    X-Foo:Bar Referer:https://httpie.org/

```
```bash
http :8080/headers Host:www.myhost.org  
```  
#### Repeat
```bash
for i in {1..10}; do http --ignore-stdin POST :8000/attempts factorA=15 factorB=20 userAlias=test-gamification-service-down guess=300; done
```
## curl

### Install

### Usage
#### Get
```bash
curl http://localhost:8080/get
```
#### Post
```bash
http POST :8000/post hello=world
```
```bash
http --ignore-stdin POST :8000/attempts factorA=15 factorB=20 userAlias=test-gamification-service-down guess=300
```
#### Put
#### Delete
```bash
http DELETE http://localhost:8090/delete
```
#### Authenticate
```bash
http -a username:password pie.dev/basic-auth/username/password
```
#### Headers
```bash
http pie.dev/headers User-Agent:Bacon/1.0 'Cookie:valued-visitor=yes;foo=bar' \
    X-Foo:Bar Referer:https://httpie.org/

```
```bash
http :8080/headers Host:www.myhost.org  
```  
#### Repeat
```bash
for i in {1..10}; do http --ignore-stdin POST :8000/attempts factorA=15 factorB=20 userAlias=test-gamification-service-down guess=300; done
```