---
title: "WriteRelationships"
description: ""
summary: ""
date: 2024-04-12T14:02:20-04:00
lastmod: 2024-04-12T14:02:20-04:00
draft: false
weight: 140
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Atomically writes and/or deletes a set of specified relationships, with optional preconditions.

**Parameters**

- `relationships` - A list of relationship updates to apply.
- `optionalPreconditions` (optional) - An optional list of preconditions that must be satisfied for the operation to commit.

**Returns**

- A task representing the asynchronous operation, with a `ZedToken?` indicating the version of the data after the write operation.

## Example

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var relationships = new List<RelationshipUpdate>
{
    new RelationshipUpdate
    {
        Operation = RelationshipUpdateOperation.Create,
        Relationship = new Relationship("document:firstdoc", "reader", "user:bob")
    }
};

// Atomically writes the specified relationships.
var resultToken = await client.WriteRelationshipsAsync(relationships);
Console.WriteLine($"Operation written at: {resultToken?.Token}");
```

