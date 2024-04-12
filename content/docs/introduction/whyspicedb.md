---
title: "Why SpiceDb?"
description: ""
summary: ""
date: 2024-04-12T12:50:41-04:00
lastmod: 2024-04-12T12:50:41-04:00
draft: false
weight: 14
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Zanzibar-inspired systems like SpiceDb offer an evolved approach to access control compared to traditional RBAC. These systems enable dynamic and granular permission management that adjusts in response to changes in user relationships and roles, and are driven by a configurable schema.

This schema-driven flexibility allows your permission system to be tailored to your specific business needs without extensive coding. Instead of being locked into a rigid set of predefined roles, you can configure and modify your permissions model as your organizational structures or business rules change. This makes SpiceDb not only adaptable but also significantly reduces the overhead and complexity typically associated with modifying access control systems.

Furthermore, SpiceDb’s approach to managing permissions at the level of individual relationships ensures that permissions are accurately represented and enforced, reducing management complexity and improving system performance in demanding environments. It also maintains consistent and auditable access controls across different services, reducing discrepancies and enhancing security without compromising scalability.

For developers and businesses of any size, adopting SpiceDb means investing in a flexible and adaptable authorization mechanism that evolves efficiently with your business needs.

Here is an example of a simple schema that could be used to allow access control to a document:

```

  /** user represents a registered user's account in our application */
  definition user {}
  
  /** document represents a document with access control */
  definition document {
    /** reader indicates that the user is a reader on the document */
    relation reader: user
  
    /** writer indicates that the user is a writer on the document */
    relation writer: user
  
    /** view indicates whether the user can view the document */
    permission view = reader + writer
  }

```

For more information on schema development, see [Developing a Schema](https://authzed.com/docs/spicedb/modeling/developing-a-schema)