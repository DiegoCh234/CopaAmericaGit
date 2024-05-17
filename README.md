Paso 01: Instalar paquetes
* Install-Package Microsoft.EntityFrameworkCore
* Install-Package Microsoft.EntityFrameworkCore.SqlServer
* Install-Package Microsoft.EntityFrameworkCore.Tools
Paso 02: Scaffold

Con Crendeciales SQL
------------------------
 Scaffold-DBContext "Server=WS2302347;Database=PeruDB;User=;Pwd=;TrustServerCertificate=True" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Data -Force -nopluralize

Con autenticación windows
-------------------------
 Scaffold-DBContext "Server=WS2302347;Database=PeruDB;Integrated Security=true;TrustServerCertificate=True" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Data -Force -nopluralize

Pase 03: Add CNX al appSettings.json
,
  "ConnectionStrings": {
    "DevConnection": "Server=WS2302347;Database=PeruDB;Integrated Security=true;TrustServerCertificate=True"
  }


Paso 04: CNX en Program.cs

// Add services to the container.
var _config = builder.Configuration;
var cnx = _config.GetConnectionString("DevConnection");
builder.Services
    .AddDbContext<PeruDbContext>
    (options => options.UseSqlServer(cnx));






