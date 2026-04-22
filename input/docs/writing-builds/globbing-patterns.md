---
Order: 50
Title: Globbing Patterns
Description: Documentation for the supported globbing syntax in Cake.
---

# Globbing Patterns

Cake provides a powerful, built-in file system globbing engine that allows you to easily find files and directories using wildcard patterns. The globber is heavily utilized across many common Cake aliases like `GetFiles()`, `GetDirectories()`, `CopyFiles()`, and `CleanDirectories()`.

## Supported Syntax

The Cake globber supports the following wildcard patterns for matching file and directory paths:

| Pattern | Description | Example |
| :--- | :--- | :--- |
| `*` | Matches zero or more characters within a single file or directory name. | `*.cs` matches `Program.cs` and `Test.cs`.<br>`src/*/bin` matches `src/ProjectA/bin`. |
| `**` | Matches zero or more directories recursively across directory boundaries. | `src/**/*.cs` matches any `.cs` file located anywhere under the `src/` directory tree. |
| `?` | Matches exactly one character within a file or directory name. | `Test?.cs` matches `Test1.cs` and `TestA.cs`, but not `Test12.cs`. |

## Common Examples

### 1. Finding all files with a specific extension
To recursively find all C# source files anywhere in your repository:
```csharp
var sourceFiles = GetFiles("./**/*.cs");
2. Finding files in a specific directory level
To find all text files located directly inside the docs folder (without searching subdirectories):

C#
var docFiles = GetFiles("./docs/*.txt");
3. Finding specific directories
To find all bin output folders across multiple projects in a solution:

C#
var binDirectories = GetDirectories("./src/**/bin");
Important Behaviors & Settings
Path Separators: Cake automatically normalizes directory separators for you. It is highly recommended to always use forward slashes (/) in your glob patterns, which will work seamlessly across Windows, Linux, and macOS.

Case Sensitivity: By default, the case sensitivity of the globber matches the behavior of the underlying operating system (case-insensitive on Windows, case-sensitive on Linux). You can override this explicitly by passing GlobberSettings:

C#
var files = GetFiles("./**/*.CS", new GlobberSettings {
    IsCaseSensitive = false
});
