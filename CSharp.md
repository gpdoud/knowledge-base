# C#

## Manually a json config file in program

```csharp
        static void Main(string[] args) {

            var config = new ConfigurationBuilder()
                                .SetBasePath(Directory.GetCurrentDirectory())
                                .AddJsonFile("Appsettings.json", optional: true, reloadOnChange: true)
                                .Build();
            var json = config.GetSection("NLog")["autoReload"];
        }
```
