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

## Example Usage

```csharp
using Microsoft.Extensions.Configuration;
using SpiceDb.Example;
using SpiceDb.Example.MyObjects;
using SpiceDb.Models;

// This is just to keep the server address and token private
var builder = new ConfigurationBuilder()
    .AddUserSecrets(typeof(Secrets).Assembly)
    .AddEnvironmentVariables();
var configurationRoot = builder.Build();

var secrets = configurationRoot.GetSection("AuthZed").Get<Secrets>();

if (secrets is null)
    throw new ArgumentException("Invalid secrets configuration");

// var serverAddress = "https://grpc.authzed.com";
// Create a new client with a prefix of "arch" for all defined objects
var client = new SpiceDbClient(secrets.ServerAddress, secrets.Token, "arch");

// Add relationship where user:bob is a reader of document:firstdoc
// Note that because the schema prefix is set in the client it is not necessary to always prefix every resource definition 
client.AddRelationship("arch/document:firstdoc#reader@arch/user:bob");

// This also works
client.AddRelationship("document:firstdoc#reader@user:kevin");

// Second approach to adding relationships
client.AddRelationship(new Relationship("arch/document:firstdoc", "reader", "arch/user:jacob"));

// This approach uses a little syntactic sugar to define each of the relations
client.AddRelationship(ZedUser.WithId("carmella").CanRead(ZedDocument.WithId("firstdoc")));

// Check to see if user:bob is in fact now a reader of document:firstdoc
var bobCanRead = client.CheckPermission(new Permission("arch/document:firstdoc#reader@arch/user:bob"));

Console.WriteLine($"Can user bob read document:firstdoc? {bobCanRead.HasPermission}");
// true

// This is a similar check but without adding prefixes
var kevinCanRead = client.CheckPermission(new Permission("document:firstdoc#reader@user:bob"));

Console.WriteLine($"Can user kevin read document:firstdoc? {kevinCanRead.HasPermission}");
// true


// Check to see if user:carmella is in fact now a reader of document:firstdoc
var carmellaCanRead = client.CheckPermission(ZedUser.WithId("carmella").CanRead(ZedDocument.WithId("firstdoc")));

Console.WriteLine($"Can user carmella read document:firstdoc? {carmellaCanRead.HasPermission}");
// true
```


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
