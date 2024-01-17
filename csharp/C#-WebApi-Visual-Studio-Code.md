# C# WebApi in Visual Studio Code

This info comes from: [Tutorial: Create a web API with ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-7.0&tabs=visual-studio-code)

[Publish to Azure](https://learn.microsoft.com/en-us/aspnet/core/tutorials/publish-to-azure-api-management-using-vs?view=aspnetcore-7.0)

Since Microsoft has dropped support for Visual Studio for MAC, Visual Studio Code will be the IDE used on a MAC.

Create the project. It would create a new folder with the name of the project which follows after the `-o` parameter. Add the NuGet packages for SqlServer support and startup VSC.

    dotnet new webapi -o TodoApi
    cd TodoApi
    dotnet add package Microsoft.EntityFrameworkCore.Tools
    dotnet add package Microsoft.EntityFrameworkCore.SqlServer
    code .

Create a dev certificate to test https (if exists). There will be a dialog asking to install the certificate. Answer 'yes'.

    dotnet dev-certs https --trust

Run the project using https:

    dotnet run --launch-profile https

Create a `Models` folder and a model within. Then create the AppDbContext in the `Models` folder.

    using Microsoft.EntityFrameworkCore;
    namespace xxx.Models;
    public class AppDbContext : DbContext {

        public DbSet<xxx> xxxs { get; set; }

        public AppDbContext(DbContextOptions<AppDbcontext> options)
            :base(options) {}

    }

Register the DbContext.

    // -- appsettings.json ---------------------------------
    "ConnectionStrings": {
        "DevDb": "server=localhost\sqlexpress;"
                    + "database=AppDb;"
                    + "trusted_connection=true;"
                    + "trustServerCertificate=true;"
    }
    // -- Program.cs --------------------------------------
    builder.Services.AddDbContext<AppDbContext>(x =>
        x.UseSqlServer(builder.Configuration.GetConnectionString("DevDb"))
    );

Install and upgrade the NuGet packages the generating controllers

    dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design -v 7.0.0
    dotnet add package Microsoft.EntityFrameworkCore.Design -v 7.0.0
    dotnet add package Microsoft.EntityFrameworkCore.SqlServer -v 7.0.0
    dotnet tool uninstall -g dotnet-aspnet-codegenerator
    dotnet tool install -g dotnet-aspnet-codegenerator
    dotnet tool update -g dotnet-aspnet-codegenerator

Scaffold (generate code) a controller

    dotnet aspnet-codegenerator controller -name TodoItemsController -async -api -m [MODEL] -dc AppDbContext -outDir Controllers