# A curated list of .NET Libraries

This repository contains a curated list of modern, open-source .NET libraries which are of general use, particularly in the context of an ASP.NET Core web application.

Each section lists a recommended library or libraries, optionally followed by one or more good alternatives.

# Background Jobs

### Recommended

- Hangfire ([Homepage](https://www.hangfire.io/) | [Github](https://github.com/HangfireIO/Hangfire))
- StackExchange.Hangfire.Redis ([Github](https://github.com/marcoCasamento/Hangfire.Redis.StackExchange))

# Caching

### Recommended

- Bitfaster.Caching ([GitHub](https://github.com/bitfaster/BitFaster.Caching))

# Compile-time Dependency Injection

ASP.NET Core has built-in [dependency injection feature](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-6.0) which is sufficient for most use-cases. However, the following source generator libraries promise increased performance:

### Recommended

- Jab ([GitHub](https://github.com/pakrym/jab))

### Alternatives

- StrongInject ([StrongInject](https://github.com/YairHalberstadt/stronginject))

# Email Templating

Scriban is a highly-performance templating engine which can used not only for email templating, but many other purposes besides.

- Scriban ([GitHub](https://github.com/scriban/scriban))

# Encryption

### Recommended

- Encrypt We Must ([GitHub](https://github.com/ffMathy/FluffySpoon.AspNet.EncryptWeMust))

# ETL

### Recommended

- Transformalize ([GitHub](https://github.com/dalenewman/Transformalize))

# Event/Message Bus

### Recommended

- CAP ([Homepage](https://cap.dotnetcore.xyz/) | [GitHub](https://github.com/dotnetcore/CAP/))

### Alternatives

- Rebus ([Homepage](https://rebus.fm/) | [GitHub](https://github.com/rebus-org/Rebus))

# GUI applications

### Recommended

- Avalonia ([Homepage](https://avaloniaui.net/) | [GitHub](https://github.com/AvaloniaUI/Avalonia))

# Logging

### Recommended

- ZLogger ([GitHub](https://github.com/Cysharp/ZLogger))

# Mediator pattern

### Recommended

- Mediator (source generator) ([GitHub](https://github.com/martinothamar/Mediator))

### Alternatives

- MediatR ([GitHub](https://github.com/jbogard/MediatR))

# ORM and Database Access

### Recommended

- Entity Framework Core ([GitHub](https://github.com/dotnet/efcore))
- EFCore.BulkExtensions ([GitHub](https://github.com/borisdj/EFCore.BulkExtensions/blob/master/README.md))
- EF Core Second Level Cache Interceptor ([GitHub](https://github.com/VahidN/EFCoreSecondLevelCacheInterceptor))

### Alternatives

The following are lighter-weight alternatives which do not offer the full functionality of Entity Framework Core:

- RepoDb ([Homepage](https://repodb.net/) | [GitHub](https://github.com/mikependon/RepoDB))
- linq2db ([GitHub](https://github.com/linq2db/linq2db))

Marten is a powerful library which allows PostgreSQL to be used a hybrid/NoSQL database:

- Marten ([Homepage](https://martendb.io/) | [GitHub](https://github.com/JasperFx/marten))

### 

# PDF generation

### Recommended

- QuestPDF ([Homepage](https://www.questpdf.com/) | [GitHub](https://github.com/QuestPDF/QuestPDF))

# Testing

### Recommended

- Bogus ([GitHub](https://github.com/bchavez/Bogus))
- FluentAssertions ([Homepage](https://fluentassertions.com/) | [GitHub](https://github.com/fluentassertions/fluentassertions))

### Alternatives

- Shouldly ([Homepage](https://shouldly.io/) | [GitHub](https://github.com/shouldly/shouldly))

# Workflows

### Recommended

- ELSA ([Homepage](https://elsa-workflows.github.io/elsa-core/) | [GitHub](https://github.com/elsa-workflows))
