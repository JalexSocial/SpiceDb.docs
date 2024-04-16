---
title: "ImportRelationships"
description: ""
summary: ""
date: 2024-04-12T14:01:45-04:00
lastmod: 2024-04-12T14:01:45-04:00
draft: false
weight: 100
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Imports relationships into SpiceDB from a specified file.

**Parameters**

- `filePath` - The path to the file containing the relationships to import.

**Returns**

- A task representing the asynchronous operation, with a `ZedToken?` indicating the version of the data after the import operation.