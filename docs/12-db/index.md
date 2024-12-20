---
title: DB
has_children: true
nav_order: 12
---

# DB
## In Brief
* The state is everything that should be preserved when shutting down a service
and spinning up a new instance.
* Data services are the stateful components of a cloud native architecture, requir-
ing storage technologies to persist the state.
* Using data services in the cloud is challenging because it’s a dynamic environment.
 Some issues to consider when choosing a data service are scalability, resilience,
performance, and compliance with specific regulations and laws.
* You can use data services that are offered and managed by your cloud provider
or manage your own, either relying on virtual machines or containers.
## Choosing a Database
requirements of project, such as 
* the availability, 
* volume of data, 
* expected traffic, 
* ata model complexity, 
* desired performance.
* scalability requirements and consider whether the chosen database can handle future growth

data requirements
* How are you planning to query the data? 
* Do you need high availability? 
* How complex is your data model? 
* Are you writing millions of records?
* Do you need very fast readings? 
nonfunctional requirements of your system
* scalability:consider whether the chosen database can handle future growth
* performance

## SQL vs. NoSQL
https://en.wikipedia.org/wiki/CAP_theorem

| Characteristics  | Relational (or SQL) Database  | NoSQL Database  |
| :---- | :---- | :---- |
| **Data model** | Fixed schema. Altering schemas can be more complex  |  Flexible schema. Schema changes are easier  |
| **Use cases** | Applications with structured and related data | Applications with unstructured data such as key-value pairs, documents, graphs, or column-based data  |
| **Transactional consistency** | ACID-compliant (Atomicity, Consistency, Isolation, Durability)  | Eventual consistency  |
| **Data integrity** | Strong data integrity and validation by defining complex relationships and constraints | Less strict data integrity checks, as it usually provides minimal support for defining complex relationships  |
| **Query support** | SQL-based queries and multi-table joins | Query capabilities differ among different NoSQL database  |
| Performance  | Well-suited for complex queries Excellent performance for read-heavy workloads | Horizontal scaling Limited options Flexible scaling options  |
| Cost | Higher cost due to hardware upgrades | Lower cost due to distributed architecture |



There are a few properties you should consider to ensure
you choose the most suitable technology.
* Scalability—Cloud native applications can scale in and out dynamically. Data ser-
vices are no different: they should scale to adapt to increasing or decreasing workloads. The new challenge is scaling while ensuring safe access to the data
storage. The amount of data flying through a system in the cloud is larger than
ever, and there can be sudden increments, so data services should support the
likelihood of increasing workloads and be resilient.
* Resilience—Much like cloud native applications, data services should be resilient
to failures. The new aspect here is that the data persisted using a specific stor-
age technology should also be resilient. One of the key strategies for ensuring
your data is resilient and preventing data loss is duplication. Replicating data
across different clusters and geographical zones makes it even more resilient,
but this comes at a cost. Data services like relational databases allow replication
while ensuring data consistency. Others, like some non-relational databases,
provide a high level of resilience but can’t always guarantee data consistency
(they offer what is referred to as eventual consistency).
* Performance—The way data is duplicated can affect performance, which is also
limited by the I/O access latency of the specific storage technology and the net-
work latency. Where the storage is located compared to the data services relying
on it becomes important—this is a concern that we haven’t encountered with
cloud native applications.
* Compliance—You might face compliance challenges with data services more than
with cloud native applications. Persisted data is usually critical for businesses
and often contains information protected by specific laws, regulations, or cus-
tomer agreements regarding how it’s managed. For example, when dealing
with personal and sensitive information, it’s vital that you manage data in accor-
dance with privacy laws. In Europe, that would mean following the General Data
Protection Regulation (GDPR). In California, there is the California Consumer
Privacy Act (CCPA). In other domains, further laws apply. For example, health
data in the United States should be handled in compliance with the Health Insur-
ance Portability and Accountability Act (HIPAA). Both the cloud native storage
and cloud provider should comply with whatever laws or agreements you are
required to respect. Because of this challenge, some organizations dealing with
very sensitive data, like health care providers and banks, prefer to use a type of
cloud native storage on their premises so they have more control over data man-
agement and can ensure compliance with the applicable regulations. 

## Categories of data services for the cloud
Data services can be managed by you (as containers or on virtual machines) or by the cloud 
provider. In the first case you can use more traditional services, and in the second, you can also access multiple 
services built specifically for the cloud by the provider.
![alt text](image.png)