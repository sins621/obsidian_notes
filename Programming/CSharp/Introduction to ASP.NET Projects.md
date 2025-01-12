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
- ImplicitUsings: Automatically includes commonly used namespaces.
- RootNamespace: Defines the default namespace for the project.

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
#### ImplicitUsings

This property, when set to `enable`, **automatically includes commonly used namespaces** in your project, so you don't have to manually `using` them at the top of each file. This feature is available in .NET 6 and later and helps reduce boilerplate code.

The specific namespaces included depend on the project type. For example:

- In a **Console app**, it might include `System`, `System.Collections.Generic`, `System.Linq`, etc.
- In an **ASP.NET Core web app**, it would include additional namespaces like `Microsoft.AspNetCore.Builder`, `Microsoft.Extensions.DependencyInjection`, and other commonly used in web development.

**Example:** Without ImplicitUsings:
```csharp
using System;
using System.Collections.Generic;
```

**Example:** With ImplicitUsings Enabled:
```csharp
// No need to manually include System or common namespaces; they are implicitly available.
```
#### RootNamespace:

This property defines the **default namespace for the project**. All files without a specified namespace will use this as their root. It also serves as the base namespace for any classes, structs, interfaces, etc., within the project. 

When you create a new class, it will use the root namespace (e.g., `Lesson_1_Creating_an_API_Project`) unless you specify a different one.

It helps ensure consistency across the project's naming conventions and simplifies the organization of classes.

**Example:**
If `RootNamespace` is set to `Lesson_1_Creating_an_API_Project` and you add a class in a `Models` folder, its full namespace would be `Lesson_1_Creating_an_API_Project.Models`.

```xml
<RootNamespace>Lesson_1_Creating_an_API_Project</RootNamespace>
```
### Output Configuration

- **Output Type:** Defines the type of application, such as `exe` for executables or `Libary` for class libraries.
- **AssemblyName:** Specifies the name of the output assembly.
- **OutputPath:** Defines the directory where build outputs will be placed.

```xml
<PropertyGroup>
	<OutputType>Exe</OutputType>
	<AssemblyName>MyApp</AssemblyName>
	<OutputPath>bin\Debug\net8.0\</OutputPath>
</PropertyGroup>
```
### Runtime Identifiers
`<RuntimeIdentifier>` and `<RuntimeIdentifiers>`

Specifies the Runtime environments the project targets, such as Windows, Linux, or macOS. This is especially relevant for self-contained deployments, where all dependencies are packaged with the app.

```xml
<RuntimeIdentifiers>win-x64;linux-x64</RuntimeIdentifers>
```
### SDK Definition
`<Project Sdk="">`

Defines the SDK used for project, such as the `Microsoft.NET.Sdk`, `Microsoft.NET.Sdk.Web` (for web apps), or `Microsoft.NET.Sdk.Worker` (for background services).

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
```
### Versioning:

- **Version:** Specifies the version number for the project, which is often used when creating NuGet packages.
- **AssemblyVersion** and **FileVersion:** These specify the assembly and file version numbers, which can be incremented for each release.

```xml
<PropertyGroup>
	<Version>1.0.0</Version>
	<AssemblyVersion>1.0.0.0</AssemblyVersion>
	<FileVersion>1.0.0.0</FileVersion>
</PropertyGroup>
```
### Environment-Specific Configurations

You can conditionally set properties or references for specific build configurations, such as `Debug` or `Release`, using conditional `PropertyGroup` blocks.

```xml
<PropertyGroup Condition = "'$(Configuration)'=='Release'">
	<Optimize>true</Optimize>
</PropertyGroup>
```
### Custom Targets and Tasks

Custom tasks or target elements can define specific actions, like copying files or cleaning directories, which are executed during the build process.

```xml
<Target Name="CustomTask" AfterTargets="Build">
	<Exec Command="echo Hello, world!" />
</Target>
```