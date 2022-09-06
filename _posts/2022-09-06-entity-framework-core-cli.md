---
layout: post
title:  "Entity Framework Core Command Line Interface"
date:   2022-09-06 12:07:34 +0100
categories: DotNet EntityFramework Migrations Reference PowerShell
---

# .NET Core Entity Framework Command Line Reference

## Installing Entity command line
The .NET Entity Framework command line tools can be installed globally in PowerShell, or just for a specific project.
```
dotnet tool install --global dotnet-ef
```

After installation, it might be a good idea to update the tools:
```
dotnet tool update --global dotnet-ef
```


## Add the Entity Framework Packages to a Project
In order to use the Entity Framework command line tools for a .NET Core project, it's necessary to install the Design package. This could be done using the EF Core CLI or the NuGet Package Manager.

```
dotnet add package Microsoft.EntityFrameworkCore.Design
```

I also recommend ensuring the following packages are also installed:
- Microsoft.EntityFrameworkCore 
- Microsoft.EntityFrameworkCore.SqlServer 
- Microsoft.EntityFrameworkCore.Tools 


## Scaffolding DbContext
To generate the migrations, Entity Framework will require the project to have a DbContext. If there isn't one present (there should be), this can be scaffolded from whatever connection string(s) might exist in the configuration file. For this, it might be necessary to define the connection string and the provider.

```
dotnet ef dbcontext scaffold [Connection String] [Microsoft.EntityFrameworkCore.SqlServer] -o Models
```

This should create the DbContext and place the model *.cs* files in the Models directory.


## Generate a SQL script from the DbContext
```
dotnet ef dbcontext script
```

## Add a migration for the project
```
dotnet ef migrations add [Name]
```


## Generate a SQL script for the latest migration
```
dotnet ef migrations script
```


## Create a bundle/executable to update the database
```
dotnet ef migrations bundle
```
