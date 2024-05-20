---
title: "ReadRelationships"
description: ""
summary: ""
date: 2024-04-12T14:02:13-04:00
lastmod: 2024-04-12T14:02:13-04:00
draft: false
weight: 130
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Asynchronously reads a set of relationships matching one or more filters.

**Parameters**

- `resource` - The filter to apply to the resource part of the relationships.
- `subject` (optional) - An optional filter to apply to the subject part of the relationships.
- `excludePrefix` (optional) - Indicates whether the prefix should be excluded from the response.
- `limit` (optional) If non-zero, specifies the limit on the number of relationships to return before the stream is closed on the server side. By default, the stream will continue resolving relationships until exhausted or the stream is closed due to the client or a network issue.</param>
- `cursor` (optional) If provided indicates the cursor after which results should resume being returned. The cursor can be found on the ReadRelationshipsResponse object.</param>
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to read.
- `cacheFreshness` (optional) - Specifies the acceptable freshness of the data to be read from the cache.

**Returns**

- An async enumerable of `ReadRelationshipsResponse` objects matching the specified filters.


## Example

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var resourceFilter = new RelationshipFilter { Type = "document" };
var subjectFilter = new SubjectFilter { Type = "user" };

// Asynchronously retrieve relationships that match the specified filters.
await foreach (var response in client.ReadRelationshipsAsync(resourceFilter, subjectFilter))
{
    Console.WriteLine($"Resource: {response.Relationship.Resource}");
    Console.WriteLine($"Relation: {response.Relationship.Relation}");
    Console.WriteLine($"Subject: {response.Relationship.Subject}");
}
```
