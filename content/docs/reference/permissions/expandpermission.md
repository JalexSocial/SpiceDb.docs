---
title: "ExpandPermission"
description: ""
summary: ""
date: 2024-04-12T14:01:07-04:00
lastmod: 2024-04-12T14:01:07-04:00
draft: false
weight: 70
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Expands the permission tree for a resource's permission or relation, revealing the graph structure. This method may require multiple calls to fully unnest a deeply nested graph.

**Parameters**

- `resource` - The resource reference for which to expand the permission tree.
- `permission` - The name of the permission or relation to expand.
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to consider.
- `cacheFreshness` (optional) - Specifies the acceptable freshness of the data to be considered from the cache.

## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var resource = new ResourceReference("document", "firstdoc");

// Expands the permission tree for the specified permission on the specified resource.
var response = await client.ExpandPermissionAsync(resource, "reader");
Console.WriteLine($"Permission expanded at token: {response?.ExpandedAt.Token}");
```