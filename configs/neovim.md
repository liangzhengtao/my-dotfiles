# Neovim 配置指南 / Neovim Configuration Guide

[返回目录 / Back to Index](../README.md)

## 目录 / Table of Contents

- [简介 / Introduction](#简介--introduction)
- [安装 / Installation](#安装--installation)
- [配置文件 / Configuration File](#配置文件--configuration-file)
- [插件管理 / Plugin Management](#插件管理--plugin-management)
- [LSP 配置 / LSP Configuration](#lsp-配置--lsp-configuration)
- [代码补全 / Code Completion](#代码补全--code-completion)
- [模糊查找 / Fuzzy Finding](#模糊查找--fuzzy-finding)
- [文件浏览 / File Explorer](#文件浏览--file-explorer)
- [Git 集成 / Git Integration](#git-集成--git-integration)
- [主题和外观 / Theme and Appearance](#主题和外观--theme-and-appearance)
- [快捷键配置 / Keybinding Configuration](#快捷键配置--keybinding-configuration)
- [自定义选项 / Customization Options](#自定义选项--customization-options)
- [常见问题 / Common Issues](#常见问题--common-issues)
- [参考资源 / References](#参考资源--references)

## 简介 / Introduction

Neovim 是 Vim 编辑器的现代化分支，具有更好的扩展性和现代化的 API。

Neovim is a modernized fork of Vim with better extensibility and modern APIs.

### 为什么选择 Neovim？ / Why Choose Neovim?

- 🚀 **高性能** - 启动速度快，响应迅速
- 🔌 **Lua 支持** - 使用 Lua 进行配置和插件开发
- 📝 **LSP 支持** - 内置语言服务器协议支持
- 🎨 **现代化 UI** - 支持浮动窗口、弹出菜单等
- 🔧 **高度可定制** - 无限的自定义可能性

- 🚀 **High Performance** - Fast startup, responsive
- 🔌 **Lua Support** - Use Lua for configuration and plugin development
- 📝 **LSP Support** - Built-in Language Server Protocol support
- 🎨 **Modern UI** - Floating windows, popup menus, etc.
- 🔧 **Highly Customizable** - Unlimited customization possibilities

## 安装 / Installation

### 安装 Neovim / Install Neovim

```bash
# macOS (使用 Homebrew)
brew install neovim

# Ubuntu/Debian
sudo apt update
sudo apt install neovim

# CentOS/RHEL
sudo yum install neovim

# Windows (使用 Chocolatey)
choco install neovim

# 或使用 scoop
scoop install neovim
```

### 安装依赖 / Install Dependencies

```bash
# 安装 ripgrep (用于模糊查找)
# macOS
brew install ripgrep

# Ubuntu/Debian
sudo apt install ripgrep

# 安装 fd (用于文件查找)
# macOS
brew install fd

# Ubuntu/Debian
sudo apt install fd-find

# 安装 lazygit (用于 Git 集成)
# macOS
brew install lazygit

# Ubuntu/Debian
sudo apt install lazygit
```

### 创建配置目录 / Create Configuration Directory

```bash
# 创建配置目录 / Create config directory
mkdir -p ~/.config/nvim

# 创建子目录 / Create subdirectories
mkdir -p ~/.config/nvim/lua
mkdir -p ~/.config/nvim/lua/plugins
mkdir -p ~/.config/nvim/lua/config
mkdir -p ~/.config/nvim/after/plugin
```

## 配置文件 / Configuration File

### 完整配置 / Full Configuration

```lua
-- ~/.config/nvim/init.lua
-- Neovim 配置文件 / Neovim Configuration File

-- ============================================================
-- 基础配置 / Basic Configuration
-- ============================================================

-- 设置 Leader 键 / Set Leader key
vim.g.mapleader = " "
vim.g.maplocalleader = " "

-- 设置行号 / Set line numbers
vim.opt.number = true
vim.opt.relativenumber = true

-- 设置缩进 / Set indentation
vim.opt.tabstop = 2
vim.opt.shiftwidth = 2
vim.opt.expandtab = true
vim.opt.autoindent = true
vim.opt.smartindent = true

-- 设置搜索 / Set search
vim.opt.hlsearch = true
vim.opt.incsearch = true
vim.opt.ignorecase = true
vim.opt.smartcase = true

-- 设置外观 / Set appearance
vim.opt.termguicolors = true
vim.opt.signcolumn = "yes"
vim.opt.scrolloff = 8
vim.opt.sidescrolloff = 8
vim.opt.wrap = false
vim.opt.cursorline = true

-- 设置分割窗口 / Set split windows
vim.opt.splitbelow = true
vim.opt.splitright = true

-- 设置撤销 / Set undo
vim.opt.undofile = true
vim.opt.undodir = os.getenv("HOME") .. "/.vim/undodir"

-- 设置剪贴板 / Set clipboard
vim.opt.clipboard = "unnamedplus"

-- 设置鼠标 / Set mouse
vim.opt.mouse = "a"

-- 设置完成 / Set completion
vim.opt.completeopt = { "menu", "menuone", "noselect" }

-- 设置更新时间 / Set update time
vim.opt.updatetime = 250
vim.opt.timeoutlen = 300

-- 设置隐藏字符 / Set hidden characters
vim.opt.list = true
vim.opt.listchars = { tab = "» ", trail = "·", nbsp = "␣" }

-- 设置全局状态行 / Set global statusline
vim.opt.laststatus = 3

-- ============================================================
-- 快捷键配置 / Keybinding Configuration
-- ============================================================

-- 设置 Leader 键 / Set Leader key
vim.g.mapleader = " "
vim.g.maplocalleader = " "

-- 保存和退出 / Save and quit
vim.keymap.set("n", "<leader>w", "<cmd>w<cr>", { desc = "Save" })
vim.keymap.set("n", "<leader>q", "<cmd>q<cr>", { desc = "Quit" })
vim.keymap.set("n", "<leader>Q", "<cmd>qa!<cr>", { desc = "Force quit" })

-- 窗口导航 / Window navigation
vim.keymap.set("n", "<C-h>", "<C-w>h", { desc = "Move to left window" })
vim.keymap.set("n", "<C-j>", "<C-w>j", { desc = "Move to lower window" })
vim.keymap.set("n", "<C-k>", "<C-w>k", { desc = "Move to upper window" })
vim.keymap.set("n", "<C-l>", "<C-w>l", { desc = "Move to right window" })

-- 调整窗口大小 / Resize windows
vim.keymap.set("n", "<C-Up>", "<cmd>resize +2<cr>", { desc = "Increase window height" })
vim.keymap.set("n", "<C-Down>", "<cmd>resize -2<cr>", { desc = "Decrease window height" })
vim.keymap.set("n", "<C-Left>", "<cmd>vertical resize -2<cr>", { desc = "Decrease window width" })
vim.keymap.set("n", "<C-Right>", "<cmd>vertical resize +2<cr>", { desc = "Increase window width" })

-- 缓冲区导航 / Buffer navigation
vim.keymap.set("n", "<S-h>", "<cmd>bprevious<cr>", { desc = "Previous buffer" })
vim.keymap.set("n", "<S-l>", "<cmd>bnext<cr>", { desc = "Next buffer" })
vim.keymap.set("n", "<leader>bd", "<cmd>bdelete<cr>", { desc = "Delete buffer" })

-- 清除搜索高亮 / Clear search highlight
vim.keymap.set("n", "<Esc>", "<cmd>nohlsearch<cr>", { desc = "Clear search highlight" })

-- 更好的缩进 / Better indentation
vim.keymap.set("v", "<", "<gv", { desc = "Indent left" })
vim.keymap.set("v", ">", ">gv", { desc = "Indent right" })

-- 移动行 / Move lines
vim.keymap.set("v", "J", "<cmd>m '>+1<cr>gv=gv", { desc = "Move line down" })
vim.keymap.set("v", "K", "<cmd>m '<-2<cr>gv=gv", { desc = "Move line up" })

-- 保持光标居中 / Keep cursor centered
vim.keymap.set("n", "<C-d>", "<C-d>zz", { desc = "Scroll down" })
vim.keymap.set("n", "<C-u>", "<C-u>zz", { desc = "Scroll up" })
vim.keymap.set("n", "n", "nzzzv", { desc = "Next search result" })
vim.keymap.set("n", "N", "Nzzzv", { desc = "Previous search result" })

-- ============================================================
-- 插件配置 / Plugin Configuration
-- ============================================================

-- 安装 lazy.nvim 插件管理器 / Install lazy.nvim plugin manager
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable",
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

-- 加载插件 / Load plugins
require("lazy").setup("plugins", {
  change_detection = {
    notify = false,
  },
})
```

## 插件管理 / Plugin Management

### lazy.nvim 插件管理器 / lazy.nvim Plugin Manager

```lua
-- ~/.config/nvim/lua/plugins/init.lua
-- 插件列表 / Plugin List

return {
  -- 主题 / Theme
  {
    "olimorris/onedarkpro.nvim",
    priority = 1000,
    config = function()
      vim.cmd.colorscheme "onedark"
    end,
  },

  -- 状态栏 / Status line
  {
    "nvim-lualine/lualine.nvim",
    dependencies = { "nvim-tree/nvim-web-devicons" },
    config = function()
      require("lualine").setup({
        options = {
          theme = "onedark",
        },
      })
    end,
  },

  -- 标签栏 / Tab line
  {
    "akinsho/bufferline.nvim",
    dependencies = { "nvim-tree/nvim-web-devicons" },
    config = function()
      require("bufferline").setup()
    end,
  },

  -- 文件浏览 / File explorer
  {
    "nvim-tree/nvim-tree.lua",
    dependencies = { "nvim-tree/nvim-web-devicons" },
    config = function()
      require("nvim-tree").setup()
    end,
  },

  -- 模糊查找 / Fuzzy finder
  {
    "nvim-telescope/telescope.nvim",
    branch = "0.1.x",
    dependencies = {
      "nvim-lua/plenary.nvim",
      { "nvim-telescope/telescope-fzf-native.nvim", build = "make" },
    },
    config = function()
      require("telescope").setup()
      pcall(require("telescope").load_extension, "fzf")
    end,
  },

  -- LSP 配置 / LSP configuration
  {
    "neovim/nvim-lspconfig",
    dependencies = {
      "williamboman/mason.nvim",
      "williamboman/mason-lspconfig.nvim",
      "hrsh7th/cmp-nvim-lsp",
    },
    config = function()
      require("config.lsp")
    end,
  },

  -- 代码补全 / Code completion
  {
    "hrsh7th/nvim-cmp",
    dependencies = {
      "hrsh7th/cmp-nvim-lsp",
      "hrsh7th/cmp-buffer",
      "hrsh7th/cmp-path",
      "L3MON4D3/LuaSnip",
      "saadparwaiz1/cmp_luasnip",
      "rafamadriz/friendly-snippets",
    },
    config = function()
      require("config.cmp")
    end,
  },

  -- 语法高亮 / Syntax highlighting
  {
    "nvim-treesitter/nvim-treesitter",
    build = ":TSUpdate",
    config = function()
      require("nvim-treesitter.configs").setup({
        ensure_installed = {
          "lua", "vim", "vimdoc", "javascript", "typescript",
          "python", "rust", "go", "html", "css", "json", "yaml",
          "markdown", "bash", "dockerfile", "gitignore",
        },
        auto_install = true,
        highlight = { enable = true },
        indent = { enable = true },
      })
    end,
  },

  -- Git 集成 / Git integration
  {
    "lewis6991/gitsigns.nvim",
    config = function()
      require("gitsigns").setup()
    end,
  },

  -- 自动括号 / Auto brackets
  {
    "windwp/nvim-autopairs",
    config = function()
      require("nvim-autopairs").setup()
    end,
  },

  -- 注释 / Comments
  {
    "numToStr/Comment.nvim",
    config = function()
      require("Comment").setup()
    end,
  },

  -- 缩进线 / Indent guides
  {
    "lukas-reineke/indent-blankline.nvim",
    main = "ibl",
    config = function()
      require("ibl").setup()
    end,
  },

  -- TODO 高亮 / TODO highlighting
  {
    "folke/todo-comments.nvim",
    dependencies = { "nvim-lua/plenary.nvim" },
    config = function()
      require("todo-comments").setup()
    end,
  },

  -- 终端 / Terminal
  {
    "akinsho/toggleterm.nvim",
    config = function()
      require("toggleterm").setup({
        open_mapping = [[<c-\>]],
        direction = "float",
      })
    end,
  },

  -- 通知 / Notifications
  {
    "rcarriga/nvim-notify",
    config = function()
      vim.notify = require("notify")
    end,
  },

  -- 启动页 / Start screen
  {
    "goolord/alpha-nvim",
    dependencies = { "nvim-tree/nvim-web-devicons" },
    config = function()
      require("alpha").setup(require("alpha.themes.startify").config)
    end,
  },
}
```

## LSP 配置 / LSP Configuration

### LSP 基础配置 / LSP Basic Configuration

```lua
-- ~/.config/nvim/lua/config/lsp.lua
-- LSP 配置 / LSP Configuration

-- 安装 Mason / Install Mason
require("mason").setup()
require("mason-lspconfig").setup({
  ensure_installed = {
    "lua_ls",
    "ts_ls",
    "pyright",
    "rust_analyzer",
    "gopls",
    "html",
    "cssls",
    "jsonls",
    "yamlls",
    "bashls",
  },
})

-- 获取 LSP 能力 / Get LSP capabilities
local capabilities = require("cmp_nvim_lsp").default_capabilities()

-- LSP 服务器配置 / LSP server configurations
local lspconfig = require("lspconfig")

-- Lua LSP / Lua LSP
lspconfig.lua_ls.setup({
  capabilities = capabilities,
  settings = {
    Lua = {
      runtime = { version = "LuaJIT" },
      workspace = { checkThirdParty = false },
      telemetry = { enable = false },
      diagnostics = { globals = { "vim" } },
    },
  },
})

-- TypeScript LSP / TypeScript LSP
lspconfig.ts_ls.setup({
  capabilities = capabilities,
})

-- Python LSP / Python LSP
lspconfig.pyright.setup({
  capabilities = capabilities,
})

-- Rust LSP / Rust LSP
lspconfig.rust_analyzer.setup({
  capabilities = capabilities,
  settings = {
    ["rust-analyzer"] = {
      checkOnSave = {
        command = "clippy",
      },
    },
  },
})

-- Go LSP / Go LSP
lspconfig.gopls.setup({
  capabilities = capabilities,
})

-- HTML LSP / HTML LSP
lspconfig.html.setup({
  capabilities = capabilities,
})

-- CSS LSP / CSS LSP
lspconfig.cssls.setup({
  capabilities = capabilities,
})

-- JSON LSP / JSON LSP
lspconfig.jsonls.setup({
  capabilities = capabilities,
})

-- YAML LSP / YAML LSP
lspconfig.yamlls.setup({
  capabilities = capabilities,
})

-- Bash LSP / Bash LSP
lspconfig.bashls.setup({
  capabilities = capabilities,
})

-- LSP 快捷键 / LSP keybindings
vim.api.nvim_create_autocmd("LspAttach", {
  group = vim.api.nvim_create_augroup("UserLspConfig", {}),
  callback = function(ev)
    local opts = { buffer = ev.buf }

    vim.keymap.set("n", "gd", vim.lsp.buf.definition, opts)
    vim.keymap.set("n", "gD", vim.lsp.buf.declaration, opts)
    vim.keymap.set("n", "gr", vim.lsp.buf.references, opts)
    vim.keymap.set("n", "gi", vim.lsp.buf.implementation, opts)
    vim.keymap.set("n", "K", vim.lsp.buf.hover, opts)
    vim.keymap.set("n", "<leader>rn", vim.lsp.buf.rename, opts)
    vim.keymap.set("n", "<leader>ca", vim.lsp.buf.code_action, opts)
    vim.keymap.set("n", "<leader>f", function()
      vim.lsp.buf.format({ async = true })
    end, opts)
    vim.keymap.set("n", "[d", vim.diagnostic.goto_prev, opts)
    vim.keymap.set("n", "]d", vim.diagnostic.goto_next, opts)
    vim.keymap.set("n", "<leader>d", vim.diagnostic.open_float, opts)
  end,
})
```

## 代码补全 / Code Completion

### nvim-cmp 配置 / nvim-cmp Configuration

```lua
-- ~/.config/nvim/lua/config/cmp.lua
-- 代码补全配置 / Code Completion Configuration

local cmp = require("cmp")
local luasnip = require("luasnip")

-- 加载代码片段 / Load snippets
require("luasnip.loaders.from_vscode").lazy_load()

cmp.setup({
  snippet = {
    expand = function(args)
      luasnip.lsp_expand(args.body)
    end,
  },

  mapping = cmp.mapping.preset.insert({
    ["<C-n>"] = cmp.mapping.select_next_item(),
    ["<C-p>"] = cmp.mapping.select_prev_item(),
    ["<C-b>"] = cmp.mapping.scroll_docs(-4),
    ["<C-f>"] = cmp.mapping.scroll_docs(4),
    ["<C-Space>"] = cmp.mapping.complete(),
    ["<C-e>"] = cmp.mapping.abort(),
    ["<CR>"] = cmp.mapping.confirm({ select = true }),
    ["<Tab>"] = cmp.mapping(function(fallback)
      if cmp.visible() then
        cmp.select_next_item()
      elseif luasnip.expand_or_jumpable() then
        luasnip.expand_or_jump()
      else
        fallback()
      end
    end, { "i", "s" }),
    ["<S-Tab>"] = cmp.mapping(function(fallback)
      if cmp.visible() then
        cmp.select_prev_item()
      elseif luasnip.jumpable(-1) then
        luasnip.jump(-1)
      else
        fallback()
      end
    end, { "i", "s" }),
  }),

  sources = cmp.config.sources({
    { name = "nvim_lsp" },
    { name = "luasnip" },
    { name = "path" },
  }, {
    { name = "buffer" },
  }),
})
```

## 模糊查找 / Fuzzy Finding

### Telescope 配置 / Telescope Configuration

```lua
-- ~/.config/nvim/lua/config/telescope.lua
-- 模糊查找配置 / Fuzzy Finding Configuration

local telescope = require("telescope")
local builtin = require("telescope.builtin")

telescope.setup({
  defaults = {
    file_ignore_patterns = {
      "node_modules",
      ".git",
      "dist",
      "build",
      ".next",
    },
  },
  pickers = {
    find_files = {
      hidden = true,
    },
    live_grep = {
      additional_args = function()
        return { "--hidden" }
      end,
    },
  },
})

-- 快捷键 / Keybindings
vim.keymap.set("n", "<leader>ff", builtin.find_files, { desc = "Find files" })
vim.keymap.set("n", "<leader>fg", builtin.live_grep, { desc = "Live grep" })
vim.keymap.set("n", "<leader>fb", builtin.buffers, { desc = "Find buffers" })
vim.keymap.set("n", "<leader>fh", builtin.help_tags, { desc = "Find help" })
vim.keymap.set("n", "<leader>fr", builtin.oldfiles, { desc = "Recent files" })
vim.keymap.set("n", "<leader>fd", builtin.diagnostics, { desc = "Find diagnostics" })
vim.keymap.set("n", "<leader>fs", builtin.git_status, { desc = "Git status" })
vim.keymap.set("n", "<leader>fc", builtin.git_commits, { desc = "Git commits" })
```

## 文件浏览 / File Explorer

### nvim-tree 配置 / nvim-tree Configuration

```lua
-- ~/.config/nvim/lua/config/nvim-tree.lua
-- 文件浏览配置 / File Explorer Configuration

require("nvim-tree").setup({
  sort_by = "case_sensitive",
  view = {
    width = 30,
  },
  renderer = {
    group_empty = true,
  },
  filters = {
    dotfiles = false,
    custom = { "^.git$" },
  },
  git = {
    enable = true,
    ignore = false,
  },
})

-- 快捷键 / Keybindings
vim.keymap.set("n", "<leader>e", "<cmd>NvimTreeToggle<cr>", { desc = "Toggle file explorer" })
vim.keymap.set("n", "<leader>ef", "<cmd>NvimTreeFindFile<cr>", { desc = "Find file in explorer" })
```

## Git 集成 / Git Integration

### gitsigns 配置 / gitsigns Configuration

```lua
-- ~/.config/nvim/lua/config/gitsigns.lua
-- Git 集成配置 / Git Integration Configuration

require("gitsigns").setup({
  signs = {
    add = { text = "│" },
    change = { text = "│" },
    delete = { text = "_" },
    topdelete = { text = "‾" },
    changedelete = { text = "~" },
    untracked = { text = "┆" },
  },
  on_attach = function(bufnr)
    local gs = package.loaded.gitsigns

    local function map(mode, l, r, opts)
      opts = opts or {}
      opts.buffer = bufnr
      vim.keymap.set(mode, l, r, opts)
    end

    -- 导航 / Navigation
    map("n", "]c", function()
      if vim.wo.diff then return "]c" end
      vim.schedule(function() gs.next_hunk() end)
      return "<Ignore>"
    end, { expr = true })

    map("n", "[c", function()
      if vim.wo.diff then return "[c" end
      vim.schedule(function() gs.prev_hunk() end)
      return "<Ignore>"
    end, { expr = true })

    -- 操作 / Actions
    map("n", "<leader>hs", gs.stage_hunk, { desc = "Stage hunk" })
    map("n", "<leader>hr", gs.reset_hunk, { desc = "Reset hunk" })
    map("v", "<leader>hs", function() gs.stage_hunk {vim.fn.line("."), vim.fn.line("v")} end)
    map("v", "<leader>hr", function() gs.reset_hunk {vim.fn.line("."), vim.fn.line("v")} end)
    map("n", "<leader>hS", gs.stage_buffer, { desc = "Stage buffer" })
    map("n", "<leader>hu", gs.undo_stage_hunk, { desc = "Undo stage hunk" })
    map("n", "<leader>hR", gs.reset_buffer, { desc = "Reset buffer" })
    map("n", "<leader>hp", gs.preview_hunk, { desc = "Preview hunk" })
    map("n", "<leader>hb", function() gs.blame_line{full=true} end, { desc = "Blame line" })
    map("n", "<leader>hd", gs.diffthis, { desc = "Diff this" })
  end,
})
```

## 主题和外观 / Theme and Appearance

### OneDark Pro 主题 / OneDark Pro Theme

```lua
-- ~/.config/nvim/lua/config/theme.lua
-- 主题配置 / Theme Configuration

require("onedarkpro").setup({
  colors = {
    dark = {
      bg = "#282c34",
      fg = "#abb2bf",
    },
  },
  styles = {
    types = "NONE",
    methods = "NONE",
    numbers = "NONE",
    strings = "NONE",
    comments = "italic",
    keywords = "bold",
    constants = "NONE",
    functions = "italic",
    operators = "NONE",
    variables = "NONE",
    parameters = "NONE",
    conditionals = "italic",
    virtual_text = "NONE",
  },
})

vim.cmd.colorscheme "onedark"
```

### 状态栏配置 / Status Line Configuration

```lua
-- ~/.config/nvim/lua/config/lualine.lua
-- 状态栏配置 / Status Line Configuration

require("lualine").setup({
  options = {
    theme = "onedark",
    component_separators = { left = "", right = "" },
    section_separators = { left = "", right = "" },
  },
  sections = {
    lualine_a = { "mode" },
    lualine_b = { "branch", "diff", "diagnostics" },
    lualine_c = { "filename" },
    lualine_x = { "encoding", "fileformat", "filetype" },
    lualine_y = { "progress" },
    lualine_z = { "location" },
  },
})
```

## 快捷键配置 / Keybinding Configuration

### 常用快捷键 / Common Keybindings

| 功能 / Function | 快捷键 / Keybinding | 模式 / Mode |
|----------------|---------------------|-------------|
| 保存 / Save | `<leader>w` | Normal |
| 退出 / Quit | `<leader>q` | Normal |
| 文件查找 / Find files | `<leader>ff` | Normal |
| 全局搜索 / Global search | `<leader>fg` | Normal |
| 文件浏览器 / File explorer | `<leader>e` | Normal |
| 切换终端 / Toggle terminal | `Ctrl+\` | Normal |
| 注释切换 / Toggle comment | `gcc` | Normal |
| 代码格式化 / Format code | `<leader>f` | Normal |
| 跳转到定义 / Go to definition | `gd` | Normal |
| 查看引用 / View references | `gr` | Normal |
| 重命名 / Rename | `<leader>rn` | Normal |
| 代码操作 / Code actions | `<leader>ca` | Normal |
| 下一个诊断 / Next diagnostic | `]d` | Normal |
| 上一个诊断 / Previous diagnostic | `[d` | Normal |

### 快捷键配置文件 / Keybinding Configuration File

```lua
-- ~/.config/nvim/lua/config/keymaps.lua
-- 快捷键配置 / Keybinding Configuration

local map = vim.keymap.set

-- 基础快捷键 / Basic keybindings
map("n", "<leader>w", "<cmd>w<cr>", { desc = "Save" })
map("n", "<leader>q", "<cmd>q<cr>", { desc = "Quit" })
map("n", "<leader>Q", "<cmd>qa!<cr>", { desc = "Force quit" })

-- 窗口管理 / Window management
map("n", "<leader>sv", "<cmd>vsplit<cr>", { desc = "Vertical split" })
map("n", "<leader>sh", "<cmd>split<cr>", { desc = "Horizontal split" })
map("n", "<leader>sc", "<cmd>close<cr>", { desc = "Close window" })

-- 缓冲区管理 / Buffer management
map("n", "<leader>bn", "<cmd>bnext<cr>", { desc = "Next buffer" })
map("n", "<leader>bp", "<cmd>bprevious<cr>", { desc = "Previous buffer" })
map("n", "<leader>bd", "<cmd>bdelete<cr>", { desc = "Delete buffer" })

-- 标签页管理 / Tab management
map("n", "<leader>tn", "<cmd>tabnew<cr>", { desc = "New tab" })
map("n", "<leader>tc", "<cmd>tabclose<cr>", { desc = "Close tab" })
map("n", "<leader>to", "<cmd>tabonly<cr>", { desc = "Close other tabs" })

-- 终端 / Terminal
map("n", "<leader>tt", "<cmd>ToggleTerm<cr>", { desc = "Toggle terminal" })
map("t", "<Esc>", [[<C-\><C-n>]], { desc = "Exit terminal mode" })
```

## 自定义选项 / Customization Options

### 选项配置 / Options Configuration

```lua
-- ~/.config/nvim/lua/config/options.lua
-- 选项配置 / Options Configuration

local opt = vim.opt

-- 行号 / Line numbers
opt.number = true
opt.relativenumber = true

-- 缩进 / Indentation
opt.tabstop = 2
opt.shiftwidth = 2
opt.expandtab = true
opt.autoindent = true
opt.smartindent = true

-- 搜索 / Search
opt.hlsearch = true
opt.incsearch = true
opt.ignorecase = true
opt.smartcase = true

-- 外观 / Appearance
opt.termguicolors = true
opt.signcolumn = "yes"
opt.scrolloff = 8
opt.sidescrolloff = 8
opt.wrap = false
opt.cursorline = true

-- 分割窗口 / Split windows
opt.splitbelow = true
opt.splitright = true

-- 撤销 / Undo
opt.undofile = true
opt.undodir = os.getenv("HOME") .. "/.vim/undodir"

-- 剪贴板 / Clipboard
opt.clipboard = "unnamedplus"

-- 鼠标 / Mouse
opt.mouse = "a"

-- 完成 / Completion
opt.completeopt = { "menu", "menuone", "noselect" }

-- 更新时间 / Update time
opt.updatetime = 250
opt.timeoutlen = 300

-- 隐藏字符 / Hidden characters
opt.list = true
opt.listchars = { tab = "» ", trail = "·", nbsp = "␣" }

-- 全局状态行 / Global statusline
opt.laststatus = 3
```

## 常见问题 / Common Issues

### 1. 插件不加载 / Plugin not loading

**问题 / Problem**: 插件已安装但不加载

**解决方案 / Solution**:
```bash
# 1. 检查插件状态 / Check plugin status
:Lazy

# 2. 同步插件 / Sync plugins
:Lazy sync

# 3. 检查配置文件 / Check configuration files
:checkhealth
```

### 2. LSP 不工作 / LSP not working

**问题 / Problem**: LSP 服务器不启动

**解决方案 / Solution**:
```bash
# 1. 检查 LSP 状态 / Check LSP status
:LspInfo

# 2. 安装 LSP 服务器 / Install LSP server
:Mason

# 3. 检查日志 / Check logs
:messages
```

### 3. 性能问题 / Performance issues

**问题 / Problem**: Neovim 运行缓慢

**解决方案 / Solution**:
```lua
-- 1. 禁用不需要的插件 / Disable unnecessary plugins
-- 在 plugins/init.lua 中注释掉不需要的插件

-- 2. 优化配置 / Optimize configuration
vim.opt.updatetime = 1000  -- 增加更新时间 / Increase update time
vim.opt.timeoutlen = 500   -- 增加超时时间 / Increase timeout

-- 3. 使用懒加载 / Use lazy loading
{
  "plugin/name",
  event = "VeryLazy",  -- 懒加载 / Lazy load
}
```

### 4. 键位冲突 / Keybinding conflicts

**问题 / Problem**: 快捷键冲突

**解决方案 / Solution**:
```bash
# 1. 查看当前键位映射 / View current key mappings
:map
:nmap
:vmap
:imap

# 2. 检查特定键位 / Check specific key
:verbose map <leader>f

# 3. 删除冲突的键位映射 / Delete conflicting key mapping
:unmap <leader>f
```

## 参考资源 / References

### 官方资源 / Official Resources

- [Neovim 官网](https://neovim.io/)
- [Neovim 文档](https://neovim.io/doc/)
- [Neovim API](https://neovim.io/doc/user/api.html)

### 推荐阅读 / Recommended Reading

- [Neovim 配置指南](https://neovim.io/doc/user/quickstart.html)
- [lazy.nvim 文档](https://github.com/folke/lazy.nvim)
- [nvim-lspconfig 文档](https://github.com/neovim/nvim-lspconfig)

### 社区资源 / Community Resources

- [Awesome Neovim](https://github.com/rockerBOO/awesome-neovim)
- [Neovimcraft](https://neovimcraft.com/)
- [Nvim Setup](https://nvimsetup.com/)

---

**相关配置 / Related Configs**
- [Zsh 配置 / Zsh Configuration](zshrc.md)
- [Git 配置 / Git Configuration](gitconfig.md)
- [VS Code 配置 / VS Code Configuration](vscode-settings.md)
- [Tmux 配置 / Tmux Configuration](tmux.md)
