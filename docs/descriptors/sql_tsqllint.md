---
title: tsqllint configuration in MegaLinter
description: How to use tsqllint (configure, ignore files, ignore errors, help & version documentations) to analyze SQL files
---
<!-- markdownlint-disable MD033 MD041 -->
<!-- @generated by .automation/build.py, please don't update manually -->
# <a href="https://github.com/tsqllint/tsqllint" target="blank" title="Visit linter Web Site"><img src="https://tsqllint.gallerycdn.vsassets.io/extensions/tsqllint/tsqllint/1.2.0/1528922982751/Microsoft.VisualStudio.Services.Icons.Default" alt="tsqllint" height="100px" class="megalinter-logo"></a>tsqllint
[![GitHub stars](https://img.shields.io/github/stars/tsqllint/tsqllint?cacheSeconds=3600)](https://github.com/tsqllint/tsqllint) [![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/tsqllint/tsqllint?sort=semver)](https://github.com/tsqllint/tsqllint/releases) [![GitHub last commit](https://img.shields.io/github/last-commit/tsqllint/tsqllint)](https://github.com/tsqllint/tsqllint/commits) [![GitHub commit activity](https://img.shields.io/github/commit-activity/y/tsqllint/tsqllint)](https://github.com/tsqllint/tsqllint/graphs/commit-activity/) [![GitHub contributors](https://img.shields.io/github/contributors/tsqllint/tsqllint)](https://github.com/tsqllint/tsqllint/graphs/contributors/)

**tsqllint** is a specialized linter for T-SQL (Transact-SQL) code used with Microsoft SQL Server. It analyzes T-SQL scripts for syntax errors, style violations, and adherence to best practices with configurable rules, helping ensure T-SQL code quality and consistency in SQL Server database development projects.

**Key Features:**

- **T-SQL Specialized**: Purpose-built for Microsoft SQL Server T-SQL syntax and features
- **Comprehensive Rule Set**: Extensive collection of rules covering syntax, style, and best practices
- **Configurable Analysis**: Customizable rule configuration to match team coding standards
- **Inline Rule Control**: Support for comment-based rule disabling and configuration within scripts
- **Detailed Error Reporting**: Clear error messages with line numbers and rule explanations
- **Performance Optimized**: Fast analysis suitable for large T-SQL codebases and stored procedures
- **Cross-Platform**: Runs on Windows, macOS, and Linux environments
- **Extensible Architecture**: Plugin system for custom rule development and organizational standards

## tsqllint documentation

- Version in MegaLinter: **1.16.0.0**
- Visit [Official Web Site](https://github.com/tsqllint/tsqllint#readme){target=_blank}
- See [How to configure tsqllint rules](https://github.com/tsqllint/tsqllint#rule-configuration){target=_blank}
- See [How to disable tsqllint rules in files](https://github.com/tsqllint/tsqllint#disabling-rules-with-inline-comments){target=_blank}
- See [Index of problems detected by tsqllint](https://github.com/tsqllint/tsqllint#rule-configuration){target=_blank}

[![tsqllint - GitHub](https://gh-card.dev/repos/tsqllint/tsqllint.svg?fullname=)](https://github.com/tsqllint/tsqllint){target=_blank}

## Configuration in MegaLinter

- Enable tsqllint by adding `SQL_TSQLLINT` in [ENABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)
- Disable tsqllint by adding `SQL_TSQLLINT` in [DISABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)

| Variable                                 | Description                                                                                                                                                                                                         | Default value                                   |
|------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| SQL_TSQLLINT_ARGUMENTS                   | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"`                                                                                                                                            |                                                 |
| SQL_TSQLLINT_COMMAND_REMOVE_ARGUMENTS    | User custom arguments to remove from command line before calling the linter<br/>Ex: `-s --foo "bar"`                                                                                                                |                                                 |
| SQL_TSQLLINT_FILTER_REGEX_INCLUDE        | Custom regex including filter<br/>Ex: `(src\|lib)`                                                                                                                                                                  | Include every file                              |
| SQL_TSQLLINT_FILTER_REGEX_EXCLUDE        | Custom regex excluding filter<br/>Ex: `(test\|examples)`                                                                                                                                                            | Exclude no file                                 |
| SQL_TSQLLINT_CLI_LINT_MODE               | Override default CLI lint mode<br/>- `file`: Calls the linter for each file<br/>- `list_of_files`: Call the linter with the list of files as argument<br/>- `project`: Call the linter from the root of the project | `list_of_files`                                 |
| SQL_TSQLLINT_FILE_EXTENSIONS             | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]`                                                                             | `[".sql"]`                                      |
| SQL_TSQLLINT_FILE_NAMES_REGEX            | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]`                        | Include every file                              |
| SQL_TSQLLINT_PRE_COMMANDS                | List of bash commands to run before the linter                                                                                                                                                                      | None                                            |
| SQL_TSQLLINT_POST_COMMANDS               | List of bash commands to run after the linter                                                                                                                                                                       | None                                            |
| SQL_TSQLLINT_UNSECURED_ENV_VARIABLES     | List of env variables explicitly not filtered before calling SQL_TSQLLINT and its pre/post commands                                                                                                                 | None                                            |
| SQL_TSQLLINT_CONFIG_FILE                 | tsqllint configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it                                                                                                                                 | `.tsqllintrc`                                   |
| SQL_TSQLLINT_RULES_PATH                  | Path where to find linter configuration file                                                                                                                                                                        | Workspace folder, then MegaLinter default rules |
| SQL_TSQLLINT_DISABLE_ERRORS              | Run linter but consider errors as warnings                                                                                                                                                                          | `false`                                         |
| SQL_TSQLLINT_DISABLE_ERRORS_IF_LESS_THAN | Maximum number of errors allowed                                                                                                                                                                                    | `0`                                             |
| SQL_TSQLLINT_CLI_EXECUTABLE              | Override CLI executable                                                                                                                                                                                             | `['tsqllint']`                                  |

## IDE Integration

Use tsqllint in your favorite IDE to catch errors before MegaLinter !

|                                                                  <!-- -->                                                                   | IDE                                                  | Extension Name                                                                     |                                                                                Install                                                                                 |
|:-------------------------------------------------------------------------------------------------------------------------------------------:|------------------------------------------------------|------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/vscode.ico" alt="" height="32px" class="megalinter-icon"></a> | [Visual Studio Code](https://code.visualstudio.com/) | [TSQL Lint](https://marketplace.visualstudio.com/items?itemName=tsqllint.tsqllint) | [![Install in VSCode](https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/btn_install_vscode.png)](vscode:extension/tsqllint.tsqllint){target=_blank} |

## MegaLinter Flavors

This linter is available in the following flavors

|                                                                         <!-- -->                                                                         | Flavor                                                     | Description                                              | Embedded linters |                                                                                                                                                                                           Info |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------|:---------------------------------------------------------|:----------------:|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://megalinter.io/beta/supported-linters/)       | Default MegaLinter Flavor                                |       127        |                     ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a>        | [dotnet](https://megalinter.io/beta/flavors/dotnet/)       | Optimized for C, C++, C# or VB based projects            |        65        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnet/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnet) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnetweb.ico" alt="" height="32px" class="megalinter-icon"></a>      | [dotnetweb](https://megalinter.io/beta/flavors/dotnetweb/) | Optimized for C, C++, C# or VB based projects with JS/TS |        74        | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnetweb/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnetweb) |

## Behind the scenes

### How are identified applicable files

- File extensions: `.sql`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->
### How the linting is performed

- tsqllint is called once with the list of files as arguments (`list_of_files` CLI lint mode)

### Example calls

```shell
tsqllint myfile.sql
```

```shell
tsqllint myfile.sql myfile2.sql
```


### Help content

```shell
running tsqllint

tsqllint [options] [file.sql] | [dir] | [file.sql | dir]

  -c, --config          Used to specify a .tsqllintrc file path other than the
                        default
  -g, --ignorelist      Used to specify a .tsqllintignore file path other than
                        the default
  -f, --force           Used to force generation of default config file when
                        one already exists
  -x, --fix             Used to fix some of the common linting errors if
                        possible
  -i, --init            Generate default .tsqllintrc config file
  -p, --print-config    Print path to config file
  -l, --list-plugins    List the loaded plugins
  -v, --version         Display tsqllint version
  -h, --help            Display this help dialog

```

### Installation on mega-linter Docker image

- Dockerfile commands :
```dockerfile
# renovate: datasource=nuget depName=TSQLLint
ARG SQL_TSQLLINT_VERSION=1.16.0
RUN apk add --no-cache dotnet9-sdk
ENV PATH="${PATH}:/root/.dotnet/tools"
RUN dotnet tool install --allow-roll-forward --global TSQLLint --version ${SQL_TSQLLINT_VERSION}
```

