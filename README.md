# A curated list of .NET Libraries

This repository contains a curated list of modern, open-source .NET libraries which are of general use, particularly in the context of an ASP.NET Core web application.

Each section lists a recommended library or libraries, optionally followed by one or more good alternatives.

# Table of Contents

- [Background Jobs](#background-jobs)
- [Caching](#caching)
- [Compile-time Dependency Injection](#compile-time-dependency-injection)
- [Console Applications](#console-applications)
- [Email Templating](#email-templating)
- [Encryption](#encryption)
- [ETL](#etl)
- [Event/Message Bus](#eventmessage-bus)
- [File Storage](#file-storage)
- [GUI Applications](#gui-applications)
- [Logging](#logging)
- [Markdown to HTML](#markdown-to-html)
- [Mediator Pattern](#mediator-pattern)
- [ORM and Database Access](#orm-and-database-access)
- [PDF Generation](#pdf-generation)
- [Reverse Proxy/API Gateway](#reverse-proxyapi-gateway)
- [Testing](#testing)
- [Workflows](#workflows)

# Background Jobs

### Recommended

Hangfire is a mature and powerful background job manager which requires minimal setup. Using Redis rather than a SQL database as the backing storage improves throughput. The official Redis support requires a paid 'pro' license, but the open-source StackExchange.Hangfire.Redis repo provides a free alternative.

- Hangfire ([Homepage](https://www.hangfire.io/) | [Github](https://github.com/HangfireIO/Hangfire))
- StackExchange.Hangfire.Redis ([Github](https://github.com/marcoCasamento/Hangfire.Redis.StackExchange))

### Alternatives

- Quartz.NET ([Homepage](https://www.quartz-scheduler.net/) | [GitHub](https://github.com/quartznet/quartznet))

# Caching

Since ASP.NET Core applications run in a persistent process, non-distributed caching can be implemented without external infrastructure dependencies. Bitfaster.Caching offers a good set of features and high performance. CacheTower offers a multi-layered caching system, which could be useful if caching large amounts of expensive queries which do not fit easily in memory.

### Recommended

- Bitfaster.Caching ([GitHub](https://github.com/bitfaster/BitFaster.Caching))
- CacheTower ([GitHub](https://github.com/TurnerSoftware/CacheTower))

### Alternatives

For a distributed Redis cache, one can use StackExchange.Redis together with the Microsoft.Extensions.Caching.StackExchangeRedis `IDistributedCache` implementation (see [here](https://docs.microsoft.com/en-us/aspnet/core/performance/caching/distributed?view=aspnetcore-6.0)).

- StackExchange.Redis ([GitHub](https://github.com/StackExchange/StackExchange.Redis))

# Compile-time Dependency Injection

ASP.NET Core has built-in [dependency injection feature](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-6.0) which is sufficient for most use-cases. However, the following source generator libraries promise increased performance.

Sadly, owing to the design of ASP.NET Core, it is not yet possible to fully integrate compile-time libraries and thereby fully replace the built-in runtime dependency injection mechanics:

### Recommended

- Jab ([GitHub](https://github.com/pakrym/jab))

### Alternatives

- StrongInject ([StrongInject](https://github.com/YairHalberstadt/stronginject))

# Console Applications

### Recommended

- ConsoleAppFramework ([GitHub](https://github.com/Cysharp/ConsoleAppFramework))

### Alternatives

System.CommandLine is sufficient for very simple scenarios.

- System.CommandLine ([GitHub](https://github.com/dotnet/command-line-api))

# Email Templating

Scriban is a high-performance templating engine which can used not only for email templating, but many other purposes besides. Fluid claims to be even faster than Scriban.

- Scriban ([GitHub](https://github.com/scriban/scriban))
- Fluid ([GitHub](https://github.com/sebastienros/fluid))

# Encryption

### Recommended

- Encrypt We Must ([GitHub](https://github.com/ffMathy/FluffySpoon.AspNet.EncryptWeMust))

# ETL

### Recommended

- Transformalize ([GitHub](https://github.com/dalenewman/Transformalize))

# Event/Message Bus

CAP supports the transactional outbox pattern, which can be helpful for reliability. MessagePipe is by Cysharp, who is famous for high-performance libraries. Rebus has been around for a long time and is battle-tested and well-documented.

### Recommended

- CAP ([Homepage](https://cap.dotnetcore.xyz/) | [GitHub](https://github.com/dotnetcore/CAP/))
- MessagePipe ([GitHub](https://github.com/Cysharp/MessagePipe))

### Alternatives

- Rebus ([Homepage](https://rebus.fm/) | [GitHub](https://github.com/rebus-org/Rebus))
- MassTransit ([Homepage](https://masstransit.io/)) | [GitHub](https://github.com/MassTransit/MassTransit))

# File Storage

### Recommended

FluentStorage is an abstraction for blob storage across multiple cloud providers (and local files). It is well-documented.

- FluentStorage ([GitHub](https://github.com/robinrodricks/FluentStorage))

# GUI applications

### Recommended

- Avalonia ([Homepage](https://avaloniaui.net/) | [GitHub](https://github.com/AvaloniaUI/Avalonia))

# Logging

### Recommended

- ZLogger ([GitHub](https://github.com/Cysharp/ZLogger))

### Alternatives

- gelf-extensions-logging ([GitHub](https://github.com/mattwcole/gelf-extensions-logging))

# Markdown to HTML

- Markdig ([GitHub](https://github.com/xoofx/markdig))

# Mediator pattern

### Recommended

- Mediator (source generator) ([GitHub](https://github.com/martinothamar/Mediator))

### Alternatives

- MediatR ([GitHub](https://github.com/jbogard/MediatR))

# ORM and Database Access

### Recommended

Entity Framework is an incredibly powerful ORM which provides advanced, strongly-typed querying capabilities, good performance - particularly since a host of improvements were made in EF Core 6 - and inbuilt support for the [unit of work](https://martinfowler.com/eaaCatalog/unitOfWork.html) pattern. EFCore.BulkExtensions can be used to improve performance when dealing with bulk CUD operations, the impact of which becomes noticeable when dealing with operations on 100s or 1000s of entities. If a second-level cache is required, EF Core Second Level Cache Interceptor can be used.

In advanced scenarios, when more than one database transaction may be required per web request, the DbContextScope library is useful. This allows for more fine-grained control over the lifetime of the DbContext than simply injecting the DbContext as a scoped dependency. For more information, see Mehdi El Gueddari's 2014 article [here](https://mehdi.me/ambient-dbcontext-in-ef6/).

To allow for primary keys that can be generated in application code and can be more efficiently sorted than standard GUIDs (particularly in databases which do not support non-clustered primary keys), consider [ULIDs](https://sudhir.io/uuids-ulids) or [COMB GUIDs](https://jim.blacksweb.com/2017/01/23/comb-guid-what-is-it-and-why-should-i-use-it/).

- Entity Framework Core ([GitHub](https://github.com/dotnet/efcore))
- EFCore.BulkExtensions ([Homepage](https://codis.tech/efcorebulk/) | [GitHub](https://github.com/borisdj/EFCore.BulkExtensions)) (**NB: PAID license**)
- EF Core Second Level Cache Interceptor ([GitHub](https://github.com/VahidN/EFCoreSecondLevelCacheInterceptor))
- DbContextScopeEFCore ([GitHub](https://github.com/zejji/DbContextScopeEFCore))
- Cysharp/Ulid ([GitHub](https://github.com/Cysharp/Ulid))
- RT.Comb ([GitHub](https://github.com/richardtallent/RT.Comb))

### Alternatives

The following are lighter-weight alternatives which do not offer the full functionality of Entity Framework Core:

- RepoDb ([Homepage](https://repodb.net/) | [GitHub](https://github.com/mikependon/RepoDB))
- linq2db ([GitHub](https://github.com/linq2db/linq2db))

Marten is a powerful library which allows PostgreSQL to be used as a hybrid/NoSQL database:

- Marten ([Homepage](https://martendb.io/) | [GitHub](https://github.com/JasperFx/marten))

### 

# PDF generation

There aren't many PDF generators that don't rely on headless browser rendering of HTML (regardless of programming language; cf. e.g. [mpdf](https://github.com/mpdf/mpdf) in PHP, although the source code looks hard-to-maintain). However, the non-browser approach yields much better performance. QuestPDF is one such library on .NET. 

### Recommended

- QuestPDF ([Homepage](https://www.questpdf.com/) | [GitHub](https://github.com/QuestPDF/QuestPDF)) (**NB: PAID license**)

# Reverse Proxy/API Gateway

### Recommended

- yarp ([Homepage](https://microsoft.github.io/reverse-proxy/) | [GitHub](https://github.com/microsoft/reverse-proxy))

# Testing

### Recommended

A good combination of libraries for implementing tests is xUnit as the test framework, NSubstitute for test doubles, Bogus for the generation of fake data and FluentAssertions for assertions.

- xUnit ([Homepage](https://xunit.net/) | [GitHub](https://github.com/xunit/xunit))
- NSubstitute ([Homepage](https://nsubstitute.github.io/) | [GitHub](https://nsubstitute.github.io/))
- Bogus ([GitHub](https://github.com/bchavez/Bogus))
- FluentAssertions ([Homepage](https://fluentassertions.com/) | [GitHub](https://github.com/fluentassertions/fluentassertions))

### Alternatives

- Shouldly ([Homepage](https://shouldly.io/) | [GitHub](https://github.com/shouldly/shouldly))

# Workflows

### Recommended

- ELSA ([Homepage](https://elsa-workflows.github.io/elsa-core/) | [GitHub](https://github.com/elsa-workflows))
