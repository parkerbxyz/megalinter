---
title: csharpier configuration in MegaLinter
description: How to use csharpier (configure, ignore files, ignore errors, help & version documentations) to analyze CSHARP files
---
<!-- markdownlint-disable MD033 MD041 -->
<!-- @generated by .automation/build.py, please don't update manually -->
# <a href="https://csharpier.com/" target="blank" title="Visit linter Web Site"><img src="https://csharpier.com/img/logo.svg" alt="csharpier" height="100px" class="megalinter-logo"></a>csharpier
[![GitHub stars](https://img.shields.io/github/stars/belav/csharpier?cacheSeconds=3600)](https://github.com/belav/csharpier) ![formatter](https://shields.io/badge/-format-yellow) [![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/belav/csharpier?sort=semver)](https://github.com/belav/csharpier/releases) [![GitHub last commit](https://img.shields.io/github/last-commit/belav/csharpier)](https://github.com/belav/csharpier/commits) [![GitHub commit activity](https://img.shields.io/github/commit-activity/y/belav/csharpier)](https://github.com/belav/csharpier/graphs/commit-activity/) [![GitHub contributors](https://img.shields.io/github/contributors/belav/csharpier)](https://github.com/belav/csharpier/graphs/contributors/)

**CSharpier** is the definitive opinionated code formatter for C# that eliminates formatting debates by automatically standardizing code style across entire projects. Inspired by Prettier's philosophy, it provides zero-configuration formatting that just works.

**Key Features:**

- **Zero Configuration**: Works out of the box with sensible defaults, no setup required
- **Opinionated Formatting**: Consistent, predictable formatting that eliminates style discussions
- **Comprehensive C# Support**: Handles all modern C# language features, syntax, and constructs
- **Fast Performance**: Lightning-fast formatting with minimal overhead for large codebases
- **Ignore Support**: Flexible ignore patterns for excluding specific files or code sections from formatting
- **Diff-Friendly**: Produces minimal, clean git diffs by maintaining consistent formatting rules
- **Team Consistency**: Ensures identical formatting across all team members and development environments

## csharpier documentation

- Version in MegaLinter: **1.0.3**
- Visit [Official Web Site](https://csharpier.com/){target=_blank}
- See [How to configure csharpier rules](https://csharpier.com/docs/Configuration){target=_blank}
- See [How to disable csharpier rules in files](https://csharpier.com/docs/Ignore){target=_blank}
- See [How to ignore files and directories with csharpier](https://csharpier.com/docs/Ignore){target=_blank}
  - You can define a `.csharpierignore` file to ignore files and folders

[![csharpier - GitHub](https://gh-card.dev/repos/belav/csharpier.svg?fullname=)](https://github.com/belav/csharpier){target=_blank}

## Configuration in MegaLinter

- Enable csharpier by adding `CSHARP_CSHARPIER` in [ENABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)
- Disable csharpier by adding `CSHARP_CSHARPIER` in [DISABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)

- Enable **autofixes** by adding `CSHARP_CSHARPIER` in [APPLY_FIXES variable](https://megalinter.io/beta/configuration/#apply-fixes)

| Variable                                     | Description                                                                                                                                                                                                         | Default value                                         |
|----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| CSHARP_CSHARPIER_ARGUMENTS                   | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"`                                                                                                                                            |                                                       |
| CSHARP_CSHARPIER_COMMAND_REMOVE_ARGUMENTS    | User custom arguments to remove from command line before calling the linter<br/>Ex: `-s --foo "bar"`                                                                                                                |                                                       |
| CSHARP_CSHARPIER_FILTER_REGEX_INCLUDE        | Custom regex including filter<br/>Ex: `(src\|lib)`                                                                                                                                                                  | Include every file                                    |
| CSHARP_CSHARPIER_FILTER_REGEX_EXCLUDE        | Custom regex excluding filter<br/>Ex: `(test\|examples)`                                                                                                                                                            | Exclude no file                                       |
| CSHARP_CSHARPIER_CLI_LINT_MODE               | Override default CLI lint mode<br/>- `file`: Calls the linter for each file<br/>- `list_of_files`: Call the linter with the list of files as argument<br/>- `project`: Call the linter from the root of the project | `list_of_files`                                       |
| CSHARP_CSHARPIER_FILE_EXTENSIONS             | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]`                                                                             | `[".config", ".cs", ".csproj", ".props", ".targets"]` |
| CSHARP_CSHARPIER_FILE_NAMES_REGEX            | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]`                        | Include every file                                    |
| CSHARP_CSHARPIER_PRE_COMMANDS                | List of bash commands to run before the linter                                                                                                                                                                      | None                                                  |
| CSHARP_CSHARPIER_POST_COMMANDS               | List of bash commands to run after the linter                                                                                                                                                                       | None                                                  |
| CSHARP_CSHARPIER_UNSECURED_ENV_VARIABLES     | List of env variables explicitly not filtered before calling CSHARP_CSHARPIER and its pre/post commands                                                                                                             | None                                                  |
| CSHARP_CSHARPIER_CONFIG_FILE                 | csharpier configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it                                                                                                                                | `.csharpierrc`                                        |
| CSHARP_CSHARPIER_RULES_PATH                  | Path where to find linter configuration file                                                                                                                                                                        | Workspace folder, then MegaLinter default rules       |
| CSHARP_CSHARPIER_DISABLE_ERRORS              | Run linter but consider errors as warnings                                                                                                                                                                          | `true`                                                |
| CSHARP_CSHARPIER_DISABLE_ERRORS_IF_LESS_THAN | Maximum number of errors allowed                                                                                                                                                                                    | `0`                                                   |
| CSHARP_CSHARPIER_CLI_EXECUTABLE              | Override CLI executable                                                                                                                                                                                             | `['csharpier']`                                       |

## IDE Integration

Use csharpier in your favorite IDE to catch errors before MegaLinter !

|                                                                   <!-- -->                                                                   | IDE                                                  | Extension Name                                                                                     |                                                                                     Install                                                                                     |
|:--------------------------------------------------------------------------------------------------------------------------------------------:|------------------------------------------------------|----------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/default.ico" alt="" height="32px" class="megalinter-icon"></a> | rider                                                | [csharpier](https://plugins.jetbrains.com/plugin/18243-csharpier)                                  |                                              [Visit Web Site](https://plugins.jetbrains.com/plugin/18243-csharpier){target=_blank}                                              |
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/default.ico" alt="" height="32px" class="megalinter-icon"></a> | visual_studio                                        | [CSharpier](https://marketplace.visualstudio.com/items?itemName=csharpier.CSharpier)               |                                    [Visit Web Site](https://marketplace.visualstudio.com/items?itemName=csharpier.CSharpier){target=_blank}                                     |
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/vscode.ico" alt="" height="32px" class="megalinter-icon"></a>  | [Visual Studio Code](https://code.visualstudio.com/) | [csharpier-vscode](https://marketplace.visualstudio.com/items?itemName=csharpier.csharpier-vscode) | [![Install in VSCode](https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/btn_install_vscode.png)](vscode:extension/csharpier.csharpier-vscode){target=_blank} |

## MegaLinter Flavors

This linter is available in the following flavors

|                                                                         <!-- -->                                                                         | Flavor                                                       | Description                                              | Embedded linters |                                                                                                                                                                                             Info |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------|:---------------------------------------------------------|:----------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://megalinter.io/beta/supported-linters/)         | Default MegaLinter Flavor                                |       127        |                       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a>        | [dotnet](https://megalinter.io/beta/flavors/dotnet/)         | Optimized for C, C++, C# or VB based projects            |        65        |         ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnet/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnet) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnetweb.ico" alt="" height="32px" class="megalinter-icon"></a>      | [dotnetweb](https://megalinter.io/beta/flavors/dotnetweb/)   | Optimized for C, C++, C# or VB based projects with JS/TS |        74        |   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnetweb/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnetweb) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/formatters.ico" alt="" height="32px" class="megalinter-icon"></a>      | [formatters](https://megalinter.io/beta/flavors/formatters/) | Contains only formatters                                 |        18        | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-formatters/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-formatters) |

## Behind the scenes

### How are identified applicable files

- File extensions: `.config`, `.cs`, `.csproj`, `.props`, `.targets`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->
### How the linting is performed

- csharpier is called once with the list of files as arguments (`list_of_files` CLI lint mode)

### Example calls

```shell
csharpier check myfile.cs myfile2.cs
```

```shell
csharpier format myfile.cs myfile2.cs
```


### Help content

```shell
Description:

Usage:
  CSharpier [command] [options]

Options:
  --version       Show version information
  -?, -h, --help  Show help and usage information

Commands:
  format <directoryOrFile>  Format files.
  check <directoryOrFile>   Check that files are formatted. Will not write any changes.
  pipe-files                Keep csharpier running so that multiples files can be piped to it via stdin.
  server                    Run CSharpier as a server so that multiple files may be formatted.

```

### Installation on mega-linter Docker image

- Dockerfile commands :
```dockerfile
# Parent descriptor install
RUN apk add --no-cache dotnet9-sdk
ENV PATH="${PATH}:/root/.dotnet/tools"
# Linter install
# renovate: datasource=nuget depName=csharpier
ARG CSHARP_CSHARPIER_VERSION=1.0.3
RUN dotnet tool install --allow-roll-forward --global csharpier --version "${CSHARP_CSHARPIER_VERSION}"
```

