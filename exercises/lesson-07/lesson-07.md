# Lesson 07 exercises
## Configuration in ASP.NET Core
The purpose of this exercise is to extract configuration from an existing app and apply the Options pattern[^1] to create strongly typed access for configuration.

## Exercise 07-1
The first thing we need to do is to get a Docker container up and running:
1. Setup a Docker container running Microsoft SQL Server[^2] (get the image with `docker pull mcr.microsoft.com/mssql/server` if haven't got it already)
2. Choose a strong password and add that as the environment variable `SA_PASSWORD` when starting the container with the following command: `docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD={VeryStrongPasswordHere!}" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest`
3. Add the connection string as the environment variable

## Exercise 07-2
Create a `Contact` model class with the following properties:
- ID (`int`)
- FirstName (`string`)
- LastName (`string`)
- Email (`string`)
- Gender (`string`)

_Hint: See `examples/lesson-07-configuration/WebAPIConfiguration/Model/NetLog.cs` on how to map JSON to properties_

## Exercise 07-3
Setup a `DbContext` for `Contact`. Start by adding the necessary NuGet packages and then:
- Create a `ContactsContext` class with a `DbSet` named Contacts
- Register the `ContactsContext` class in `Program.cs`

## Exercise 07-4
Add the connection string[^4] to Secret Manager[^3]:
- Run `dotnet user-secrets init` in the project root directory
- Run `dotnet user-secrets set "ConnectionStrings:Contacts" "YourConnectionStringHere"`

_Hint: Use the connection string in `examples/lesson-07-configuration/WebAPIConfiguration/appsettings.json` as a start_

## Exercise 07-4


[^1]: https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/options
[^2]: https://hub.docker.com/_/microsoft-mssql-server
[^3]: https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets
[^4]: https://docs.microsoft.com/en-us/ef/core/miscellaneous/connection-strings