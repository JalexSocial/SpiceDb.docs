---
title: "ImportRelationships"
description: ""
summary: ""
date: 2024-04-12T14:01:39-04:00
lastmod: 2024-04-12T14:01:39-04:00
draft: false
weight: 90
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Imports relationships into SpiceDB from a provided string.

**Parameters**

- `content` - The relationships to import, provided as a string.

**Returns**

- A task representing the asynchronous operation, with a `ZedToken?` indicating the version of the data after the import operation.