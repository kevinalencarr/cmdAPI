# What this is

This a minimal API built with .NET 6, designed with repository & DTO pattern to store command lines. This is what it looks like when you run its HTTPS requests:

![Sem título](https://user-images.githubusercontent.com/90851371/178108064-1caf334d-55f9-4236-b8e3-ce04c880c261.png)

Credits for the project's idea go to Les Jackson.

# Steps taken

### 1. Install necessary packages
- Microsoft.EntityFrameworkCore
- Microsoft.EntityFrameworkCore.Design
- AutoMapper.Extensions.Microsoft.DependencyInjection

### 2. Configure Docker

We used docker-compose.yaml to create a Docker containner and establish connection with SQL Server.

### 3. Create Model

Only one Model required, with four properties, in this case. Only Id marked as [Key], auto-generated by our database, while the rest are marked as [Required].

### 4. Create DTOs

Three DTOs were made, for Create, Read and Update. Delete should be not necessary.

### 5. Configure DbContext

Entity Framework comes in play to create our DbContext. While Connection String goes into appsettings.Development.json file, note that UserId and Password are stored with user-secrets. DbContext is later injected into our Program.cs file.

### 6. Migrate

EF once again used, now to migrate the code into our database:
- dotnet ef migrations add InitialMigration
- dotnet ef database update

### 7. Create repositories

An interface was used to establish our methods, including SaveChangesAsync(), later inherited by CommandRepo file.

### 8. Create profiles for auto-mapping

Because we are using AutoMapper, a profile (inherited from Profile base AutoMapper class) must be made, defining our sources and targets.

### 9. Go for endpoints

Once base code is done, we are ready to create our endpoints. app.MapGet, app.MapPost, app.MapPut and app.MapDelete should now be able to do all the work with HTTPS requests.

# Tools used

- Visual Studio Code, as main IDE
- Insomnia, to test HTTPS request
- Entity Framework, to migrate our code to database
- SQL Server, to manage our database
- Docker, to establish connection with SQL Server
