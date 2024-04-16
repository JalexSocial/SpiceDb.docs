---
title: "DeleteRelationship"
description: ""
summary: ""
date: 2024-04-12T14:00:29-04:00
lastmod: 2024-04-12T14:00:29-04:00
draft: false
weight: 50
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Removes an existing relationship (if it exists).

**Parameters**

- `relation` - The relationship to remove.

**Returns**

- A task representing the asynchronous operation, with a `ZedToken` indicating the version of the data after the relationship is removed.

## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var relationship = new Relationship("document:firstdoc", "reader", "user:charlie");

// Remove an existing relationship if it exists.
var resultToken = await client.DeleteRelationshipAsync(relationship);
Console.WriteLine($"Relationship deleted at token: {resultToken.Token}");
```