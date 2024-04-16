---
title: "AddRelationships"
description: ""
summary: ""
date: 2024-04-12T13:59:54-04:00
lastmod: 2024-04-12T13:59:54-04:00
draft: false
weight: 20
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Adds or updates multiple relationships as a single atomic update.

**Parameters**

- `relationships` - List of relationships to add or update.

**Returns**

- A task representing the asynchronous operation, with a `ZedToken?` indicating the version of the data after the operation.

## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var relationships = new List<Relationship>
{
    new Relationship("document:firstdoc", "reader", "user:alice")
};

// Add or update multiple relationships as a single atomic operation.
var resultToken = await client.AddRelationshipsAsync(relationships);
Console.WriteLine($"Relationships added at token: {resultToken?.Token}");
```