# My Dotfiles

**My development environment configs. Zsh, Git, VS Code, Neovim, Tmux — everything you need to be productive.**

[English](#my-dotfiles) | [中文](#我的-dotfiles)

---

## What's Included

| Config | File | Description |
|--------|------|-------------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | Shell config with oh-my-zsh, plugins, aliases, and prompt |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Git aliases, signing, diff tools, and workflow helpers |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | Settings, extensions, keybindings, and snippets |
| Neovim | [configs/neovim.md](configs/neovim.md) | Full Neovim setup with LazyVim, LSP, and plugins |
| Tmux | [configs/tmux.md](configs/tmux.md) | Terminal multiplexer config with plugins and status bar |

## Quick Start

```bash
# Clone the repo
git clone https://github.com/liangzhengtao/my-dotfiles.git ~/my-dotfiles
cd ~/my-dotfiles

# Backup existing configs (always backup first!)
mkdir -p ~/dotfiles-backup/$(date +%Y%m%d)
cp ~/.zshrc ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.gitconfig ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.tmux.conf ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true

# Apply configs (read each guide for the specific steps)
# Each config file is a detailed guide — follow the setup instructions inside
```

> **Note:** Each config file (`.md`) contains the actual configuration content along with setup instructions and explanations. Copy the relevant sections into your config files.

## Installation by Tool

### Zsh

```bash
# Install oh-my-zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# See configs/zshrc.md for full .zshrc content
```

### Tmux

```bash
# Install TPM (Tmux Plugin Manager)
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# See configs/tmux.md for full .tmux.conf content
```

### Neovim

```bash
# Install Neovim (macOS)
brew install neovim

# See configs/neovim.md for LazyVim starter setup
```

### Git

```bash
# See configs/gitconfig.md for full .gitconfig content
# Copy relevant sections to ~/.gitconfig
```

### VS Code

```bash
# See configs/vscode-settings.md for settings, extensions, and keybindings
# Extensions can be installed via CLI:
# code --install-extension <extension-id>
```

## Project Structure

```
my-dotfiles/
├── configs/
│   ├── zshrc.md              # Zsh configuration
│   ├── gitconfig.md          # Git configuration
│   ├── vscode-settings.md    # VS Code settings & extensions
│   ├── neovim.md             # Neovim + LazyVim
│   └── tmux.md              # Tmux configuration
├── README.md
├── CONTRIBUTING.md
├── SECURITY.md
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

## See Also

- [dotfiles.github.io](https://dotfiles.github.io/) — Community dotfiles directory
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Dotfiles resources
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Zsh framework
- [LazyVim](https://github.com/LazyVim/LazyVim) — Neovim config framework
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Tmux plugin manager

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please read the [Contributing Guide](CONTRIBUTING.md) before submitting a pull request.

---

# 我的 Dotfiles

**我的开发环境配置。Zsh、Git、VS Code、Neovim、Tmux —— 你需要的一切，开箱即用。**

[English](#my-dotfiles) | [中文](#我的-dotfiles)

---

## 包含内容

| 配置 | 文件 | 说明 |
|------|------|------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | Shell 配置，含 oh-my-zsh、插件、别名和提示符 |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Git 别名、签名、差异工具和工作流助手 |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | 设置、扩展、快捷键和代码片段 |
| Neovim | [configs/neovim.md](configs/neovim.md) | 完整 Neovim 配置，含 LazyVim、LSP 和插件 |
| Tmux | [configs/tmux.md](configs/tmux.md) | 终端复用器配置，含插件和状态栏 |

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/liangzhengtao/my-dotfiles.git ~/my-dotfiles
cd ~/my-dotfiles

# 备份现有配置（务必先备份！）
mkdir -p ~/dotfiles-backup/$(date +%Y%m%d)
cp ~/.zshrc ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.gitconfig ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.tmux.conf ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true

# 应用配置（每个指南内有具体步骤）
# 每个配置文件（.md）包含实际配置内容和设置说明
```

> **注意：** 每个配置文件（`.md`）包含实际配置内容和设置说明。将相关部分复制到你的配置文件中。

## 相关项目

- [dotfiles.github.io](https://dotfiles.github.io/) — 社区 dotfiles 目录
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Dotfiles 资源
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Zsh 框架
- [LazyVim](https://github.com/LazyVim/LazyVim) — Neovim 配置框架
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Tmux 插件管理器

## 许可证

本项目基于 MIT 许可证 —— 详见 [LICENSE](LICENSE) 文件。

## 贡献

欢迎贡献！请在提交 Pull Request 前阅读 [贡献指南](CONTRIBUTING.md)。
