[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# Meine Dotfiles

**Meine Entwicklungsumgebung-Konfigurationen. Zsh, Git, VS Code, Neovim, Tmux — alles, was Sie für Produktivität brauchen.**

---

## Was ist enthalten

| Konfiguration | Datei | Beschreibung |
|---------------|-------|--------------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | Shell-Konfiguration mit oh-my-zsh, Plugins, Aliases und Prompt |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Git-Aliases, Signierung, Diff-Tools und Workflow-Helfer |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | Einstellungen, Erweiterungen, Tastenkombinationen und Snippets |
| Neovim | [configs/neovim.md](configs/neovim.md) | Vollständige Neovim-Einrichtung mit LazyVim, LSP und Plugins |
| Tmux | [configs/tmux.md](configs/tmux.md) | Terminal-Multiplexer-Konfiguration mit Plugins und Statusleiste |

## Schnellstart

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

> **Hinweis:** Jede Konfigurationsdatei (`.md`) enthält den tatsächlichen Konfigurationsinhalt zusammen mit Setup-Anleitungen und Erklärungen. Kopieren Sie die relevanten Abschnitte in Ihre Konfigurationsdateien.

## Installation nach Tool

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

## Projektstruktur

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

## Siehe auch

- [dotfiles.github.io](https://dotfiles.github.io/) — Community-Dotfiles-Verzeichnis
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Dotfiles-Ressourcen
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Zsh-Framework
- [LazyVim](https://github.com/LazyVim/LazyVim) — Neovim-Konfigurationsframework
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Tmux-Plugin-Manager

## Lizenz

Dieses Projekt steht unter der MIT-Lizenz — siehe die Datei [LICENSE](LICENSE) für Details.

## Mitwirken

Beiträge sind willkommen! Bitte lesen Sie den [Beitragsleitfaden](CONTRIBUTING.md) vor dem Erstellen eines Pull Requests.
