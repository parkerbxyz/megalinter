---
title: jsonlint configuration in MegaLinter
description: How to use jsonlint (configure, ignore files, ignore errors, help & version documentations) to analyze JSON files
---
<!-- markdownlint-disable MD033 MD041 -->
<!-- @generated by .automation/build.py, please don't update manually -->
# jsonlint
[![GitHub stars](https://img.shields.io/github/stars/prantlf/jsonlint?cacheSeconds=3600)](https://github.com/prantlf/jsonlint) [![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/prantlf/jsonlint?sort=semver)](https://github.com/prantlf/jsonlint/releases) [![GitHub last commit](https://img.shields.io/github/last-commit/prantlf/jsonlint)](https://github.com/prantlf/jsonlint/commits) [![GitHub commit activity](https://img.shields.io/github/commit-activity/y/prantlf/jsonlint)](https://github.com/prantlf/jsonlint/graphs/commit-activity/) [![GitHub contributors](https://img.shields.io/github/contributors/prantlf/jsonlint)](https://github.com/prantlf/jsonlint/graphs/contributors/)

**jsonlint** is a comprehensive JSON validation tool that provides command-line interface for ensuring JSON files conform to specifications and maintain proper structure. It serves as the essential validator for JSON data integrity across web applications, APIs, and configuration systems.

**Key Features:**

- **Pure JavaScript Implementation**: Native JavaScript JSON parser ensuring accurate validation without external dependencies
- **Strict JSON Compliance**: Validates against official JSON specification to ensure maximum compatibility
- **Syntax Error Detection**: Identifies malformed JSON structures, missing brackets, invalid characters, and formatting issues
- **Fast Validation**: High-performance parsing suitable for large JSON files and batch processing
- **Detailed Error Reporting**: Clear error messages with line and column information for easy debugging
- **Configurable Options**: Flexible validation options through .jsonlintrc configuration files
- **Batch Processing**: Efficient validation of multiple JSON files in a single command
- **Cross-Platform**: Consistent validation behavior across Windows, macOS, and Linux environments

## jsonlint documentation

- Version in MegaLinter: **16.0.0**
- Visit [Official Web Site](https://github.com/prantlf/jsonlint#readme){target=_blank}
- See [How to configure jsonlint rules](https://github.com/prantlf/jsonlint#configuration){target=_blank}
- See [Index of problems detected by jsonlint](https://github.com/prantlf/jsonlint#configuration){target=_blank}

[![jsonlint - GitHub](https://gh-card.dev/repos/prantlf/jsonlint.svg?fullname=)](https://github.com/prantlf/jsonlint){target=_blank}

## Configuration in MegaLinter

- Enable jsonlint by adding `JSON_JSONLINT` in [ENABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)
- Disable jsonlint by adding `JSON_JSONLINT` in [DISABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)

| Variable                                  | Description                                                                                                                                                                                                         | Default value                                   |
|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| JSON_JSONLINT_ARGUMENTS                   | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"`                                                                                                                                            |                                                 |
| JSON_JSONLINT_COMMAND_REMOVE_ARGUMENTS    | User custom arguments to remove from command line before calling the linter<br/>Ex: `-s --foo "bar"`                                                                                                                |                                                 |
| JSON_JSONLINT_FILTER_REGEX_INCLUDE        | Custom regex including filter<br/>Ex: `(src\|lib)`                                                                                                                                                                  | Include every file                              |
| JSON_JSONLINT_FILTER_REGEX_EXCLUDE        | Custom regex excluding filter<br/>Ex: `(test\|examples)`                                                                                                                                                            | Exclude no file                                 |
| JSON_JSONLINT_CLI_LINT_MODE               | Override default CLI lint mode<br/>- `file`: Calls the linter for each file<br/>- `list_of_files`: Call the linter with the list of files as argument<br/>- `project`: Call the linter from the root of the project | `list_of_files`                                 |
| JSON_JSONLINT_FILE_EXTENSIONS             | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]`                                                                             | `[".json"]`                                     |
| JSON_JSONLINT_FILE_NAMES_REGEX            | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]`                        | Include every file                              |
| JSON_JSONLINT_PRE_COMMANDS                | List of bash commands to run before the linter                                                                                                                                                                      | None                                            |
| JSON_JSONLINT_POST_COMMANDS               | List of bash commands to run after the linter                                                                                                                                                                       | None                                            |
| JSON_JSONLINT_UNSECURED_ENV_VARIABLES     | List of env variables explicitly not filtered before calling JSON_JSONLINT and its pre/post commands                                                                                                                | None                                            |
| JSON_JSONLINT_CONFIG_FILE                 | jsonlint configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it                                                                                                                                 | `.jsonlintrc`                                   |
| JSON_JSONLINT_RULES_PATH                  | Path where to find linter configuration file                                                                                                                                                                        | Workspace folder, then MegaLinter default rules |
| JSON_JSONLINT_DISABLE_ERRORS              | Run linter but consider errors as warnings                                                                                                                                                                          | `false`                                         |
| JSON_JSONLINT_DISABLE_ERRORS_IF_LESS_THAN | Maximum number of errors allowed                                                                                                                                                                                    | `0`                                             |
| JSON_JSONLINT_CLI_EXECUTABLE              | Override CLI executable                                                                                                                                                                                             | `['jsonlint']`                                  |

## MegaLinter Flavors

This linter is available in the following flavors

|                                                                         <!-- -->                                                                         | Flavor                                                             | Description                                                            | Embedded linters |                                                                                                                                                                                                   Info |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------|:-----------------------------------------------------------------------|:----------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://megalinter.io/beta/supported-linters/)               | Default MegaLinter Flavor                                              |       127        |                             ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/c_cpp.ico" alt="" height="32px" class="megalinter-icon"></a>        | [c_cpp](https://megalinter.io/beta/flavors/c_cpp/)                 | Optimized for pure C/C++ projects                                      |        57        |                 ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-c_cpp/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-c_cpp) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/ci_light.ico" alt="" height="32px" class="megalinter-icon"></a>       | [ci_light](https://megalinter.io/beta/flavors/ci_light/)           | Optimized for CI items (Dockerfile, Jenkinsfile, JSON/YAML schemas,XML |        22        |           ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-ci_light/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-ci_light) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/cupcake.ico" alt="" height="32px" class="megalinter-icon"></a>       | [cupcake](https://megalinter.io/beta/flavors/cupcake/)             | MegaLinter for the most commonly used languages                        |        88        |             ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-cupcake/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-cupcake) |
|    <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/documentation.ico" alt="" height="32px" class="megalinter-icon"></a>    | [documentation](https://megalinter.io/beta/flavors/documentation/) | MegaLinter for documentation projects                                  |        50        | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-documentation/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-documentation) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a>        | [dotnet](https://megalinter.io/beta/flavors/dotnet/)               | Optimized for C, C++, C# or VB based projects                          |        65        |               ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnet/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnet) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnetweb.ico" alt="" height="32px" class="megalinter-icon"></a>      | [dotnetweb](https://megalinter.io/beta/flavors/dotnetweb/)         | Optimized for C, C++, C# or VB based projects with JS/TS               |        74        |         ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnetweb/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnetweb) |
|         <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/go.ico" alt="" height="32px" class="megalinter-icon"></a>          | [go](https://megalinter.io/beta/flavors/go/)                       | Optimized for GO based projects                                        |        52        |                       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-go/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-go) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/java.ico" alt="" height="32px" class="megalinter-icon"></a>         | [java](https://megalinter.io/beta/flavors/java/)                   | Optimized for JAVA based projects                                      |        55        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-java/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-java) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/javascript.ico" alt="" height="32px" class="megalinter-icon"></a>      | [javascript](https://megalinter.io/beta/flavors/javascript/)       | Optimized for JAVASCRIPT or TYPESCRIPT based projects                  |        60        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-javascript/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-javascript) |
|         <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/php.ico" alt="" height="32px" class="megalinter-icon"></a>         | [php](https://megalinter.io/beta/flavors/php/)                     | Optimized for PHP based projects                                       |        55        |                     ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-php/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-php) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/python.ico" alt="" height="32px" class="megalinter-icon"></a>        | [python](https://megalinter.io/beta/flavors/python/)               | Optimized for PYTHON based projects                                    |        66        |               ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-python/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-python) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/ruby.ico" alt="" height="32px" class="megalinter-icon"></a>         | [ruby](https://megalinter.io/beta/flavors/ruby/)                   | Optimized for RUBY based projects                                      |        51        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-ruby/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-ruby) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/rust.ico" alt="" height="32px" class="megalinter-icon"></a>         | [rust](https://megalinter.io/beta/flavors/rust/)                   | Optimized for RUST based projects                                      |        51        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-rust/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-rust) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/salesforce.ico" alt="" height="32px" class="megalinter-icon"></a>      | [salesforce](https://megalinter.io/beta/flavors/salesforce/)       | Optimized for Salesforce based projects                                |        55        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-salesforce/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-salesforce) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/swift.ico" alt="" height="32px" class="megalinter-icon"></a>        | [swift](https://megalinter.io/beta/flavors/swift/)                 | Optimized for SWIFT based projects                                     |        51        |                 ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-swift/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-swift) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a>      | [terraform](https://megalinter.io/beta/flavors/terraform/)         | Optimized for TERRAFORM based projects                                 |        55        |         ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-terraform/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-terraform) |

## Behind the scenes

### How are identified applicable files

- File extensions: `.json`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->
### How the linting is performed

- jsonlint is called once with the list of files as arguments (`list_of_files` CLI lint mode)

### Example calls

```shell
jsonlint myfile1.json myfile2.json
```


### Help content

```shell
JSON/CJSON/JSON5 parser, syntax and schema validator and pretty-printer.

Usage: jsonlint [options] [--] [<file, directory, pattern> ...]

Options:
  -f, --config <file>          read options from a custom configuration file
  -F, --no-config              disable searching for configuration files
  --ignore-proto-key           ignore occurrences of "__proto__" object key
  --ignore-prototype-keys      ignore all keys from "Object.prototype"
  -s, --sort-keys              sort object keys (not when prettifying)
  --sort-keys-ignore-case      sort object keys ignoring the letter case
  --sort-keys-locale <id>      locale identifier to sort object keys with
                               (or "default" for the system default)
  --sort-keys-case-first <id>  order if only letter case is different
                               ("upper", "lower" and "false" are allowed)
  --sort-keys-numeric          sort by numbers recognised in object keys
  -E, --extensions <ext...>    file extensions to process for directory walk
                               (default: json, JSON)
  -i, --in-place               overwrite the input files
  -j, --diff                   print difference instead of writing the output
  -k, --check                  check that the input is equal to the output
  -t, --indent <num|char>      number of spaces or specific characters to use
                               for indentation or a string with whitespace
  -c, --compact                compact error display
  -M, --mode <mode>            set other parsing flags according to the format
                               of the input data (default: json)
  -B, --bom                    ignore the leading UTF-8 byte-order mark
  -C, --comments               recognize and ignore JavaScript-style comments
  -S, --single-quoted-strings  support single quotes as string delimiters
  -T, --trailing-commas        ignore trailing commas in objects and arrays
  -D, --no-duplicate-keys      report duplicate object keys as an error
  -V, --validate <file...>     JSON Schema file(s) to use for validation
  -e, --environment <env>      which version of JSON Schema the validation
                               should use
  -x, --context <num>          line number used as the diff context
                               (default: 3)
  -l, --log-files              print only the parsed file names to stdout
  -q, --quiet                  do not print the parsed json to stdout
  -n, --continue               continue with other files if an error occurs
  -p, --pretty-print           prettify the input instead of stringifying
                               the parsed object
  -P, --pretty-print-invalid   force pretty-printing even for invalid input
  -r, --trailing-newline       ensure a line break at the end of the output
  -R, --no-trailing-newline    ensure no line break at the end of the output
  --prune-comments             omit comments from the prettified output
  --strip-object-keys          strip quotes from object keys if possible
  --enforce-double-quotes      surrounds all strings with double quotes
  --enforce-single-quotes      surrounds all strings with single quotes
  --trim-trailing-commas       omit trailing commas from objects and arrays
  --succeed-with-no-files      succeed (exit code 0) if no files were found
  -v, --version                output the version number
  -h, --help                   display help for command

Examples:
  $ jsonlint myfile.json
  $ jsonlint --in-place --pretty-print mydir
  $ jsonlint --comments --trailing-commas --no-duplicate-keys \
      --log-files --compact --continue '**/*.json' '!**/node_modules'
```

### Installation on mega-linter Docker image

- Dockerfile commands :
```dockerfile
# renovate: datasource=npm depName=@prantlf/jsonlint
ARG NPM_PRANTLF_JSONLINT_VERSION=16.0.0
```

- NPM packages (node.js):
  - [@prantlf/jsonlint@16.0.0](https://www.npmjs.com/package/@prantlf/jsonlint/v/16.0.0)
