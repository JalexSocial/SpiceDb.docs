---
title: "Watch"
description: ""
summary: ""
date: 2024-04-12T14:02:28-04:00
lastmod: 2024-04-12T14:02:28-04:00
draft: false
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Listens for changes to specified subjects and returns updates as they occur.

**Parameters**

- `optionalSubjectTypes` (optional) - A list of subject types to watch for changes.
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to watch.
- `deadline` (optional) - An optional deadline for the call. The operation will be cancelled if the deadline is reached.
- `cancellationToken` (optional) - An optional token for cancelling the call.

**Returns**

- An async enumerable of `WatchResponse` objects representing the updates to the watched subjects.