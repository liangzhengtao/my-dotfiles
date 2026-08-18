# Zsh Configuration

> A comprehensive Zsh setup with oh-my-zsh, useful plugins, aliases, and a modern prompt.

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [The .zshrc File](#the-zshrc-file)
- [Plugins](#plugins)
- [Aliases](#aliases)
- [Key Bindings](#key-bindings)
- [Prompt Customization](#prompt-customization)
- [Fuzzy Finder (fzf)](#fuzzy-finder-fzf)
- [Directory Navigation](#directory-navigation)
- [Troubleshooting](#troubleshooting)

---

## Prerequisites

- Zsh (`zsh --version` to check)
- Git
- curl or wget

Install Zsh if not present:

```bash
# macOS
brew install zsh

# Ubuntu/Debian
sudo apt install zsh

# Arch
sudo pacman -S zsh

# Set as default shell
chsh -s $(which zsh)
```

## Installation

```bash
# 1. Install oh-my-zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 2. Install plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-completions
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
git clone https://github.com/MichaelAqworthy/zsh-autocomplete.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete

# 3. Install Starship prompt (optional but recommended)
curl -sS https://starship.rs/install.sh | sh

# 4. Install fzf
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

# 5. Install zoxide (smart cd)
curl -sSfL https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | sh
```

## The .zshrc File

```bash
# =============================================================================
# ~/.zshrc — Zsh Configuration
# =============================================================================

# --- oh-my-zsh ---
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME=""  # Using Starship instead

# --- Plugins ---
plugins=(
  git
  docker
  docker-compose
  kubectl
  helm
  terraform
  aws
  golang
  node
  npm
  python
  pip
  rust
  brew
  macos
  zsh-autosuggestions
  zsh-syntax-highlighting
  zsh-completions
  zsh-history-substring-search
  zsh-autocomplete
  colored-man-pages
  command-not-found
  extract
  sudo
  copypath
  copyfile
  jsontools
  urltools
  web-search
  aliases
)

source $ZSH/oh-my-zsh.sh

# --- Environment Variables ---
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export EDITOR="nvim"
export VISUAL="nvim"
export MANPAGER="sh -c 'col -bx | bat -l man -p'"

# --- History ---
HISTSIZE=50000
SAVEHIST=50000
HISTFILE=~/.zsh_history
setopt HIST_IGNORE_ALL_DUPS
setopt HIST_FIND_NO_DUPS
setopt HIST_SAVE_NO_DUPS
setopt SHARE_HISTORY
setopt APPEND_HISTORY
setopt INC_APPEND_HISTORY
setopt HIST_REDUCE_BLANKS
setopt HIST_VERIFY

# --- Completion ---
setopt COMPLETE_IN_WORD
setopt ALWAYS_TO_END
setopt MENU_COMPLETE
zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'
zstyle ':completion:*' menu select
zstyle ':completion:*' use-cache on
zstyle ':completion:*' cache-path ~/.zsh/cache

# --- Starship Prompt ---
eval "$(starship init zsh)"

# --- Zoxide (smart cd) ---
eval "$(zoxide init zsh)"

# --- fzf ---
[ -f ~/.fzf.zsh ] && source ~/.fzf.zsh
export FZF_DEFAULT_OPTS="--height 40% --layout=reverse --border --preview 'bat --color=always --style=numbers --line-range=:500 {}'"

# Source aliases
[ -f ~/.zsh_aliases ] && source ~/.zsh_aliases
[ -f ~/.zsh_local ] && source ~/.zsh_local
```

## Plugins

| Plugin | Description |
|--------|-------------|
| zsh-autosuggestions | Fish-like autosuggestions based on history |
| zsh-syntax-highlighting | Real-time command syntax highlighting |
| zsh-completions | Additional completion definitions |
| zsh-history-substring-search | History search with substring matching |
| zsh-autocomplete | Real-time autocompletion |
| colored-man-pages | Colorized man pages |
| extract | Universal archive extractor |
| sudo | Double-ESC to prepend sudo |
| copypath | Copy current path to clipboard |
| copyfile | Copy file contents to clipboard |

## Aliases

```bash
# =============================================================================
# ~/.zsh_aliases — Shell Aliases
# =============================================================================

# --- Navigation ---
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias ~="cd ~"
alias dl="cd ~/Downloads"
alias dt="cd ~/Desktop"
alias proj="cd ~/Projects"

# --- ls replacements ---
alias ls="eza --icons --group-directories-first"
alias ll="eza -la --icons --group-directories-first --git"
alias lt="eza --tree --level=2 --icons"
alias la="eza -a --icons --group-directories-first"

# --- cat/bat ---
alias cat="bat --style=auto"
alias catn="bat --style=plain"
alias catl="bat --style=numbers"

# --- grep/ripgrep ---
alias grep="rg"
alias fgrep="rg -F"
alias egrep="rg -E"

# --- find/fd ---
alias find="fd"

# --- Git ---
alias g="git"
alias gs="git status -sb"
alias ga="git add"
alias gaa="git add --all"
alias gc="git commit -m"
alias gca="git commit -am"
alias gp="git push"
alias gpl="git pull"
alias gf="git fetch --all --prune"
alias gd="git diff"
alias gds="git diff --staged"
alias gl="git log --oneline --graph --decorate -20"
alias gla="git log --oneline --graph --decorate --all"
alias gb="git branch -vv"
alias gco="git checkout"
alias gcb="git checkout -b"
alias gm="git merge"
alias gr="git rebase"
alias gst="git stash"
alias gstp="git stash pop"
alias gclean="git clean -fd"
alias greset="git reset --hard HEAD"

# --- Docker ---
alias d="docker"
alias dps="docker ps --format 'table {{.Names}}\t{{.Status}}\t{{.Ports}}'"
alias dpsa="docker ps -a --format 'table {{.Names}}\t{{.Status}}\t{{.Ports}}'"
alias di="docker images"
alias dex="docker exec -it"
alias dlog="docker logs -f"
alias dprune="docker system prune -af"
alias dc="docker compose"
alias dcu="docker compose up -d"
alias dcd="docker compose down"
alias dcl="docker compose logs -f"

# --- k8s ---
alias k="kubectl"
alias kgp="kubectl get pods"
alias kgs="kubectl get services"
alias kgd="kubectl get deployments"
alias kgn="kubectl get nodes"
alias kl="kubectl logs -f"
alias kex="kubectl exec -it"
alias kctx="kubectx"
alias kns="kubens"

# --- Python ---
alias py="python3"
alias pip="pip3"
alias venv="python3 -m venv"
alias activate="source .venv/bin/activate"
alias ipy="ipython"

# --- Node ---
alias ni="npm install"
alias nid="npm install -D"
alias nr="npm run"
alias ns="npm start"
alias nt="npm test"
alias nb="npm run build"
alias nup="npx npm-check-updates -u"

# --- System ---
alias path='echo $PATH | tr ":" "\n"'
alias ports="netstat -tulanp"
alias meminfo="free -h"
alias cpuinfo="lscpu"
alias diskinfo="df -h"
alias myip="curl -s ifconfig.me"
alias localip="ipconfig getifaddr en0"
alias flushdns="sudo dscacheutil -flushcache && sudo killall -HUP mDNSResponder"

# --- Utilities ---
alias reload="source ~/.zshrc && echo 'Zsh config reloaded'"
alias zshconfig="nvim ~/.zshrc"
alias aliases="nvim ~/.zsh_aliases"
alias weather="curl -s 'wttr.in?format=3'"
alias cheat="curl -s cheat.sh/"
alias urlencode='python3 -c "import sys, urllib.parse; print(urllib.parse.quote(sys.argv[1]))"'
alias urldecode='python3 -c "import sys, urllib.parse; print(urllib.parse.unquote(sys.argv[1]))"'
```

## Key Bindings

```bash
# History search with arrows
bindkey "^[[A" history-substring-search-up
bindkey "^[[B" history-substring-search-down

# Ctrl+R for fzf history search
bindkey "^R" fzf-history-widget

# Ctrl+T for fzf file finder
bindkey "^T" fzf-file-widget

# Ctrl+E to edit current command in $EDITOR
autoload -z edit-command-line
zle -N edit-command-line
bindkey "^E" edit-command-line

# Alt+. to insert last argument
bindkey "^[." insert-last-word

# Ctrl+X Ctrl+E to edit command in editor
bindkey "^X^E" edit-command-line
```

## Prompt Customization

Starship prompt config (`~/.config/starship.toml`):

```toml
format = """
$directory\
$git_branch\
$git_status\
$python\
$nodejs\
$rust\
$docker_context\
$cmd_duration\
$line_break\
$character"""

[directory]
truncation_length = 3
truncation_symbol = "…/"

[git_branch]
symbol = " "
format = "on [$symbol$branch]($style) "

[git_status]
format = '([$all_status$ahead_behind]($style) )'

[character]
success_symbol = "[❯](bold green)"
error_symbol = "[❯](bold red)"

[cmd_duration]
min_time = 2_000
format = "took [$duration]($style) "
```

## Fuzzy Finder (fzf)

```bash
# Useful fzf functions for .zshrc

# Interactive git log
fgit() {
  git log --oneline --decorate | fzf --preview 'git show {1}' | awk '{print $1}'
}

# Interactive process killer
fkill() {
  ps aux | fzf --multi | awk '{print $2}' | xargs kill -${1:-9}
}

# Interactive directory changer
fcd() {
  local dir
  dir=$(fd --type d --hidden --exclude .git | fzf) && cd "$dir"
}

# Interactive file opener
fo() {
  local file
  file=$(fd --type f --hidden --exclude .git | fzf --preview 'bat --color=always {}') && nvim "$file"
}

# Interactive docker container exec
fdex() {
  local container
  container=$(docker ps --format '{{.Names}}' | fzf) && docker exec -it "$container" /bin/sh
}
```

## Directory Navigation

```bash
# Zoxide (already in .zshrc) — smart cd that learns your habits
# Usage:
#   z foo         # cd to most frecent directory matching "foo"
#   z foo bar     # cd to most frecent directory matching "foo" and "bar"
#   zi            # interactive selection with fzf
#   z -           # cd to previous directory

# Useful directory functions
mkcd() { mkdir -p "$1" && cd "$1" }
```

## Troubleshooting

**Slow startup?** Profile with:
```bash
time zsh -i -c exit
# Enable profiling in .zshrc:
# zmodload zsh/zprof && at the end: zprof
```

**Plugins not loading?** Verify paths:
```bash
ls ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/
```

**Completions not working?** Rebuild:
```bash
rm -f ~/.zsh/cache/*
compinit -u
```
