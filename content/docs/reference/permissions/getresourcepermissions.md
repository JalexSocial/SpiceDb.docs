---
title: "GetResourcePermissions"
description: ""
summary: ""
date: 2024-04-12T14:01:19-04:00
lastmod: 2024-04-12T14:01:19-04:00
draft: false
weight: 80
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Retrieves the list of permissions for a specified resource, permission, and subject.

**Parameters**

- `resourceType` - The type of the resource.
- `permission` - The name of the permission.
- `subject` - The subject for which permissions are being checked.
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to consider.
- `cacheFreshness` (optional) - Specifies the acceptable freshness of the data to be considered from the cache.

**Returns**

- A task representing the asynchronous operation, with a list of string indicating the permissions for the specified resource.

## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var subject = new ResourceReference("user", "bob");

// Retrieves the permissions associated with a specific resource and subject.
var permissions = await client.GetResourcePermissionsAsync("document", "reader", subject);
foreach (var perm in permissions)
{
    Console.WriteLine($"Permission: {perm}");
}
```