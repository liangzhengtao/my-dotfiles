[中文版](README.zh.md)
n<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# My Dotfiles

**My development environment configs. Zsh, Git, VS Code, Neovim, Tmux — everything you need to be productive.**

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
├── README.zh.md
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
