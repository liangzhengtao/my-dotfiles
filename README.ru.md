[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# Мои Dotfiles

**Мои конфигурации среды разработки. Zsh, Git, VS Code, Neovim, Tmux — всё, что нужно для продуктивной работы.**

---

## Что включено

| Конфигурация | Файл | Описание |
|-------------|------|----------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | Настройка оболочки с oh-my-zsh, плагинами, алиасами и промптом |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Git-алиасы, подпись, инструменты diff и помощники рабочего процесса |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | Настройки, расширения, привязки клавиш и сниппеты |
| Neovim | [configs/neovim.md](configs/neovim.md) | Полная настройка Neovim с LazyVim, LSP и плагинами |
| Tmux | [configs/tmux.md](configs/tmux.md) | Конфигурация терминального мультиплексора с плагинами и строкой состояния |

## Быстрый старт

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

> **Примечание:** Каждый конфигурационный файл (`.md`) содержит фактическое содержимое конфигурации вместе с инструкциями по настройке и пояснениями. Скопируйте соответствующие разделы в свои конфигурационные файлы.

## Установка по инструментам

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

## Структура проекта

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

## Также смотрите

- [dotfiles.github.io](https://dotfiles.github.io/) — Сообщество dotfiles
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Ресурсы по dotfiles
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Фреймворк Zsh
- [LazyVim](https://github.com/LazyVim/LazyVim) — Конфигурационный фреймворк Neovim
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Менеджер плагинов Tmux

## Лицензия

Проект распространяется под лицензией MIT — подробности в файле [LICENSE](LICENSE).

## Участие

Приветствуется вклад! Пожалуйста, прочитайте [Руководство по участию](CONTRIBUTING.md) перед отправкой pull request.
