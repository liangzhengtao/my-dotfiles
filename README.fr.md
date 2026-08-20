[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# Mes Dotfiles

**Mes configurations d'environnement de développement. Zsh, Git, VS Code, Neovim, Tmux — tout ce qu'il faut pour être productif.**

---

## Contenu

| Config | Fichier | Description |
|--------|------|-------------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | Configuration Shell avec oh-my-zsh, plugins, alias et prompt |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Alias Git, signature, outils de diff et aides au workflow |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | Paramètres, extensions, raccourcis et extraits de code |
| Neovim | [configs/neovim.md](configs/neovim.md) | Configuration Neovim complète avec LazyVim, LSP et plugins |
| Tmux | [configs/tmux.md](configs/tmux.md) | Configuration du multiplexeur de terminal avec plugins et barre d'état |

## Démarrage rapide

```bash
# Cloner le dépôt
git clone https://github.com/liangzhengtao/my-dotfiles.git ~/my-dotfiles
cd ~/my-dotfiles

# Sauvegarder les configurations existantes (toujours sauvegarder d'abord !)
mkdir -p ~/dotfiles-backup/$(date +%Y%m%d)
cp ~/.zshrc ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.gitconfig ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.tmux.conf ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true

# Appliquer les configurations (voir chaque guide pour les étapes spécifiques)
# Chaque fichier de configuration (.md) contient le contenu réel et les instructions
```

> **Remarque :** Chaque fichier de configuration (`.md`) contient le contenu de configuration ainsi que les instructions de mise en place et les explications. Copiez les sections pertinentes dans vos fichiers de configuration.

## Installation par outil

### Zsh

```bash
# Installer oh-my-zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Voir configs/zshrc.md pour le contenu complet de .zshrc
```

### Tmux

```bash
# Installer TPM (Tmux Plugin Manager)
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# Voir configs/tmux.md pour le contenu complet de .tmux.conf
```

### Neovim

```bash
# Installer Neovim (macOS)
brew install neovim

# Voir configs/neovim.md pour la configuration initiale LazyVim
```

### Git

```bash
# Voir configs/gitconfig.md pour le contenu complet de .gitconfig
# Copiez les sections pertinentes dans ~/.gitconfig
```

### VS Code

```bash
# Voir configs/vscode-settings.md pour les paramètres, extensions et raccourcis
# Les extensions peuvent être installées via le CLI :
# code --install-extension <extension-id>
```

## Structure du projet

```
my-dotfiles/
├── configs/
│   ├── zshrc.md              # Configuration Zsh
│   ├── gitconfig.md          # Configuration Git
│   ├── vscode-settings.md    # Paramètres et extensions VS Code
│   ├── neovim.md             # Neovim + LazyVim
│   └── tmux.md              # Configuration Tmux
├── README.md
├── README.zh.md
├── CONTRIBUTING.md
├── SECURITY.md
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

## Voir aussi

- [dotfiles.github.io](https://dotfiles.github.io/) — Répertoire communautaire de dotfiles
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Ressources Dotfiles
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Framework Zsh
- [LazyVim](https://github.com/LazyVim/LazyVim) — Framework de configuration Neovim
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Gestionnaire de plugins Tmux

## Licence

Ce projet est sous licence MIT — voir le fichier [LICENSE](LICENSE) pour les détails.

## Contribuer

Les contributions sont les bienvenues ! Veuillez lire le [Guide de contribution](CONTRIBUTING.md) avant de soumettre une pull request.
