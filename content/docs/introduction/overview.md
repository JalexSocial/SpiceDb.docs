---
title: "Overview"
description: ""
summary: ""
date: 2024-02-05T12:06:30-05:00
lastmod: 2024-02-05T12:06:30-05:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "overview-d93d15301c0c12c7496db4ce3d157080"
weight: 10
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

SpiceDb is an open-source, Zanzibar-inspired authorization system that provides a robust and scalable solution for managing fine-grained permissions across distributed systems. Its implementation closely follows the principles set out in Google's Zanzibar paper, adapting them into a practical and deployable system. 

## What is SpiceDB?

SpiceDB is an open source, [Google Zanzibar]-inspired database system for real-time, security-critical application permissions.

<img src="/images/developer1.webp" class="img-fluid" style="margin-bottom: 2rem">

Developers create and apply a schema that models their application's resources and permissions.
From their applications, client libraries such as SpiceDb.net are used to insert relationships or check permissions in their applications.

Building modern authorization from scratch is non-trivial and requires years of development from domain experts.
Until SpiceDB, the only developers with access to these workflows were employed by massive tech companies that could invest in building mature, but proprietary solutions.

Now we have a community organized around sharing this technology so that the entire industry can benefit.

In some scenarios, SpiceDB can be challenging to operate because it is a critical, low-latency, distirbuted system.
For folks interested in a managed SpiceDB services and enterprise functionality, there are [AuthZed's products](https://authzed.com/docs/authzed/guides/picking-a-product).

[Google Zanzibar]: https://authzed.com/blog/what-is-zanzibar/
[schema]: https://authzed.com/docs/guides/schema
[client libraries]: https://github.com/authzed/awesome-spicedb#clients
[relationships]: ../concepts/relationships
[authzed-products]: ../../authzed/guides/picking-a-product

### A brief SpiceDB history lesson

In August 2020, the founders of AuthZed left [Red Hat], who had acquired their previous company [CoreOS].
In the following month, they would write the first API-complete implementation of Zanzibar; project Arrakis was written in lazily-evaluated, type-annotated Python.
In September, Arrakis was demoed as a part of their [YCombinator] application.
In March 2021, Arrakis was rewritten in Go, a project code-named Caladan.
This rewrite would eventually be open-sourced in September 2021 under the name [SpiceDB].

You can read also read the [history of Google's Zanzibar project](https://authzed.com/docs/spicedb/concepts/zanzibar#history), which is the spirtual predecessor and inspiration for SpiceDB.

[Red Hat]: https://redhat.com
[CoreOS]: https://www.redhat.com/en/technologies/cloud-computing/openshift/what-was-coreos
[YCombinator]: https://www.ycombinator.com/companies/authzed
[SpiceDB]: https://authzed.com/blog/spicedb-is-open-source-zanzibar
[zanzibar-history]: ../concepts/zanzibar#history

### SpiceDB Features

Features that distinguish SpiceDB from other systems include:

- Expressive [gRPC] and [HTTP/JSON] APIs for checking permissions, listing access, and powering devtools
- A distributed, parallel graph-engine faithful to the architecture described in [Google's Zanzibar paper]
- A flexible consistency model configurable [per-request] that includes resistance to the [New Enemy Problem]
- An expressive [schema language] with a [playground] and CI/CD integrations for [validation] and [integration testing]
- A pluggable [storage system] supporting [in-memory], [Spanner], [CockroachDB], [PostgreSQL] and [MySQL]
- Deep observability with [Prometheus] metrics, [pprof] profiles, structured logging, and [OpenTelemetry] tracing

[gRPC]: https://buf.build/authzed/api/docs/main:authzed.api.v1
[HTTP/JSON]: https://app.swaggerhub.com/apis-docs/authzed/authzed/1.0

[per-request]: https://docs.authzed.com/reference/api-consistency
[New Enemy Problem]: https://authzed.com/blog/new-enemies/

[schema language]: https://docs.authzed.com/guides/schema
[playground]: https://play.authzed.com
[validation]: https://github.com/authzed/action-spicedb-validate
[integration testing]: https://github.com/authzed/action-spicedb

[storage system]: https://authzed.com/docs/spicedb/selecting-a-datastore
[in-memory]: https://github.com/hashicorp/go-memdb
[PostgreSQL]: https://www.postgresql.org
[Spanner]: https://cloud.google.com/spanner
[CockroachDB]: https://github.com/cockroachdb/cockroach
[MySQL]: https://www.mysql.com

[Prometheus]: https://prometheus.io
[pprof]: https://jvns.ca/blog/2017/09/24/profiling-go-with-pprof/
[OpenTelemetry]: https://opentelemetry.io

[Google's Zanzibar paper]: https://authzed.com/zanzibar


Below is an overview of the key features and components of SpiceDb's implementation of the Zanzibar algorithm.

### 1. **Architecture Overview**
SpiceDb operates with a service-oriented architecture that separates the storage layer from the logic layer, allowing for scalability and resilience. The system is built to handle large volumes of access checks with low latency.

### 2. **Namespace Configurations**
In SpiceDb, "namespaces" are used to define types of objects and their relations. Each namespace has a schema that specifies relations and permissions. These configurations allow developers to define complex hierarchical relationships and permission logic that mirror those found in Zanzibar.

### 3. **Relation Tuples**
At the heart of SpiceDb is the concept of "relation tuples", which are records that define the relationships between objects, users, and permissions. These tuples are analogous to Zanzibar's "ACL tuples" and are fundamental in resolving authorization queries.

### 4. **Authorization Queries**
SpiceDb processes authorization queries by evaluating the relation tuples against the namespace schemas. It utilizes optimized graph traversal algorithms to efficiently resolve whether a user has a certain permission on an object, even through multiple layers of relationships.

### 5. **Consistency and Storage**
SpiceDb ensures strong consistency and durability by leveraging modern distributed databases as its backend storage solution. This setup enables SpiceDb to maintain high performance and reliability, which are critical for authorization systems.

### 6. **APIs and Integration**
SpiceDb provides gRPC and HTTP APIs, making it highly compatible with various programming environments. These APIs allow for seamless integration with existing services and applications, facilitating easy implementation of complex authorization rules defined in the Zanzibar paper.

### 7. **Scalability and Performance**
Designed for high scalability, SpiceDb can serve thousands of authorization checks per second. It uses caching and batch processing techniques to minimize latency and maximize throughput.

### 8. **Security and Compliance**
SpiceDb is designed with security at its core, offering robust mechanisms to ensure data integrity and confidentiality. It also supports various compliance requirements, making it suitable for use in regulated industries.

### 9. **Community and Support**
As an open-source project, SpiceDb benefits from a community of developers who contribute to its ongoing improvement. The project offers comprehensive documentation, tutorials, and community support forums to assist users in deploying and maintaining their authorization systems.

