---
title: "CheckPermission"
description: ""
summary: ""
date: 2024-04-12T14:00:19-04:00
lastmod: 2024-04-12T14:00:19-04:00
draft: false
weight: 40
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Checks permissions for a given resource and subject, optionally considering additional context.

**Parameters**

- `permission` - The permission relationship to evaluate.
- `context` (optional) - An optional dictionary providing additional context information for evaluating caveats.
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to consider.
- `cacheFreshness` (optional) - Specifies the acceptable freshness of the data to be considered from the cache.

**Returns**

- A task representing the asynchronous operation, with a `PermissionResponse` indicating the result of the permission check.

## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var permission = new Permission("document:firstdoc", "reader", "user:bob");

// Check if the specified subject has the specified permission on the resource.
var response = await client.CheckPermissionAsync(permission);
Console.WriteLine($"User has permission: {response.HasPermission}");
```

