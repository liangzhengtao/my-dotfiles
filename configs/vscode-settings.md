# VS Code 配置指南 / VS Code Configuration Guide

[返回目录 / Back to Index](../README.md)

## 目录 / Table of Contents

- [简介 / Introduction](#简介--introduction)
- [配置文件 / Configuration File](#配置文件--configuration-file)
- [基本设置 / Basic Settings](#基本设置--basic-settings)
- [编辑器设置 / Editor Settings](#编辑器设置--editor-settings)
- [工作区设置 / Workspace Settings](#工作区设置--workspace-settings)
- [扩展推荐 / Extension Recommendations](#扩展推荐--extension-recommendations)
- [快捷键配置 / Keybinding Configuration](#快捷键配置--keybinding-configuration)
- [代码片段 / Code Snippets](#代码片段--code-snippets)
- [自定义选项 / Customization Options](#自定义选项--customization-options)
- [常见问题 / Common Issues](#常见问题--common-issues)
- [参考资源 / References](#参考资源--references)

## 简介 / Introduction

Visual Studio Code 是一个轻量级但功能强大的源代码编辑器，支持多种编程语言和丰富的扩展生态系统。

Visual Studio Code is a lightweight but powerful source code editor that supports multiple programming languages and a rich extension ecosystem.

### 为什么选择 VS Code？ / Why Choose VS Code?

- 🚀 **轻量级** - 启动速度快，资源占用少
- 🎨 **高度可定制** - 主题、快捷键、扩展等
- 🔌 **丰富的扩展** - 海量扩展支持各种语言和框架
- 🐛 **强大的调试** - 内置调试器支持多种语言
- 📝 **智能提示** - IntelliSense 代码补全

- 🚀 **Lightweight** - Fast startup, low resource usage
- 🎨 **Highly Customizable** - Themes, keybindings, extensions, etc.
- 🔌 **Rich Extensions** - Massive extensions for various languages and frameworks
- 🐛 **Powerful Debugging** - Built-in debugger supporting multiple languages
- 📝 **Smart Suggestions** - IntelliSense code completion

## 配置文件 / Configuration File

### 完整配置 / Full Configuration

```json
{
  // ============================================================
  // 基本设置 / Basic Settings
  // ============================================================
  
  // 编辑器设置 / Editor settings
  "editor.fontSize": 14,
  "editor.fontFamily": "'Fira Code', 'Cascadia Code', Consolas, monospace",
  "editor.fontLigatures": true,
  "editor.lineHeight": 22,
  "editor.letterSpacing": 0.5,
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.detectIndentation": true,
  "editor.renderWhitespace": "boundary",
  "editor.cursorBlinking": "smooth",
  "editor.cursorSmoothCaretAnimation": "on",
  "editor.smoothScrolling": true,
  "editor.mouseWheelZoom": true,
  "editor.minimap.enabled": true,
  "editor.minimap.side": "right",
  "editor.minimap.renderCharacters": false,
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": true,
  "editor.linkedEditing": true,
  "editor.stickyScroll.enabled": true,
  
  // 工作台设置 / Workbench settings
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "workbench.startupEditor": "none",
  "workbench.editor.enablePreview": false,
  "workbench.editor.enablePreviewFromQuickOpen": false,
  "workbench.editor.labelFormat": "short",
  "workbench.tree.indent": 16,
  "workbench.list.smoothScrolling": true,
  "workbench.sideBar.location": "left",
  "workbench.panel.defaultLocation": "bottom",
  
  // 窗口设置 / Window settings
  "window.zoomLevel": 0,
  "window.titleBarStyle": "custom",
  "window.title": "${dirty}${activeEditorShort}${separator}${rootName}",
  "window.newWindowDimensions": "inherit",
  "window.restoreWindows": "all",
  
  // 终端设置 / Terminal settings
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.fontFamily": "'Fira Code', 'Cascadia Code', Consolas, monospace",
  "terminal.integrated.lineHeight": 1.2,
  "terminal.integrated.scrollback": 10000,
  "terminal.integrated.cursorBlinking": true,
  "terminal.integrated.cursorStyle": "line",
  "terminal.integrated.enableMultiLinePasteWarning": false,
  "terminal.integrated.defaultProfile.windows": "Git Bash",
  "terminal.integrated.profiles.windows": {
    "Git Bash": {
      "path": "C:\\Program Files\\Git\\bin\\bash.exe",
      "icon": "terminal-bash"
    },
    "PowerShell": {
      "source": "PowerShell",
      "icon": "terminal-powershell"
    },
    "Command Prompt": {
      "path": "C:\\WINDOWS\\System32\\cmd.exe",
      "icon": "terminal-cmd"
    }
  },
  
  // ============================================================
  // 编辑器高级设置 / Editor Advanced Settings
  // ============================================================
  
  // 文件设置 / File settings
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "files.encoding": "utf8",
  "files.eol": "\n",
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,
  "files.trimFinalNewlines": true,
  "files.exclude": {
    "**/.git": true,
    "**/.DS_Store": true,
    "**/node_modules": true,
    "**/__pycache__": true,
    "**/.pytest_cache": true,
    "**/.mypy_cache": true,
    "**/.ruff_cache": true,
    "**/dist": true,
    "**/build": true,
    "**/.next": true,
    "**/coverage": true
  },
  "files.watcherExclude": {
    "**/node_modules/**": true,
    "**/.git/objects/**": true,
    "**/.git/subtree-cache/**": true,
    "**/dist/**": true,
    "**/build/**": true
  },
  
  // 搜索设置 / Search settings
  "search.exclude": {
    "**/node_modules": true,
    "**/dist": true,
    "**/build": true,
    "**/coverage": true,
    "**/.git": true,
    "**/.DS_Store": true,
    "**/package-lock.json": true,
    "**/yarn.lock": true,
    "**/pnpm-lock.yaml": true
  },
  
  // ============================================================
  // 语言特定设置 / Language-Specific Settings
  // ============================================================
  
  // JavaScript/TypeScript / JavaScript/TypeScript
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": "explicit",
      "source.organizeImports": "explicit"
    }
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": "explicit",
      "source.organizeImports": "explicit"
    }
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": "explicit",
      "source.organizeImports": "explicit"
    }
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": "explicit",
      "source.organizeImports": "explicit"
    }
  },
  
  // Python / Python
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll.ruff": "explicit",
      "source.organizeImports": "explicit"
    },
    "editor.rulers": [88],
    "editor.wordWrap": "off"
  },
  "python.analysis.typeCheckingMode": "basic",
  "python.analysis.autoImportCompletions": true,
  "python.analysis.diagnosticMode": "workspace",
  
  // HTML/CSS / HTML/CSS
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  
  // Markdown / Markdown
  "[markdown]": {
    "editor.defaultFormatter": "yzhang.markdown-all-in-one",
    "editor.wordWrap": "on",
    "editor.formatOnSave": false
  },
  
  // YAML / YAML
  "[yaml]": {
    "editor.defaultFormatter": "redhat.vscode-yaml",
    "editor.formatOnSave": true
  },
  
  // ============================================================
  // 扩展设置 / Extension Settings
  // ============================================================
  
  // ESLint / ESLint
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ],
  "eslint.alwaysShowStatus": true,
  "eslint.format.enable": true,
  "eslint.lintTask.enable": true,
  
  // Prettier / Prettier
  "prettier.requireConfig": true,
  "prettier.useEditorConfig": true,
  
  // GitLens / GitLens
  "gitlens.hovers.currentLine.over": "line",
  "gitlens.currentLine.enabled": true,
  "gitlens.currentLine.format": "${author}, ${date}",
  "gitlens.codeLens.enabled": true,
  "gitlens.codeLens.recentChange.enabled": true,
  "gitlens.codeLens.authors.enabled": true,
  
  // Error Lens / Error Lens
  "errorLens.enabledDiagnosticLevels": ["error", "warning"],
  "errorLens.delay": 500,
  "errorLens.gutterIconsEnabled": true,
  
  // indent-rainbow / indent-rainbow
  "indentRainbow.colors": [
    "rgba(255,255,64,0.07)",
    "rgba(127,255,127,0.07)",
    "rgba(255,127,255,0.07)",
    "rgba(79,193,255,0.07)"
  ],
  
  // TODO Highlight / TODO Highlight
  "todohighlight.keywords": [
    {
      "text": "TODO:",
      "color": "#fff",
      "backgroundColor": "#ffbd2a",
      "overviewRulerColor": "#ffbd2a"
    },
    {
      "text": "FIXME:",
      "color": "#fff",
      "backgroundColor": "#f06292",
      "overviewRulerColor": "#f06292"
    },
    {
      "text": "NOTE:",
      "color": "#fff",
      "backgroundColor": "#4fc3f7",
      "overviewRulerColor": "#4fc3f7"
    },
    {
      "text": "HACK:",
      "color": "#fff",
      "backgroundColor": "#ff7043",
      "overviewRulerColor": "#ff7043"
    }
  ],
  
  // Live Server / Live Server
  "liveServer.settings.port": 5500,
  "liveServer.settings.root": "/",
  "liveServer.settings.CustomBrowser": "chrome",
  "liveServer.settings.donotShowInfoMsg": true,
  
  // Docker / Docker
  "docker.showStartPage": false,
  
  // Kubernetes / Kubernetes
  "vscode-kubernetes.minikube-show-info": false,
  
  // Remote - SSH / Remote - SSH
  "remote.SSH.defaultForwardedPorts": [],
  
  // ============================================================
  // 其他设置 / Other Settings
  // ============================================================
  
  // 面包屑导航 / Breadcrumb navigation
  "breadcrumbs.enabled": true,
  "breadcrumbs.symbolPath": "on",
  
  // 遥测 / Telemetry
  "telemetry.telemetryLevel": "off",
  
  // 更新 / Update
  "update.mode": "manual",
  "update.showReleaseNotes": false,
  
  // 调试 / Debug
  "debug.console.fontSize": 13,
  "debug.console.fontFamily": "'Fira Code', Consolas, monospace",
  
  // Git / Git
  "git.enableSmartCommit": true,
  "git.autofetch": true,
  "git.confirmSync": false,
  "git.allowForcePush": true,
  
  // 同步设置 / Sync settings
  "settingsSync.keybindingsPerPlatform": true,
  
  // 工作区信任 / Workspace trust
  "security.workspace.trust.enabled": true,
  "security.workspace.trust.untrustedFiles": "prompt"
}
```

## 基本设置 / Basic Settings

### 编辑器字体 / Editor Font

```json
{
  "editor.fontSize": 14,
  "editor.fontFamily": "'Fira Code', 'Cascadia Code', Consolas, monospace",
  "editor.fontLigatures": true,
  "editor.lineHeight": 22,
  "editor.letterSpacing": 0.5
}
```

### 推荐字体 / Recommended Fonts

- **Fira Code** - 连字支持 / Ligature support
- **Cascadia Code** - 微软出品，连字支持 / Microsoft, ligature support
- **JetBrains Mono** - JetBrains 出品 / JetBrains
- **Source Code Pro** - Adobe 出品 / Adobe

### 主题推荐 / Recommended Themes

- **One Dark Pro** - Atom 风格 / Atom style
- **Dracula** - 暗色主题 / Dark theme
- **GitHub Theme** - GitHub 风格 / GitHub style
- **Monokai Pro** - 经典主题 / Classic theme
- **Ayu** - 简洁主题 / Minimal theme

## 编辑器设置 / Editor Settings

### 自动保存 / Auto Save

```json
{
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000
}
```

选项 / Options:
- `off` - 关闭自动保存 / Disable auto save
- `afterDelay` - 延迟后保存 / Save after delay
- `onFocusChange` - 焦点变化时保存 / Save on focus change
- `onWindowChange` - 窗口变化时保存 / Save on window change

### 格式化 / Formatting

```json
{
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.formatOnType": false,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

### 代码折叠 / Code Folding

```json
{
  "editor.folding": true,
  "editor.foldingStrategy": "auto",
  "editor.showFoldingControls": "mouseover",
  "editor.foldStyle": "auto"
}
```

## 工作区设置 / Workspace Settings

### 工作区配置文件 / Workspace Configuration File

```json
// .vscode/settings.json (项目根目录)
{
  "editor.tabSize": 2,
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "files.exclude": {
    "**/node_modules": true,
    "**/dist": true,
    "**/.next": true
  },
  "search.exclude": {
    "**/node_modules": true,
    "**/dist": true,
    "**/.next": true,
    "**/package-lock.json": true
  }
}
```

### 推荐扩展文件 / Recommended Extensions File

```json
// .vscode/extensions.json (项目根目录)
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "dbaeumer.vscode-eslint",
    "ms-python.python",
    "ms-python.vscode-pylance",
    "bradlc.vscode-tailwindcss",
    "prisma.prisma",
    "graphql.vscode-graphql"
  ],
  "unwantedRecommendations": [
    "hookyqr.beautify",
    "michelemelluso.code-beautifier"
  ]
}
```

## 扩展推荐 / Extension Recommendations

### 必装扩展 / Essential Extensions

| 扩展 / Extension | 说明 / Description |
|-----------------|-------------------|
| ESLint | JavaScript/TypeScript 代码检查 / JS/TS linting |
| Prettier | 代码格式化 / Code formatting |
| GitLens | Git 增强工具 / Git enhancement |
| Error Lens | 内联错误显示 / Inline error display |
| indent-rainbow | 缩进彩虹色 / Indent rainbow colors |
| TODO Highlight | TODO 高亮 / TODO highlighting |
| Material Icon Theme | 文件图标主题 / File icon theme |
| One Dark Pro | 编辑器主题 / Editor theme |

### 语言扩展 / Language Extensions

| 扩展 / Extension | 说明 / Description |
|-----------------|-------------------|
| Python | Python 语言支持 / Python support |
| Pylance | Python 语言服务器 / Python language server |
| Black Formatter | Python 格式化 / Python formatting |
| Ruff | Python 代码检查 / Python linting |
| TypeScript | TypeScript 支持 / TypeScript support |
| JavaScript | JavaScript 支持 / JavaScript support |
| HTML CSS Support | HTML/CSS 支持 / HTML/CSS support |
| Auto Rename Tag | 自动重命名标签 / Auto rename tag |

### 框架扩展 / Framework Extensions

| 扩展 / Extension | 说明 / Description |
|-----------------|-------------------|
| Vue - Official | Vue.js 支持 / Vue.js support |
| ES7+ React Snippets | React 代码片段 / React snippets |
| Angular Language Service | Angular 支持 / Angular support |
| Svelte for VS Code | Svelte 支持 / Svelte support |
| Tailwind CSS IntelliSense | Tailwind CSS 支持 / Tailwind CSS support |

### 工具扩展 / Tool Extensions

| 扩展 / Extension | 说明 / Description |
|-----------------|-------------------|
| Docker | Docker 支持 / Docker support |
| Kubernetes | Kubernetes 支持 / K8s support |
| Remote - SSH | 远程 SSH 开发 / Remote SSH development |
| Remote - WSL | WSL 开发 / WSL development |
| Live Server | 本地 HTTP 服务器 / Local HTTP server |
| REST Client | REST API 测试 / REST API testing |
| Thunder Client | API 测试工具 / API testing tool |

### 安装扩展命令 / Install Extension Commands

```bash
# 安装单个扩展 / Install single extension
code --install-extension esbenp.prettier-vscode

# 安装多个扩展 / Install multiple extensions
code --install-extension esbenp.prettier-vscode \
     --install-extension dbaeumer.vscode-eslint \
     --install-extension ms-python.python

# 列出已安装扩展 / List installed extensions
code --list-extensions

# 导出扩展列表 / Export extension list
code --list-extensions > extensions.txt

# 从文件安装扩展 / Install extensions from file
cat extensions.txt | xargs -L 1 code --install-extension
```

## 快捷键配置 / Keybinding Configuration

### 自定义快捷键 / Custom Keybindings

```json
// keybindings.json
[
  // 切换侧边栏 / Toggle sidebar
  {
    "key": "ctrl+b",
    "command": "workbench.action.toggleSidebarVisibility"
  },
  
  // 切换终端 / Toggle terminal
  {
    "key": "ctrl+`",
    "command": "workbench.action.terminal.toggleTerminal"
  },
  
  // 格式化文档 / Format document
  {
    "key": "shift+alt+f",
    "command": "editor.action.formatDocument"
  },
  
  // 保存所有文件 / Save all files
  {
    "key": "ctrl+shift+s",
    "command": "workbench.action.files.saveAll"
  },
  
  // 切换标签页 / Switch tab
  {
    "key": "ctrl+tab",
    "command": "workbench.action.quickOpenPreviousRecentlyUsedEditorInGroup"
  },
  
  // 向上复制行 / Copy line up
  {
    "key": "shift+alt+up",
    "command": "editor.action.copyLinesUpAction"
  },
  
  // 向下复制行 / Copy line down
  {
    "key": "shift+alt+down",
    "command": "editor.action.copyLinesDownAction"
  },
  
  // 向上移动行 / Move line up
  {
    "key": "alt+up",
    "command": "editor.action.moveLinesUpAction"
  },
  
  // 向下移动行 / Move line down
  {
    "key": "alt+down",
    "command": "editor.action.moveLinesDownAction"
  },
  
  // 删除行 / Delete line
  {
    "key": "ctrl+shift+k",
    "command": "editor.action.deleteLines"
  },
  
  // 注释切换 / Toggle comment
  {
    "key": "ctrl+/",
    "command": "editor.action.commentLine",
    "when": "editorTextFocus"
  },
  
  // 块注释 / Block comment
  {
    "key": "shift+alt+a",
    "command": "editor.action.blockComment",
    "when": "editorTextFocus"
  }
]
```

### 常用快捷键 / Common Keybindings

| 功能 / Function | Windows/Linux | macOS |
|----------------|---------------|-------|
| 命令面板 / Command Palette | Ctrl+Shift+P | Cmd+Shift+P |
| 快速打开 / Quick Open | Ctrl+P | Cmd+P |
| 切换侧边栏 / Toggle Sidebar | Ctrl+B | Cmd+B |
| 切换终端 / Toggle Terminal | Ctrl+` | Cmd+` |
| 格式化文档 / Format Document | Shift+Alt+F | Shift+Option+F |
| 保存所有 / Save All | Ctrl+Shift+S | Cmd+Shift+S |
| 跳转到行 / Go to Line | Ctrl+G | Cmd+G |
| 查找替换 / Find Replace | Ctrl+H | Cmd+H |
| 多光标 / Multi Cursor | Alt+Click | Option+Click |
| 选择所有出现 / Select All Occurrences | Ctrl+Shift+L | Cmd+Shift+L |

## 代码片段 / Code Snippets

### JavaScript/TypeScript 片段 / JavaScript/TypeScript Snippets

```json
// javascript.json
{
  "Print to console": {
    "prefix": "log",
    "body": [
      "console.log('$1');"
    ],
    "description": "Log output to console"
  },
  "Arrow Function": {
    "prefix": "af",
    "body": [
      "const ${1:functionName} = (${2:params}) => {",
      "\t$0",
      "};"
    ],
    "description": "Arrow function"
  },
  "Async Arrow Function": {
    "prefix": "aaf",
    "body": [
      "const ${1:functionName} = async (${2:params}) => {",
      "\t$0",
      "};"
    ],
    "description": "Async arrow function"
  },
  "Import": {
    "prefix": "imp",
    "body": [
      "import ${1:module} from '${2:package}';"
    ],
    "description": "Import module"
  }
}
```

### Python 片段 / Python Snippets

```json
// python.json
{
  "Print": {
    "prefix": "print",
    "body": [
      "print(${1:variable})"
    ],
    "description": "Print statement"
  },
  "Main Function": {
    "prefix": "main",
    "body": [
      "def main():",
      "\t$0",
      "",
      "",
      "if __name__ == '__main__':",
      "\tmain()"
    ],
    "description": "Main function"
  },
  "Class": {
    "prefix": "class",
    "body": [
      "class ${1:ClassName}:",
      "\tdef __init__(self${2:, params}):",
      "\t\t$0"
    ],
    "description": "Class definition"
  },
  "Try Except": {
    "prefix": "try",
    "body": [
      "try:",
      "\t$1",
      "except ${2:Exception} as e:",
      "\t$0"
    ],
    "description": "Try-except block"
  }
}
```

## 自定义选项 / Customization Options

### 工作区颜色 / Workspace Colors

```json
{
  "workbench.colorCustomizations": {
    // 编辑器 / Editor
    "editor.background": "#282c34",
    "editor.foreground": "#abb2bf",
    "editor.lineHighlightBackground": "#2c313c",
    "editor.selectionBackground": "#3e4451",
    "editor.inactiveSelectionBackground": "#3e4451",
    
    // 侧边栏 / Sidebar
    "sideBar.background": "#21252b",
    "sideBar.foreground": "#abb2bf",
    
    // 状态栏 / Status bar
    "statusBar.background": "#21252b",
    "statusBar.foreground": "#abb2bf",
    
    // 标签页 / Tabs
    "tab.activeBackground": "#282c34",
    "tab.activeForeground": "#ffffff",
    "tab.inactiveBackground": "#21252b",
    "tab.inactiveForeground": "#abb2bf"
  }
}
```

### 文件图标主题 / File Icon Theme

```json
{
  "workbench.iconTheme": "material-icon-theme",
  "material-icon-theme.folders.theme": "specific",
  "material-icon-theme.activeIconPack": "react"
}
```

## 常见问题 / Common Issues

### 1. 扩展不生效 / Extension not working

**问题 / Problem**: 安装扩展后不生效

**解决方案 / Solution**:
```bash
# 1. 重新加载窗口 / Reload window
Ctrl+Shift+P -> "Developer: Reload Window"

# 2. 检查扩展是否启用 / Check if extension is enabled
Ctrl+Shift+X -> 搜索扩展 / Search extension

# 3. 检查设置 / Check settings
Ctrl+, -> 搜索扩展设置 / Search extension settings
```

### 2. 格式化不工作 / Formatting not working

**问题 / Problem**: 保存时格式化不工作

**解决方案 / Solution**:
```json
// 1. 检查设置 / Check settings
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}

// 2. 检查语言特定设置 / Check language-specific settings
"[javascript]": {
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}

// 3. 检查 Prettier 配置文件 / Check Prettier config file
// .prettierrc
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2
}
```

### 3. 性能问题 / Performance issues

**问题 / Problem**: VS Code 运行缓慢

**解决方案 / Solution**:
```json
// 1. 禁用不需要的扩展 / Disable unnecessary extensions
// Ctrl+Shift+X -> 禁用 / Disable

// 2. 优化设置 / Optimize settings
{
  "editor.minimap.enabled": false,
  "editor.smoothScrolling": false,
  "editor.cursorBlinking": "solid",
  "editor.cursorSmoothCaretAnimation": "off"
}

// 3. 排除大文件夹 / Exclude large folders
{
  "files.exclude": {
    "**/node_modules": true,
    "**/.git": true
  },
  "search.exclude": {
    "**/node_modules": true,
    "**/dist": true
  }
}
```

### 4. Git 集成问题 / Git integration issues

**问题 / Problem**: Git 功能不正常

**解决方案 / Solution**:
```bash
# 1. 检查 Git 路径 / Check Git path
git --version

# 2. 检查 VS Code Git 设置 / Check VS Code Git settings
{
  "git.enabled": true,
  "git.path": "/usr/bin/git"  # 或你的 Git 路径 / or your Git path
}

# 3. 重新初始化 Git / Reinitialize Git
# Ctrl+Shift+P -> "Git: Close All Editors"
# 重新打开项目 / Reopen project
```

## 参考资源 / References

### 官方资源 / Official Resources

- [VS Code 官网](https://code.visualstudio.com/)
- [VS Code 文档](https://code.visualstudio.com/docs)
- [VS Code API](https://code.visualstudio.com/api)

### 推荐阅读 / Recommended Reading

- [VS Code Tips and Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)
- [VS Code Keybindings](https://code.visualstudio.com/docs/getstarted/keybindings)
- [VS Code Settings](https://code.visualstudio.com/docs/getstarted/settings)

### 社区资源 / Community Resources

- [VS Code Awesome Extensions](https://github.com/viatsko/awesome-vscode)
- [VS Code Themes](https://vscodethemes.com/)

---

**相关配置 / Related Configs**
- [Zsh 配置 / Zsh Configuration](zshrc.md)
- [Git 配置 / Git Configuration](gitconfig.md)
- [Neovim 配置 / Neovim Configuration](neovim.md)
- [Tmux 配置 / Tmux Configuration](tmux.md)
