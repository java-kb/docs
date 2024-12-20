---
title: Spring Data JPA
parent: Spring Data
grand_parent: Spring Framework
nav_order: 2
---

# Spring Data JPA
Spring Data JPA works with mutating objects, so you can’t use Java
records. JPA entity classes must be marked with the @Entity annotation and
expose a no-args constructor. JPA identifiers are annotated with @Id and
@Version from the javax.persistence package instead of org.springframework.data.annotation.
## Enabling and configuring JPA auditing
When persisting data, it’s useful to know the creation date for each row in a table and
the date when it was updated last. After securing an application with authentication
and authorization, you can even register who created each entity and recently updated
it. All of that is called database auditing.
 With Spring Data JPA, you can enable auditing for all the persistent entities
using the @EnableJpaAuditing annotation on a configuration class. 
```java
import org.springframework.context.annotation.Configuration;
import org.springframework.data.jpa.repository.config.EnableJpaAuditing;

@Configuration
@EnableJpaAuditing
public class DataConfig {
}
```
and you would annotate the entity class with @EntityListeners(AuditingEntityListener.class) to make it listen to audit events, which doesn’t happen automatically as in Spring Data JDBC.
```java
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

@Entity
@EntityListeners(AuditingEntityListener.class)
public class Book {
}
```
Spring Data provides convenient annotations that we can use on dedicated fields to capture the information from such events (audit
metadata) and store it in the database as part of the entity.
```java
@CreatedDate
private Instant createdDate;

@LastModifiedDate
private Instant lastModifiedDate;
```

There are two main options for defining custom queries in Spring Data:
* Using the @Query annotation to provide an SQL-like statement that will be exe-
cuted by the method.
    ```java
    @Modifying
    @Transactional
    @Query("delete from Book where isbn = :isbn")
    void deleteByIsbn(String isbn);
    ```
* Defining query methods following a specific naming convention.
Spring Data JPA provides full support for read and write operations.

    |Repository method building block |Examples|
    |:--------------------------------|:------|
    |Action| find, exists, delete, count|
    |Limit |One, All, First10|
    |-| By|
    |Property expression| findByIsbn, findByTitleAndAuthor, findByAuthorOrPrice|
    |Comparison |findByTitleContaining, findByIsbnEndingWith, findByPriceLessThan|
    |Ordering operator |orderByTitleAsc, orderByTitleDesc|

    ```java
    Optional<Book> findByIsbn(String isbn);

    boolean existsByIsbn(String isbn);
    ```