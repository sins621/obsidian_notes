# Creating an API Project

A bare-bones Dotnet Application is composed of a few key components:

- The .csproj File
- Program.cs
- appsettings.json
- appsettings.Development.json
- Properties Directory
- obj Directory
## .csproj File

This is the project file, containing configuration information for the .NET build system including:

- Framework Target
- Dependencies
- Build Options
- Output Configuration
- Runtime Identifiers
- SDK Definition
- Versioning
- Environment-Specific Configurations
- Custom Target and Tasks

The format is XML (eXtensible Markup Language) and defines the project's structure, helping the .NET CLI manage the project.
### Framework Target
`<TargetFramework>`

This specifies which .NET framework version(s) the project targets, such as `.NET 6`, `.NET Core 3.1` or `.NET Framework 4.8`, etc. This defines compatibility with the .NET runtime and libraries

```xml
<TargetFramework>net8.0</TargetFramework>
```
### Dependencies
`<PackageReference>` and `<ProjectReference>`

Lists external libraries or NuGet (.NET Package Manager) packages the project depends on. This includes everything from Microsoft packages (e.g., `Microsoft.EntityFrameworkCore`) to third-party libraries. `PackageReference` defines package dependencies, and `ProjectReference` allows referencing other projects within the solution

```xml
<ItemGroup>
	<PackageReference Include="Newtonsoft.Json" Version="13.0.1" />
	<ProjectReference Include="..\OtherProject\OtherProject.csproj" />
</ItemGroup>
```
### Build Options

Configures how the project is build. Common build options include:

- DefineConstants: Defines conditional compilation symbols for the project.
- Optimize: Enables or disables optimization for release builds.
- Nullable: Enforces nullable reference types and warnings.

```xml
<PropertyGroup>
	<DefineConstants>DEBUG;TRACE</DefineConstants>
	<Optimize>true</Optimize>
	<Nullable>enable</Nullable>
</PropertyGroup>
```
#### DefineConstants:

This option allows you to set **conditional compilation symbols**, which can control which part of your code are compiled and executed based on the symbol's presence.

For example, you can use symbols like `DEBUG` or `RELEASE` to include or exclude code segments for different build configurations. In the code, you might see these symbols used with `#if`, `#else`, and `#endif` directives to enable certain blocks only when specific symbols are defined.

**Example:**
```cs
#if DEBUG
Console.WriteLine("Debugging mode:");
#endif
```
#### Optimize:

This option enables or disables optimizations applied by the compiler, primarily used in **release builds** to make the code run faster or take up less space. 

When `Optimize` is set to `true`, the compiler might:

- Remove unused variables and inline certain methods.

- Reorder or transform code to improve performance.

For development builds (`Optimize=false`), debugging is easier because the code structure stays closer to the source, but optimized builds (`Optimize=true`) generally run faster. It's often set to `true` for the `Release` configuration and `false` for the `Debug` configuration.
#### Nullable:

This option controls **nullable reference types** in C# 8.0 and later, allowing you to enable or disable nullability warnings. When nullable is **enabled**, the compiler gives warnings if there's a risk of null references, helping catch potential null reference exceptions (e.g., if a non-nullable reference type could be null).

It introduces two types of reference types:

- **Nullable reference types** (e.g., `string?`), which can hold `null`.
- **Non-nullable reference types** (e.g., `string`), which are not expected to hold null.

Setting `Nullable` to `enable` makes it easier to write null-safe code by enforcing explicit handling of nullable types.

**Example:**
```cs
string? name = null; // Nullable reference type
string address = null; // this will produce a warning if Nullable is enabled
```