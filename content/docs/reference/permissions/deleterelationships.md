---
title: "DeleteRelationships"
description: ""
summary: ""
date: 2024-04-12T14:00:33-04:00
lastmod: 2024-04-12T14:00:33-04:00
draft: false
weight: 60
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Atomically bulk deletes all relationships matching the provided filters, with optional preconditions.

**Parameters**

- `resourceFilter` - The filter to apply to the resource part of the relationships. The resourceFilter.Type is required; all other fields are optional.
- `optionalSubjectFilter` (optional) - An optional additional filter for the subject part of the relationships.
- `optionalPreconditions` (optional) - An optional list of preconditions that must be satisfied for the operation to commit.
- `deadline` (optional) - An optional deadline for the call. The operation will be cancelled if the deadline is reached.
- `cancellationToken` (optional) - An optional token for cancelling the call.

**Returns**

- A task representing the asynchronous operation, with a `ZedToken?` indicating the version of the data after the delete operation.

## Example

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var resourceFilter = new RelationshipFilter { Type = "document", OptionalId = "firstdoc" };

// Atomically delete all relationships matching the provided filter.
var resultToken = await client.DeleteRelationshipsAsync(resourceFilter);
Console.WriteLine($"Delete operation token: {resultToken?.Token}");
```