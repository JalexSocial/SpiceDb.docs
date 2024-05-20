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
- `allowPartialDeletions` (optional) - If true and a limit is specified, will delete matching found relationships up to the count specified in limit, and no more.
- `limit` (optional) if non-zero, specifies the limit on the number of relationships to be deleted. If there are more matching relationships found to be deleted than the limit specified here,
    the deletion call will fail with an error to prevent partial deletion. If partial deletion is needed, specify below that partial deletion is allowed. Partial deletions can be used
    in a loop to delete large amounts of relationships in a *non-transactional* manner.</param>
- `deadline` (optional) - An optional deadline for the call. The operation will be cancelled if the deadline is reached.
- `cancellationToken` (optional) - An optional token for cancelling the call.

**Returns**

- DeleteRelationshipsResponse object that contains a ZedToken representing the point of deletion and an indicator of deletion progress

## Example

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var resourceFilter = new RelationshipFilter { Type = "document", OptionalId = "firstdoc" };

// Atomically delete all relationships matching the provided filter.
var result = await client.DeleteRelationshipsAsync(resourceFilter);
Console.WriteLine($"Delete operation token: {resultToken?.DeletedAt.Token}");
```