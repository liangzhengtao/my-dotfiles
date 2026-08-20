[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

# 我的 Dotfiles

**我的开发环境配置。Zsh、Git、VS Code、Neovim、Tmux —— 你需要的一切，开箱即用。**

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

## 按工具安装

### Zsh

```bash
# 安装 oh-my-zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 完整 .zshrc 内容请参阅 configs/zshrc.md
```

### Tmux

```bash
# 安装 TPM（Tmux 插件管理器）
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# 完整 .tmux.conf 内容请参阅 configs/tmux.md
```

### Neovim

```bash
# 安装 Neovim（macOS）
brew install neovim

# LazyVim 初始配置请参阅 configs/neovim.md
```

### Git

```bash
# 完整 .gitconfig 内容请参阅 configs/gitconfig.md
# 将相关部分复制到 ~/.gitconfig
```

### VS Code

```bash
# 设置、扩展和快捷键请参阅 configs/vscode-settings.md
# 扩展可通过 CLI 安装：
# code --install-extension <extension-id>
```

## 项目结构

```
my-dotfiles/
├── configs/
│   ├── zshrc.md              # Zsh 配置
│   ├── gitconfig.md          # Git 配置
│   ├── vscode-settings.md    # VS Code 设置与扩展
│   ├── neovim.md             # Neovim + LazyVim
│   └── tmux.md              # Tmux 配置
├── README.md
├── README.zh.md
├── CONTRIBUTING.md
├── SECURITY.md
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

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
