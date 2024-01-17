```
  "ConnectionStrings": {
    "WinDb": "server=localhost\\sqlexpress;database=AocDb;trustServerCertificate=true;trusted_connection=true;",
    "MacDb": "server=localhost,1433;database=AocDb;uid=sa;pwd=p@ssw0rd1#",
    "ProdDb": "Data Source=tcp:s23.winhost.com;Initial Catalog=DB_133575_aocdb;User ID=DB_133575_aocdb_user;Password=aocuser27$;Integrated Security=False;"
  }

  services.AddDbContext<ServantDbContext>(x => {
    var connStrKey = "ProdDb"; // auto set if in Release mode
#if DEBUG
    connStrKey = Environment.GetEnvironmentVariable("VSOPSYS") != null ? "WinDb" : "MacDb";
#endif
    x.UseSqlServer(Configuration.GetConnectionString(connStrKey));


dotnet ef migrations add <name>
dotnet ef migrations remove

dotnet tool install --global dotnet-ef
dotnet tool update --global dotnet-ef

```