# Lemminx-Compiled

[![Latest Release](https://img.shields.io/github/v/release/Israiloff/lemminx-compiled)](https://github.com/Israiloff/lemminx-compiled/releases/latest)

Lemminx-Compiled is a repository for precompiled [lemminx](https://github.com/eclipse/lemminx) artifacts (JAR files). Lemminx is an XML language server used to provide XML language support in various editors and IDEs. For more information and source code exploration please visit [lemminx github repo](https://github.com/eclipse/lemminx).

## Table of Contents

- [Introduction](#introduction)
- [Releases](#releases)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This repository provides precompiled [lemminx](https://github.com/eclipse/lemminx) JAR files for easy integration into your development environment. By downloading a precompiled JAR, you can avoid the need to build [lemminx](https://github.com/eclipse/lemminx) from source.

## Releases

All releases come with a version tag. The latest release is `v0.28.0`. You can find all releases on the [Releases](https://github.com/Israiloff/lemminx-compiled/releases) page.

### Latest Release

- **Version:** v0.28.0
- **Date:** YYYY-MM-DD
- **Download:** [lemminx-0.28.0.jar](https://github.com/Israiloff/lemminx-compiled/releases/tag/v0.28.0)

For earlier versions, visit the [Releases](https://github.com/Israiloff/lemminx-compiled/releases) page.

## Installation

To use the precompiled Lemminx JAR, follow these steps:

1. Download the latest JAR file from the [Releases](https://github.com/Israiloff/lemminx-compiled/releases) page.
2. Place the JAR file in a directory of your choice.

## Usage

To use Lemminx in your development environment, you typically need to configure your editor or IDE to use the downloaded JAR file. Here are examples for some popular editors:

### VS Code

1. Install the [XML Language Support by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml) extension.
2. Configure the extension to use the downloaded Lemminx JAR file by adding the following to your `settings.json`:

    ```json
    {
        "xml.server.jar": "/path/to/your/org.eclipse.lemminx-uber.jar"
    }
    ```

### Neovim with nvim-lspconfig

1. Install the `nvim-lspconfig` plugin.
2. Get this plugin via your favorite plugin manager (I will use [Lazy.nvim](https://github.com/folke/lazy.nvim)) :
   ```lua
   {
       "Israiloff/lemminx-compiled",
   }
   ```
3. Add the following to your `/ftplugin/xml.lua`:

    ```lua
    local lspconfig = require('lspconfig')
    local lemminx_path = vim.fn.glob(vim.env.HOME .. "/.local/share/nvim/lazy/lemminx-compiled/org.eclipse.lemminx-uber.jar")

    lspconfig.lemminx.setup {
        cmd = { "java", "-jar", lemminx_path },
        capabilities = require("cmp_nvim_lsp").default_capabilities(),
        filetypes = { "xml", "xsd", "xsl", "xslt", "svg" },
    }
    ```

## Contributing

Contributions are welcome! If you would like to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch with a descriptive name.
3. Make your changes.
4. Open a pull request with a clear description of your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
