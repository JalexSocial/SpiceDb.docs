---
title: "LookupResources"
description: ""
summary: ""
date: 2024-04-12T14:01:56-04:00
lastmod: 2024-04-12T14:01:56-04:00
draft: false
weight: 110
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Returns all the resources of a given type that a subject can access, whether via a computed permission or relation membership.

**Parameters**

- `resourceType` - The type of resource object for which the IDs will be returned.
- `permission` - The name of the permission or relation for which the subject must check.
- `subject` - The subject with access to the resources.
- `context` (optional) - Dictionary of values that are injected into the caveat evaluation context.
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to consider.
- `cacheFreshness` (optional) - Specifies the acceptable freshness of the data to be considered from the cache.

**Returns**

- An async enumerable of `LookupResourcesResponse` objects representing the resources accessible to the specified subject.


## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var subject = new ResourceReference("user", "bob");

// Lookup all resources of a given type that the specified subject can access.
await foreach (var resource in client.LookupResources("document", "reader", subject))
{
    Console.WriteLine($"Resource ID: {resource.ResourceId}");
}
```