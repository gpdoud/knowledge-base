# C#

## C# v9
    https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-9

### Record types
    * Immutable
    * Cannot be inherited or inherit a class
    * Equality
    * Formatted display
    * Positional syntax for property definition

```csharp
// abbreviated definition
public record Person(string FirstName, string LastName);

// Using init-only
public record Person {
    public string FirstName { get; init; }
    public string LastName { get; init; }
}

// Postional property definition
Person noah = new("Noah", "Phence");

// nondestrictive mutation
Person piket = noah with { FirstName = "Piket" };
```

### Init-only initializer
    * Once initialized, becomes readonly
### Top-level statements

```csharp

// program.cs
// No namespace, class, or Main method
using System;
Console.WriteLine("A top-level statement");
```

## Add a json config file in program

```csharp
    static void Main(string[] args) {
        var config = new ConfigurationBuilder()
                            .SetBasePath(Directory.GetCurrentDirectory())
                            .AddJsonFile("Appsettings.json", optional: true, reloadOnChange: true)
                            .Build();
        var json = config.GetSection("NLog")["autoReload"];
    }
```
