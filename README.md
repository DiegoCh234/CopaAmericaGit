Paso 01: Instalar paquetes
* Install-Package Microsoft.EntityFrameworkCore
* Install-Package Microsoft.EntityFrameworkCore.SqlServer
* Install-Package Microsoft.EntityFrameworkCore.Tools
Paso 02: Scaffold

http: RECURSO
Con Crendeciales SQL
------------------------
 Scaffold-DBContext "Server=WS2302347;Database=PeruDB;User=;Pwd=;TrustServerCertificate=True" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Data -Force -nopluralize

Con autenticación windows
-------------------------
 Scaffold-DBContext "Server=WS2302347;Database=PeruDB;Integrated Security=true;TrustServerCertificate=True" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Data -Force -nopluralize

Pase 03: Add CNX al appSettings.json

Es una herramienta de prueba de API  /get
 ,
  "ConnectionStrings": {
    "DevConnection": "Server=WS2302347;Database=PeruDB;Integrated Security=true;TrustServerCertificate=True"
  }

datos que fluyen entre diversos sistemas operativos
con la minima intervencion humana / interop
Paso 04: CNX en Program.cs

// Add services to the container.
var _config = builder.Configuration;
var cnx = _config.GetConnectionString("DevConnection");
builder.Services
    .AddDbContext<PeruDbContext>
    (options => options.UseSqlServer(cnx));





// ¿Qué SI es .NET?
- Un entorno de ejecución administrado.
– Un conjunto de lenguajes de programación.
– Un conjunto de bibliotecas y clases reutilizables.

ASP.NET =
Modelo de desarrollo Web
unificado que incluye los servicios
necesarios para crear aplicaciones Web
empresariales con el código mínimo

API 

Es un conjunto de productos y servicios tecnológicos que permiten comunicarse a través de internet.




