---
title: DB Migration Tools
has_children: true
parent: DB
nav_order: 3
---

# DB Migration Tools
It’s good practice to register any database changes, just like you do for your applica-
tion source code through version control. You’ll need a deterministic and automated
way to infer the database’s state, whether specific changes have already been applied,
how to recreate a database from scratch, and how to migrate it in a controlled, repeat-
able, and reliable way. The continuous delivery approach encourages automating as
much as possible, including database management.

Spring Data offers a feature to initialize a data source at startup time. By default,
you can use a schema.sql file to create a schema and a data.sql file to insert data in the
newly created tables. Such files should be placed in the src/main/resources folder.
 That is a convenient feature, and it’s useful for demos and experiments. However, it’s
too limited for use in production.  it’s better to create
and evolve relational resources with a more sophisticated tool, like Flyway or Liquibase,
which will let you version-control your database. 