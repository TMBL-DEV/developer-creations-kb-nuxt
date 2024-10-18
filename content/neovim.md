# Neovim Setup Guide

## Table of Contents
1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Key Mappings](#key-mappings)
4. [Plugins](#plugins)
5. [LSP Setup for TypeScript](#lsp-setup-for-typescript)
6. [Removing Entries from Harpoon](#removing-entries-from-harpoon)

## Installation

1. **Install Neovim**:
   ```bash
   sudo apt install neovim
   ```

2. **Install Packer.nvim** (Plugin Manager):
   ```bash
   git clone --depth 1 https://github.com/wbthomason/packer.nvim \
     ~/.local/share/nvim/site/pack/packer/start/packer.nvim
   ```

## Configuration

1. **Create the Configuration Directory**:
   ```bash
   mkdir -p ~/.config/nvim
   ```

2. **Create and Open the `init.lua` File**:
   ```bash
   nvim ~/.config/nvim/init.lua
   ```

3. **Basic Configuration**:
   ```lua
   -- Initialize packer.nvim
   require('packer').startup(function()
     use 'wbthomason/packer.nvim'        -- Packer manages itself
     use 'nvim-telescope/telescope.nvim' -- Fuzzy Finder
     use 'ThePrimeagen/harpoon'          -- Harpoon for file navigation
     use 'neovim/nvim-lspconfig'         -- LSP configurations
   end)

   -- Set leader key to space
   vim.g.mapleader = ' '

   -- Keymap to save the current file
   vim.api.nvim_set_keymap('n', '<leader>s', ':w<CR>', { noremap = true, silent = true })

   -- LSP for TypeScript
   require'lspconfig'.tsserver.setup{}
   ```

## Key Mappings

| Shortcut             | Action                                |
|----------------------|---------------------------------------|
| `<leader>s`        | Save the current file                |
| `<leader>m`        | Open Harpoon Menu                    |
| `<leader>ff`       | Find files with Telescope             |
| `<C-d>`            | Remove an entry from Harpoon          |
| `<C-s>`            | (If set) Save the current file        |

## Plugins

- **Packer.nvim**: A plugin manager for Neovim.
- **Telescope**: A fuzzy finder for files, buffers, and more.
- **Harpoon**: A plugin for quick navigation between files.
- **nvim-lspconfig**: Configurations for language servers, including TypeScript.

## LSP Setup for TypeScript

1. **Install Node.js and npm** (if not already installed):
   ```bash
   sudo apt update
   sudo apt install nodejs npm
   ```

2. **Install TypeScript and TypeScript Language Server**:
   ```bash
   npm install -g typescript typescript-language-server
   ```

3. **Add TypeScript LSP Configuration** in `init.lua`:
   ```lua
   -- LSP for TypeScript
   require'lspconfig'.tsserver.setup{}
   ```

## Removing Entries from Harpoon

1. **Open Harpoon Menu**:
   - Press `<leader>m` to open the Harpoon menu.

2. **Navigate to the Entry**:
   - Use the arrow keys or `hjkl` to navigate.

3. **Remove the Entry**:
   - Press `Ctrl + d` while the entry is selected to delete it from Harpoon.

---

### Notes
- Remember to run `:PackerSync` in Neovim after adding or modifying plugins in your `init.lua`.
- Use `:source ~/.config/nvim/init.lua` to reload your configuration without restarting Neovim.
