---
title: Visitor
parent: Behavioral Design Patterns
has_children: true
nav_order:1
---

# Visitor
The Gang of Four describes the purpose of the Visitor pattern as follows:

> Encapsulate an operation to be performed on the elements of an object structure as an object. 
> The visitor pattern allows you to defne a new operation without changing the classes of the 
> elements it operates on.

Visitor is a behavioral design pattern that allows adding new behaviors to existing class hierarchy without altering any existing code.

Visitor isn’t a very common pattern because of its complexity and narrow applicability.

## Identification
The prototype can be easily recognized by a clone or copy methods, etc.

## Usage examples
## JDK
Visitor isn’t a very common pattern because of its complexity and narrow applicability.

Here are some examples of pattern in core Java libraries:

* javax.lang.model.element.AnnotationValue and AnnotationValueVisitor
* javax.lang.model.element.Element and ElementVisitor
* javax.lang.model.type.TypeMirror and TypeVisitor
* java.nio.file.FileVisitor and SimpleFileVisitor
* javax.faces.component.visit.VisitContext and VisitCallback

## Examples
https://github.com/java-kb/design_patterns