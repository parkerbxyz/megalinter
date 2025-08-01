---
title: markdown-link-check configuration in MegaLinter
description: How to use markdown-link-check (configure, ignore files, ignore errors, help & version documentations) to analyze MARKDOWN files
---
<!-- markdownlint-disable MD033 MD041 -->
<!-- @generated by .automation/build.py, please don't update manually -->
# markdown-link-check
![downgraded version](https://shields.io/badge/-downgraded%20version-orange) [![GitHub stars](https://img.shields.io/github/stars/tcort/markdown-link-check?cacheSeconds=3600)](https://github.com/tcort/markdown-link-check) [![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/tcort/markdown-link-check?sort=semver)](https://github.com/tcort/markdown-link-check/releases) [![GitHub last commit](https://img.shields.io/github/last-commit/tcort/markdown-link-check)](https://github.com/tcort/markdown-link-check/commits) [![GitHub commit activity](https://img.shields.io/github/commit-activity/y/tcort/markdown-link-check)](https://github.com/tcort/markdown-link-check/graphs/commit-activity/) [![GitHub contributors](https://img.shields.io/github/contributors/tcort/markdown-link-check)](https://github.com/tcort/markdown-link-check/graphs/contributors/)

**markdown-link-check** is a specialized tool for validating link integrity in Markdown documentation that ensures all links remain functional and accessible. It serves as an essential quality assurance tool for maintaining reliable documentation with working references.

**Key Features:**

- **Comprehensive Link Validation**: Tests HTTP/HTTPS links, relative file paths, anchor links, and email addresses
- **Dead Link Detection**: Identifies broken external links, missing internal files, and invalid anchor references
- **HTTP Status Checking**: Validates that external links return successful HTTP responses (200 status codes)
- **Configurable Timeouts**: Adjustable request timeouts and retry logic for reliable network-dependent testing
- **Pattern Matching**: Supports regex patterns for excluding specific links or domains from validation
- **Detailed Reporting**: Clear output showing which links passed, failed, or were skipped with specific error details
- **Bulk Processing**: Efficiently processes multiple Markdown files with consolidated reporting
- **Inline Control**: Comment-based directives for disabling checks on specific links when needed

## markdown-link-check documentation

- Version in MegaLinter: **3.12.2**
- Visit [Official Web Site](https://github.com/tcort/markdown-link-check#readme){target=_blank}
- See [How to configure markdown-link-check rules](https://github.com/tcort/markdown-link-check#config-file-format){target=_blank}
  - If custom `.markdown-link-check.json` config file isn't found, [.markdown-link-check.json](https://github.com/oxsecurity/megalinter/tree/main/TEMPLATES/.markdown-link-check.json){target=_blank} will be used
- See [How to disable markdown-link-check rules in files](https://github.com/tcort/markdown-link-check#disable-comments){target=_blank}

[![markdown-link-check - GitHub](https://gh-card.dev/repos/tcort/markdown-link-check.svg?fullname=)](https://github.com/tcort/markdown-link-check){target=_blank}

## Configuration in MegaLinter

- Enable markdown-link-check by adding `MARKDOWN_MARKDOWN_LINK_CHECK` in [ENABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)
- Disable markdown-link-check by adding `MARKDOWN_MARKDOWN_LINK_CHECK` in [DISABLE_LINTERS variable](https://megalinter.io/beta/configuration/#activation-and-deactivation)

| Variable                                                 | Description                                                                                                                                                                                                         | Default value                                   |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| MARKDOWN_MARKDOWN_LINK_CHECK_ARGUMENTS                   | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"`                                                                                                                                            |                                                 |
| MARKDOWN_MARKDOWN_LINK_CHECK_COMMAND_REMOVE_ARGUMENTS    | User custom arguments to remove from command line before calling the linter<br/>Ex: `-s --foo "bar"`                                                                                                                |                                                 |
| MARKDOWN_MARKDOWN_LINK_CHECK_FILTER_REGEX_INCLUDE        | Custom regex including filter<br/>Ex: `(src\|lib)`                                                                                                                                                                  | Include every file                              |
| MARKDOWN_MARKDOWN_LINK_CHECK_FILTER_REGEX_EXCLUDE        | Custom regex excluding filter<br/>Ex: `(test\|examples)`                                                                                                                                                            | Exclude no file                                 |
| MARKDOWN_MARKDOWN_LINK_CHECK_CLI_LINT_MODE               | Override default CLI lint mode<br/>- `file`: Calls the linter for each file<br/>- `list_of_files`: Call the linter with the list of files as argument<br/>- `project`: Call the linter from the root of the project | `list_of_files`                                 |
| MARKDOWN_MARKDOWN_LINK_CHECK_FILE_EXTENSIONS             | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]`                                                                             | `[".md"]`                                       |
| MARKDOWN_MARKDOWN_LINK_CHECK_FILE_NAMES_REGEX            | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]`                        | Include every file                              |
| MARKDOWN_MARKDOWN_LINK_CHECK_PRE_COMMANDS                | List of bash commands to run before the linter                                                                                                                                                                      | None                                            |
| MARKDOWN_MARKDOWN_LINK_CHECK_POST_COMMANDS               | List of bash commands to run after the linter                                                                                                                                                                       | None                                            |
| MARKDOWN_MARKDOWN_LINK_CHECK_UNSECURED_ENV_VARIABLES     | List of env variables explicitly not filtered before calling MARKDOWN_MARKDOWN_LINK_CHECK and its pre/post commands                                                                                                 | None                                            |
| MARKDOWN_MARKDOWN_LINK_CHECK_CONFIG_FILE                 | markdown-link-check configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it                                                                                                                      | `.markdown-link-check.json`                     |
| MARKDOWN_MARKDOWN_LINK_CHECK_RULES_PATH                  | Path where to find linter configuration file                                                                                                                                                                        | Workspace folder, then MegaLinter default rules |
| MARKDOWN_MARKDOWN_LINK_CHECK_DISABLE_ERRORS              | Run linter but consider errors as warnings                                                                                                                                                                          | `false`                                         |
| MARKDOWN_MARKDOWN_LINK_CHECK_DISABLE_ERRORS_IF_LESS_THAN | Maximum number of errors allowed                                                                                                                                                                                    | `0`                                             |
| MARKDOWN_MARKDOWN_LINK_CHECK_CLI_EXECUTABLE              | Override CLI executable                                                                                                                                                                                             | `['markdown-link-check']`                       |

## MegaLinter Flavors

This linter is available in the following flavors

|                                                                         <!-- -->                                                                         | Flavor                                                             | Description                                              | Embedded linters |                                                                                                                                                                                                   Info |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------|:---------------------------------------------------------|:----------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://megalinter.io/beta/supported-linters/)               | Default MegaLinter Flavor                                |       127        |                             ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/c_cpp.ico" alt="" height="32px" class="megalinter-icon"></a>        | [c_cpp](https://megalinter.io/beta/flavors/c_cpp/)                 | Optimized for pure C/C++ projects                        |        57        |                 ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-c_cpp/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-c_cpp) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/cupcake.ico" alt="" height="32px" class="megalinter-icon"></a>       | [cupcake](https://megalinter.io/beta/flavors/cupcake/)             | MegaLinter for the most commonly used languages          |        88        |             ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-cupcake/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-cupcake) |
|    <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/documentation.ico" alt="" height="32px" class="megalinter-icon"></a>    | [documentation](https://megalinter.io/beta/flavors/documentation/) | MegaLinter for documentation projects                    |        50        | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-documentation/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-documentation) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a>        | [dotnet](https://megalinter.io/beta/flavors/dotnet/)               | Optimized for C, C++, C# or VB based projects            |        65        |               ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnet/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnet) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnetweb.ico" alt="" height="32px" class="megalinter-icon"></a>      | [dotnetweb](https://megalinter.io/beta/flavors/dotnetweb/)         | Optimized for C, C++, C# or VB based projects with JS/TS |        74        |         ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnetweb/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnetweb) |
|         <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/go.ico" alt="" height="32px" class="megalinter-icon"></a>          | [go](https://megalinter.io/beta/flavors/go/)                       | Optimized for GO based projects                          |        52        |                       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-go/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-go) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/java.ico" alt="" height="32px" class="megalinter-icon"></a>         | [java](https://megalinter.io/beta/flavors/java/)                   | Optimized for JAVA based projects                        |        55        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-java/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-java) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/javascript.ico" alt="" height="32px" class="megalinter-icon"></a>      | [javascript](https://megalinter.io/beta/flavors/javascript/)       | Optimized for JAVASCRIPT or TYPESCRIPT based projects    |        60        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-javascript/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-javascript) |
|         <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/php.ico" alt="" height="32px" class="megalinter-icon"></a>         | [php](https://megalinter.io/beta/flavors/php/)                     | Optimized for PHP based projects                         |        55        |                     ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-php/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-php) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/python.ico" alt="" height="32px" class="megalinter-icon"></a>        | [python](https://megalinter.io/beta/flavors/python/)               | Optimized for PYTHON based projects                      |        66        |               ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-python/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-python) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/ruby.ico" alt="" height="32px" class="megalinter-icon"></a>         | [ruby](https://megalinter.io/beta/flavors/ruby/)                   | Optimized for RUBY based projects                        |        51        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-ruby/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-ruby) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/rust.ico" alt="" height="32px" class="megalinter-icon"></a>         | [rust](https://megalinter.io/beta/flavors/rust/)                   | Optimized for RUST based projects                        |        51        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-rust/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-rust) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/salesforce.ico" alt="" height="32px" class="megalinter-icon"></a>      | [salesforce](https://megalinter.io/beta/flavors/salesforce/)       | Optimized for Salesforce based projects                  |        55        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-salesforce/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-salesforce) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/swift.ico" alt="" height="32px" class="megalinter-icon"></a>        | [swift](https://megalinter.io/beta/flavors/swift/)                 | Optimized for SWIFT based projects                       |        51        |                 ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-swift/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-swift) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a>      | [terraform](https://megalinter.io/beta/flavors/terraform/)         | Optimized for TERRAFORM based projects                   |        55        |         ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-terraform/beta) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-terraform) |

## Behind the scenes

### How are identified applicable files

- File extensions: `.md`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->
### How the linting is performed

- markdown-link-check is called once with the list of files as arguments (`list_of_files` CLI lint mode)

### Example calls

```shell
markdown-link-check myfile.md
```

```shell
markdown-link-check -c .markdown-link-check.json myfile.md
```


### Help content

```shell
Usage: markdown-link-check [options] [filenamesOrUrls...]

Options:
  -V, --version           output the version number
  -p, --progress          show progress bar
  -c, --config [config]   apply a config file (JSON), holding e.g. url specific
                          header configuration
  -q, --quiet             displays errors only
  -v, --verbose           displays detailed error information
  -i --ignore <paths>     ignore input paths including an ignore path
  -a, --alive <code>      comma separated list of HTTP codes to be considered
                          as alive
  -r, --retry             retry after the duration indicated in 'retry-after'
                          header when HTTP code is 429
  --projectBaseUrl <url>  the URL to use for {{BASEURL}} replacement
  -h, --help              display help for command
```

### Installation on mega-linter Docker image

- Dockerfile commands :
```dockerfile
# renovate: datasource=npm depName=markdown-link-check
ARG NPM_MARKDOWN_LINK_CHECK_VERSION=3.12.2
```

- NPM packages (node.js):
  - [markdown-link-check@3.12.2](https://www.npmjs.com/package/markdown-link-check/v/3.12.2)
