[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# My Dotfiles

**나의 개발 환경 설정. Zsh, Git, VS Code, Neovim, Tmux — 생산성에 필요한 모든 것.**

---

## 포함된 설정

| 설정 | 파일 | 설명 |
|------|------|------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | oh-my-zsh, 플러그인, 별칭, 프롬프트가 포함된 셸 설정 |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Git 별칭, 서명, diff 도구, 워크플로우 헬퍼 |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | 설정, 확장, 키 바인딩, 스니펫 |
| Neovim | [configs/neovim.md](configs/neovim.md) | LazyVim, LSP, 플러그인이 포함된 Neovim 전체 설정 |
| Tmux | [configs/tmux.md](configs/tmux.md) | 플러그인과 상태 표시줄이 포함된 터미널 멀티플렉서 설정 |

## 빠른 시작

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

> **참고:** 각 설정 파일 (`.md`)에는 실제 설정 내용과 함께 설정 안내 및 설명이 포함되어 있습니다. 해당 섹션을 설정 파일에 복사하세요.

## 도구별 설치

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

## 프로젝트 구조

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

## 관련 링크

- [dotfiles.github.io](https://dotfiles.github.io/) — 커뮤니티 dotfiles 디렉토리
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Dotfiles 리소스
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Zsh 프레임워크
- [LazyVim](https://github.com/LazyVim/LazyVim) — Neovim 설정 프레임워크
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Tmux 플러그인 관리자

## 라이선스

이 프로젝트는 MIT 라이선스에 따라 라이선스가 부여됩니다 — 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

## 기여하기

기여를 환영합니다! 풀 리퀘스트를 제출하기 전에 [기여 가이드](CONTRIBUTING.md)를 읽어주세요.
