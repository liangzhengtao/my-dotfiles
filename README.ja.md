[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# My Dotfiles

**私の開発環境設定集。Zsh、Git、VS Code、Neovim、Tmux — 生産性を最大化するための完璧なセットアップ。**

---

## 含まれる設定

| 設定 | ファイル | 説明 |
|--------|------|-------------|
| Zsh | [configs/zshrc.md](configs/zshrc.md) | oh-my-zsh、プラグイン、エイリアス、プロンプトを含む Shell 設定 |
| Git | [configs/gitconfig.md](configs/gitconfig.md) | Git エイリアス、署名、差分ツール、ワークフロー支援 |
| VS Code | [configs/vscode-settings.md](configs/vscode-settings.md) | 設定、拡張拡張機能、キーバインド、スニペット |
| Neovim | [configs/neovim.md](configs/neovim.md) | LazyVim、LSP、プラグインを含む完全な Neovim セットアップ |
| Tmux | [configs/tmux.md](configs/tmux.md) | プラグインとステータスバー付きのターミナルマルチプレクサー設定 |

## クイックスタート

```bash
# リポジトリをクローン
git clone https://github.com/liangzhengtao/my-dotfiles.git ~/my-dotfiles
cd ~/my-dotfiles

# 既存の設定をバックアップ（必ずバックアップを先に！）
mkdir -p ~/dotfiles-backup/$(date +%Y%m%d)
cp ~/.zshrc ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.gitconfig ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true
cp ~/.tmux.conf ~/dotfiles-backup/$(date +%Y%m%d)/ 2>/dev/null || true

# 設定を適用（各ガイドに具体的な手順あり）
# 各設定ファイル（.md）に実際の設定内容と解説が含まれています
```

> **注意:** 各設定ファイル（`.md`）には実際の設定内容とセットアップ手順、解説が含まれています。関連セクションをあなたの設定ファイルにコピーしてください。

## ツール別インストール手順

### Zsh

```bash
# oh-my-zsh をインストール
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 完全な .zshrc の内容は configs/zshrc.md を参照
```

### Tmux

```bash
# TPM（Tmux Plugin Manager）をインストール
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# 完全な .tmux.conf の内容は configs/tmux.md を参照
```

### Neovim

```bash
# Neovim をインストール（macOS）
brew install neovim

# LazyVim の初期セットアップは configs/neovim.md を参照
```

### Git

```bash
# 完全な .gitconfig の内容は configs/gitconfig.md を参照
# 関連セクションを ~/.gitconfig にコピー
```

### VS Code

```bash
# 設定、拡張拡張機能、キーバインドは configs/vscode-settings.md を参照
# 拡張機能は CLI からインストール可能:
# code --install-extension <extension-id>
```

## プロジェクト構成

```
my-dotfiles/
├── configs/
│   ├── zshrc.md              # Zsh 設定
│   ├── gitconfig.md          # Git 設定
│   ├── vscode-settings.md    # VS Code 設定＆拡張機能
│   ├── neovim.md             # Neovim + LazyVim
│   └── tmux.md              # Tmux 設定
├── README.md
├── README.zh.md
├── CONTRIBUTING.md
├── SECURITY.md
├── CODE_OF_CONDUCT.md
├── CHANGELOG.md
├── LICENSE
└── .gitignore
```

## 関連リンク

- [dotfiles.github.io](https://dotfiles.github.io/) — コミュニティ dotfiles ディレクトリ
- [awesome-dotfiles](https://github.com/webpro/awesome-dotfiles) — Dotfiles リソース集
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) — Zsh フレームワーク
- [LazyVim](https://github.com/LazyVim/LazyVim) — Neovim 設定フレームワーク
- [tmux-plugin-manager](https://github.com/tmux-plugins/tpm) — Tmux プラグインマネージャー

## ライセンス

本プロジェクトは MIT ライセンスの下で公開されています。詳細は [LICENSE](LICENSE) をご覧ください。

## コントリビューション

コントリビューションを歓迎します！Pull Request を送る前に [コントリビューションガイド](CONTRIBUTING.md) をお読みください。
