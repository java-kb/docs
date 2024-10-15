---
title: Builder
parent: Creational Design Patterns
has_children: true
nav_order: 5
---

# Builder Design Pattern
The Gang of Four describes the purpose of the “Prototype” pattern as follows:

> Separate the construction of a complex object from its representation, so that the same con-
struction process can produce different representations.

With the builder pattern, you have an object that is complex or complicated to construct. This object cannot be created in one pass, but goes through an 
elaborate construction process.

* A Builder is an object whose task is to build other objects-.
* The design process is isolated in the Builder.
* Usually the construction process of the objects to be built is complex or complicated; 
often several steps are required.
* Builders can also be chained together and thus made dependent on each other.
* Since the data is independent of the object creation, many similar objects can be created.
* Typically, builders are used to build a composite.

## Identification
The Builder pattern can be recognized in a class, which has a single creation method and several methods to configure the resulting object. Builder methods often support chaining (for example, someBuilder.setValueA(1).setValueB(2).create()).

## Usage examples
## JDK
Builder is widely used in Java core libraries:

* java.lang.StringBuilder#append() (unsynchronized)
* java.lang.StringBuffer#append() (synchronized)
* java.nio.ByteBuffer#put() (also in CharBuffer, ShortBuffer, IntBuffer, LongBuffer, FloatBuffer and DoubleBuffer)
* javax.swing.GroupLayout.Group#addComponent()
* All implementations java.lang.Appendable

## Spring
* EmbeddedDatabaseBuilder
```java
@Bean
public DataSource dataSource() {
    return new EmbeddedDatabaseBuilder()
            .setName("dataSource")
            .setType(EmbeddedDatabaseType.H2)
            .addScript("schema.sql")
            .addScript("data.sql")
            .build();
}
```

## Examples
https://github.com/java-kb/design_patterns