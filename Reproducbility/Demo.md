# .NET reproducibility

- Create new console with the following CLI call : `dotnet new console -n ConsoleApp`
- Rename the folder `ConsoleApp` to `ConsoleApp2`
- Execute `dotnet new console -n ConsoleApp` again that will create a new folder
- Now build both of the projects
  - `dotnet build ConsoleApp\ConsoleApp.csproj`
  - `dotnet build ConsoleApp2\ConsoleApp.csproj`
- What will the output binaries look like? 
  - MacOSX/Linux: `diff ConsoleApp/bin/Debug/net8.0/ConsoleApp.dll ConsoleApp2/bin/Debug/net8.0/ConsoleApp.dll`
  - Windows: `fc ConsoleApp/bin/Debug/net8.0/ConsoleApp.dll ConsoleApp2/bin/Debug/net8.0/ConsoleApp.dll`
- Maybe you can decompile (e.g. JetBrains Rider) and look into what it looks like?
- Run string on the binaries and create text files to compare with e.g. VS Code or any other preferred tool
  - MacOSX/Linux:
    - `strings ConsoleApp/bin/Debug/net8.0/ConsoleApp.dll >> ConsoleAppStrings`
    - `strings ConsoleApp2/bin/Debug/net8.0/ConsoleApp.dll >> ConsoleApp2Strings`
  - Windows:
    - `more < ConsoleApp/bin/Debug/net8.0/ConsoleApp.dll | findstr "." >> ConsoleAppStrings`
    - `more < ConsoleApp2/bin/Debug/net8.0/ConsoleApp.dll | findstr "." >> ConsoleApp2Strings`
  - What are the differences? If you have VS Code on your machine consider doing the following:
    `code -r --diff ConsoleAppStrings ConsoleApp2Strings`
- Alter both `.csproj` files and add `<DebugType>None</DebugType>` to it.
- Build both projects and check the strings output again same way described above.
