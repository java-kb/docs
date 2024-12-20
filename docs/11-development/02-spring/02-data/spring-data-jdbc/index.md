---
title: Spring Data JDBC
parent: Spring Data
grand_parent: Spring Framework
nav_order: 1
---

# Spring Data JDBC
Spring Data JDBC encourages working with immutable entities. Using Java records to
model entities is an excellent choice, since they’re immutable by design and expose
an all-args constructor that the framework can use to populate objects.
## Enabling and configuring JDBC auditing
When persisting data, it’s useful to know the creation date for each row in a table and
the date when it was updated last. After securing an application with authentication
and authorization, you can even register who created each entity and recently updated
it. All of that is called database auditing.
 With Spring Data JDBC, you can enable auditing for all the persistent entities
using the @EnableJdbcAuditing annotation on a configuration class. 
```java
import org.springframework.context.annotation.Configuration;
import org.springframework.data.jdbc.repository.config.EnableJdbcAuditing;

@Configuration
@EnableJdbcAuditing
public class DataConfig {
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
## Data repositories with Spring Data
The repository pattern provides an abstraction for accessing data independently of its
source.

When using Spring Data repositories, your responsibility is limited to defining an
interface. At startup time, Spring Data will generate an implementation for your interface on the fly. 

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
Spring Data JDBC supports this option only for read operations.

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

## DEFINING TRANSACTIONAL CONTEXTS
The repositories provided by Spring Data come configured with transactional con-
texts for all the operations. For example, all methods in CrudRepository are transac-
tional. That means you can safely call the saveAll() method, knowing that it will be
executed in a transaction.
 When you add your own query methods, it’s up
to you to define which ones should be part of a transaction. You can rely on the
declarative transaction management provided by the Spring Framework and use
the @Transactional annotation (from the org.springframework.transaction
.annotation package) on classes or methods to ensure they are executed as part of
a single unit of work.
```java
@Modifying
@Transactional
@Query("delete from Book where isbn = :isbn")
void deleteByIsbn(String isbn);
```
## Usage
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jdbc</artifactId>
</dependency>
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <scope>runtime</scope>
</dependency>
```

Domain
```java
public record Book(

        @Id Long id,

        @NotBlank(message = "The book ISBN must be defined.") @Pattern(regexp = "^([0-9]{10}|[0-9]{13})$", message = "The ISBN format must be valid.") String isbn,

        @NotBlank(message = "The book title must be defined.") String title,

        @NotBlank(message = "The book author must be defined.") String author,

        @NotNull(message = "The book price must be defined.") @Positive(message = "The book price must be greater than zero.") Double price,

        String publisher,

        @CreatedDate Instant createdDate,

        @LastModifiedDate Instant lastModifiedDate,

        @Version int version

) {

    public static Book of(String isbn, String title, String author, Double price, String publisher) {
        return new Book(null, isbn, title, author, price, publisher, null, null, 0);
    }

}
```