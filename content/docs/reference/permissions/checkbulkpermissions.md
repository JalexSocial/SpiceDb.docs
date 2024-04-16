---
title: "CheckBulkPermissions"
description: ""
summary: ""
date: 2024-04-12T14:00:09-04:00
lastmod: 2024-04-12T14:00:09-04:00
draft: false
weight: 30
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

### CheckBulkPermissionAsync (IEnumerable<string> permissions)

Checks multiple permissions in bulk for a specified list of permission identifiers.

**Parameters**

- `permissions` - An enumerable of permission identifiers to check.

**Returns**

- A task representing the asynchronous operation, with a `CheckBulkPermissionsResponse?` indicating the results of the bulk permission checks.

### CheckBulkPermissionAsync (IEnumerable<Permission> permissions)

Checks multiple permissions in bulk for a specified list of `Permission` objects.

**Parameters**

- `permissions` - An enumerable of `Permission` objects to check.

**Returns**

- A task representing the asynchronous operation, with a `CheckBulkPermissionsResponse?` indicating the results of the bulk permission checks.

### CheckBulkPermissionAsync (IEnumerable<CheckBulkPermissionsRequestItem> items)

Checks multiple permissions in bulk for a specified list of `CheckBulkPermissionsRequestItem` objects.

**Parameters**

- `items` - An enumerable of `CheckBulkPermissionsRequestItem` objects to check.

**Returns**

- A task representing the asynchronous operation, with a `CheckBulkPermissionsResponse?` indicating the results of the bulk permission checks.
