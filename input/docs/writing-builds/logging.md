---
Order: 60
Title: Logging
Description: Documentation for using Cake's built-in logging functionality.
---

# Logging

Cake provides a robust, built-in logging system that allows you to output messages to the console during your build process. This is incredibly useful for debugging, tracking build progress, and surfacing important warnings or errors.

## Logging Aliases

Cake exposes several global aliases for logging. These correspond directly to the different severity levels of the messages you want to output.

| Alias | Description | Example |
| :--- | :--- | :--- |
| `Information` | Standard output for general build progress. | `Information("Cleaning directories...");` |
| `Warning` | Highlights potential issues that do not stop the build. | `Warning("Missing configuration file, using defaults.");` |
| `Error` | Outputs a red error message. Does *not* stop the build script automatically. | `Error("Failed to copy assets.");` |
| `Verbose` | Detailed output. Only visible if verbosity is set to Verbose or higher. | `Verbose("Discovered 45 files to process.");` |
| `Debug` | Deep debugging information. Only visible at Diagnostic verbosity. | `Debug("Resolved file path: /src/obj/debug");` |
| `Fatal` | Critical failure logging. | `Fatal("Cannot continue without valid API key.");` |

## String Formatting

All Cake logging aliases natively support string formatting, allowing you to easily inject variables directly into your log messages without needing string concatenation.

```csharp
var projectCount = 5;
Information("Successfully compiled {0} projects.", projectCount);
Verbosity Levels
The visibility of your log messages depends on the verbosity level specified when the Cake script is executed. You can pass the --verbosity argument via the command line:

Bash
dotnet cake --verbosity=Diagnostic
Cake supports the following verbosity levels:

Quiet: Displays only Error and Fatal messages.

Minimal: Displays Warning, Error, and Fatal messages.

Normal: (Default) Displays Information and above.

Verbose: Displays Verbose messages and above.

Diagnostic: Displays Debug messages and above, providing the most detailed output.
