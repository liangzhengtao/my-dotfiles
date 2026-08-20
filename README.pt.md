[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# Meus Dotfiles

**Minhas configs de ambiente de desenvolvimento. Zsh, Git, VS Code, Neovim, Tmux — tudo que você precisa para ser produtivo.**

---

## O que está incluído

| Config | Arquivo | Descrição |
|--------|---------|-----------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | Config do shell com oh-my-zsh, plugins, aliases e prompt |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Aliases do Git, assinatura, ferramentas diff e helpers de workflow |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | Configurações, extensões, atalhos de teclado e snippets |
| Neovim | [configs/neovim.md](configs/neovim.md) | Setup completo do Neovim com LazyVim, LSP e plugins |
| Tmux | [configs/tmux.md](configs/tmux.md) | Config do multiplexador de terminal com plugins e barra de status |

## Início Rápido

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

> **Nota:** Cada arquivo de config (`.md`) contém o conteúdo real da configuração junto com instruções de setup e explicações. Copie as seções relevantes para seus arquivos de configuração.

## Instalação por Ferramenta

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

## Estrutura do Projeto

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

## Veja Também

- [dotfiles.github.io](https://dotfiles.github.io/) — Diretório comunitário de dotfiles
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Recursos de Dotfiles
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Framework Zsh
- [LazyVim](https://github.com/LazyVim/LazyVim) — Framework de config do Neovim
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Gerenciador de plugins do Tmux

## Licença

Este projeto está licenciado sob a licença MIT — veja o arquivo [LICENSE](LICENSE) para detalhes.

## Contribuindo

Contribuições são bem-vindas! Por favor, leia o [Guia de Contribuição](CONTRIBUTING.md) antes de enviar um pull request.
