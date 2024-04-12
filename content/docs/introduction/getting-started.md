---
title: "Getting Started"
description: ""
summary: ""
date: 2024-02-05T12:07:02-05:00
lastmod: 2024-02-05T12:07:02-05:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "getting-started-b61c1d09773be2e6c7aa6e8dbfc38058"
weight: 999
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

This README provides instructions on how to incorporate the SpiceDb library into your .NET projects. 

## Requirements

- **.NET Version**: .NET 7 or newer.

## Installation

SpiceDb is available as a NuGet package. You can install it using the .NET CLI with the following command:

```sh
dotnet add package SpiceDb
```

For the latest version and more details, visit the [SpiceDb NuGet package page](https://www.nuget.org/packages/SpiceDb).

## Configuration

After installing SpiceDb, you need to create a client using the SpiceDb endpoint web address. 

```csharp

// Create a new client with a namespace prefix of "arch" for all defined objects

// Approach #1 - Uses default server address
var client = new SpiceDbClient("secret_token", "schemaprefix");  // defaults to server address of "https://grpc.authzed.com

// Approach #2 - Specifies server (must include http or https in address)
var client = new SpiceDbClient("http://127.0.0.1:50051", "secret_token", "schemaprefix");

// Approach #3 - Custom created Grpc ChannelBase for full control of the connection channel
var channel = GrpcChannel.ForAddress("http://127.0.0.1:50051");  // You can get as elaborate as you want
var client = new SpiceDbClient(channel, "schemaprefix");

```
