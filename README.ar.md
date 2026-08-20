[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# ملفات الإعدادات الخاصة بي

**إعدادات بيئة التطوير الخاصة بي. Zsh، Git، VS Code، Neovim، Tmux — كل ما تحتاجه للإنتاجية.**

---

## ما يتضمنه

| الإعداد | الملف | الوصف |
|---------|-------|-------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | إعداد الشاشة مع oh-my-zsh والإضافات والأسماء المستعارة |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | أسماء مستعارة لـ Git، التوقيع، أدوات diff، ومساعدين سير العمل |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | الإعدادات، الإضافات، اختصارات لوحة المفاتيح، والمقتطفات |
| Neovim | [configs/neovim.md](configs/neovim.md) | إعداد Neovim الكامل مع LazyVim، LSP، والإضافات |
| Tmux | [configs/tmux.md](configs/tmux.md) | إعداد مضاعف الطرفية مع الإضافات وشريط الحالة |

## البدء السريع

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

> **ملاحظة:** يحتوي كل ملف إعداد (`.md`) على محتوى الإعداد الفعلي إلى جانب تعليمات الإعداد والتوضيحات. انسخ الأقسام ذات الصلة إلى ملفات الإعداد الخاصة بك.

## التثبيت حسب الأداة

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

## هيكل المشروع

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

## انظر أيضًا

- [dotfiles.github.io](https://dotfiles.github.io/) — دليل ملفات الإعدادات المجتمعية
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — موارد ملفات الإعدادات
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — إطار عمل Zsh
- [LazyVim](https://github.com/LazyVim/LazyVim) — إطار إعداد Neovim
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — مدير إضافات Tmux

## الرخصة

هذا المشروع مرخص بموجب رخصة MIT — راجع ملف [LICENSE](LICENSE) للتفاصيل.

## المساهمة

المساهمات مرحب بها! يرجى قراءة [دليل المساهمة](CONTRIBUTING.md) قبل تقديم طلب سحب.
