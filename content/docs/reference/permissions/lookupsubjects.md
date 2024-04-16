---
title: "LookupSubjects"
description: ""
summary: ""
date: 2024-04-12T14:02:04-04:00
lastmod: 2024-04-12T14:02:04-04:00
draft: false
weight: 120
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
Returns all the subjects of a given type that have access, whether via a computed permission or relation membership.

**Parameters**

- `resource` - Resource is the resource for which all matching subjects for the permission or relation will be returned.
- `permission` - Permission is the name of the permission (or relation) for which to find the subjects.
- `subjectType` - SubjectType is the type of subject object for which the IDs will be returned.
- `optionalSubjectRelation` (optional) - OptionalSubjectRelation is the optional relation for the subject.
- `context` (optional) - Context consists of named values that are injected into the caveat evaluation context.
- `zedToken` (optional) - An optional ZedToken for specifying a version of the data to consider.
- `cacheFreshness` (optional) - Specifies the acceptable freshness of the data to be considered from the cache.

**Returns**

- An async enumerable of `LookupSubjectsResponse` objects representing the subjects with access to the specified resource.


## Example Code

```csharp
var client = new SpiceDbClient("your_token", "your_schema_prefix");
var resource = new ResourceReference("document", "firstdoc");

// Lookup all subjects that have the specified permission on the specified resource.
await foreach (var subject in client.LookupSubjects(resource, "reader", "user"))
{
    Console.WriteLine($"Subject ID: {subject.Subject.Id}");
}
```