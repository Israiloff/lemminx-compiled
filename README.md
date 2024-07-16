# Lemminx-Compiled

[![Latest Release](https://img.shields.io/github/v/release/yourusername/lemminx-compiled)](https://github.com/yourusername/lemminx-compiled/releases/latest)

Lemminx-Compiled is a repository for precompiled Lemminx artifacts (JAR files). Lemminx is an XML language server used to provide XML language support in various editors and IDEs.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This repository provides precompiled Lemminx JAR files for easy integration into your development environment. By downloading a precompiled JAR, you can avoid the need to build Lemminx from source.

## Installation

To use the precompiled Lemminx JAR, follow these steps:

1. Download the latest JAR file from the [Releases](https://github.com/yourusername/lemminx-compiled/releases) page.
2. Place the JAR file in a directory of your choice.

## Usage

To use Lemminx in your development environment, you typically need to configure your editor or IDE to use the downloaded JAR file. Here are examples for some popular editors:

### VS Code

1. Install the [XML Language Support by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml) extension.
2. Configure the extension to use the downloaded Lemminx JAR file by adding the following to your `settings.json`:

    ```json
    {
        "xml.server.jar": "/path/to/your/lemminx-0.28.0.jar"
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
