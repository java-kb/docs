---
title: Flyway
has_children: true
parent: DB Migration Tools
grand_parent: DB
nav_order: 1
---

# Flyway
Flyway is a tool that provides version control for your database. It offers a single source
of truth for the version of your database’s state and keeps track of any changes incre-
mentally. It automates changes and lets you reproduce or roll back the state of a data-
base. Flyway is highly reliable, safe to use in cluster environments, and supports
several relational databases, including the cloud ones like Amazon RDS, Azure Data-
base, and Google Cloud SQL.

At its core, Flyway manages database changes. Any database change is called a migra-
tion, and migrations can be either versioned or repeatable. 
* Versioned migrations are
identified by a unique version number and are applied in order exactly once. For
each regular versioned migration, you can also provide an optional undo migration
to revert its effects (in case something goes wrong). They can be used to create,
alter, or drop relational objects like schemas, tables, columns, and sequences or to
correct data. 
* On the other hand, repeatable migrations are applied every time their
checksum changes. They can be used for creating or updating views, procedures,
and packages.

Both types of migration can be defined in standard SQL scripts (useful for DDL
changes) or Java classes (useful for DML changes, like data migrations). Flyway keeps
track of which migrations have already been applied through a flyway_schema_history
table automatically created in the database the first time it runs. You can picture
migrations as commits in a Git repository and the schema history table as the reposi-
tory log containing the list of all the commits applied over time 

## Spring Integeration
You can use Flyway in standalone mode or embedded in a Java application. Spring
Boot provides auto-configuration for it, making it very convenient to include Flyway in
your applications. When integrated with Spring Boot, Flyway will search for SQL
migrations in the src/main/resources/db/migration folder and Java migrations in
src/main/java/db/migration.

Running schema and data migrations is one of those administrative processes described by the 15-Factor methodology. In this case, the
strategy adopted for managing such a process was to embed it in the application itself. By default, it’s activated during the application startup phase. 
1.  add a dependency on Flyway 
```xml
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-core</artifactId>
</dependency>
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-database-postgresql</artifactId>
</dependency>
```
1.  create a src/main/resources/db/migration folder. That’s where Flyway will
look for SQL migrations by default. Inside the folder, create a V1__Initial_schema.sql
file, which will contain the SQL statement for initializing the database schema required by the  Service application. Flyway expects SQL migration files to comply with a specific naming pattern. Regular versioned migrations should follow this structure:
    * Prefix—V for versioned migrations
    * Version—Version number using dots or underscores to separate it into multiple
    parts (e.g., 2.0.1)
    * Separator—Two underscores: __
    * Description—Words separated by underscores
    * Suffix—.sql
## make field mandatory
1. using an new SQL migration to enforce the field
column to be NON NULL 
1. and implementing a Java migration that adds a field to all
the existing table rows in the database that don’t have one already.
