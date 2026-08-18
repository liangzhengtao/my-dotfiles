# Git Configuration

> Git aliases, signing setup, diff tools, and workflow helpers for productive version control.

---

## Table of Contents

- [The .gitconfig File](#the-gitconfig-file)
- [Aliases Explained](#aliases-explained)
- [GPG Signing Setup](#gpg-signing-setup)
- [SSH Signing Setup](#ssh-signing-setup)
- [Diff and Merge Tools](#diff-and-merge-tools)
- [Git Hooks](#git-hooks)
- [Conditional Includes](#conditional-includes)
- [Useful Git Functions](#useful-git-functions)
- [Troubleshooting](#troubleshooting)

---

## The .gitconfig File

```ini
# =============================================================================
# ~/.gitconfig — Git Configuration
# =============================================================================

[user]
    name = Your Name
    email = your-email@example.com
    # signingkey = YOUR_GPG_KEY_ID

[init]
    defaultBranch = main

[core]
    editor = nvim
    autocrlf = input
    whitespace = trailing-space,space-before-tab
    pager = delta
    # Trust file mode changes (important for executable scripts)
    trustctime = false

[interactive]
    diffFilter = delta --color-only

[delta]
    navigate = true
    line-numbers = true
    side-by-side = true
    syntax-theme = Dracula
    plus-style = "syntax #003800"
    minus-style = "syntax #3f0001"

[merge]
    conflictstyle = diff3
    tool = nvim

[mergetool "nvim"]
    cmd = nvim -d $MERGED $LOCAL $BASE $REMOTE -c 'wincmd J'

[diff]
    colorMoved = default
    algorithm = histogram
    tool = delta

[difftool "delta"]
    cmd = delta $LOCAL $REMOTE

[pull]
    rebase = true
    default = current

[push]
    default = current
    autoSetupRemote = true
    followTags = true

[fetch]
    prune = true
    pruneTags = true
    all = true

[rebase]
    autoStash = true
    autoSquash = true
    updateRefs = true

[rerere]
    enabled = true

[branch]
    sort = -committerdate

[tag]
    sort = -version:refname

[help]
    autocorrect = prompt

[grep]
    lineNumber = true
    extendRegexp = true

[credential]
    helper = cache --timeout=7200

# --- GitHub ---
[github]
    user = your-github-username

# --- Signing (choose one: GPG or SSH) ---
# [commit]
#     gpgsign = true
# [tag]
#     gpgsign = true

# =============================================================================
# Aliases
# =============================================================================

[alias]
    # --- Status & Info ---
    s = status -sb
    st = status
    info = remote -v

    # --- Staging ---
    a = add
    aa = add --all
    ap = add --patch

    # --- Commit ---
    c = commit
    ca = commit --amend
    cane = commit --amend --no-edit
    cm = commit -m
    cma = commit -am
    cf = commit --fixup
    cs = commit --squash
    cw = commit -m "WIP: work in progress"

    # --- Log ---
    l = log --oneline --graph --decorate -30
    la = log --oneline --graph --decorate --all
    lg = log --graph --format='%C(auto)%h%Creset %C(cyan)%ar%Creset %C(yellow)%d%Creset %s %C(green)<%an>%Creset'
    lga = log --graph --format='%C(auto)%h%Creset %C(cyan)%ar%Creset %C(yellow)%d%Creset %s %C(green)<%an>%Creset' --all
    today = log --since=midnight --oneline --no-merges
    yesterday = log --since=yesterday.midnight --until=midnight --oneline --no-merges
    wip = log --oneline --all --grep="WIP"

    # --- Diff ---
    d = diff
    ds = diff --staged
    dw = diff --word-diff
    dc = diff --cached

    # --- Branch ---
    b = branch -vv
    ba = branch -a
    bd = branch -d
    bdd = branch -D
    bm = branch -m

    # --- Checkout ---
    co = checkout
    cob = checkout -b
    com = checkout main
    cod = checkout develop

    # --- Stash ---
    ss = stash
    sp = stash pop
    sl = stash list
    sd = stash drop
    sa = stash apply
    sw = stash show -p

    # --- Remote ---
    f = fetch --all --prune
    fo = fetch origin
    pom = push origin main
    pod = push origin develop
    pl = pull
    plr = pull --rebase

    # --- Merge & Rebase ---
    m = merge
    mt = mergetool
    r = rebase
    ri = rebase -i
    ra = rebase --abort
    rc = rebase --continue
    rs = rebase --skip

    # --- Reset ---
    undo = reset HEAD~1 --mixed
    undohard = reset HEAD~1 --hard
    unstage = reset HEAD --
    clean-branches = "!git branch --merged | grep -v '\\*\\|main\\|develop' | xargs -n 1 git branch -d"

    # --- Tag ---
    t = tag
    tl = tag -l
    tn = tag -a

    # --- Search ---
    grep = grep -n --heading

    # --- Miscellaneous ---
    contributors = shortlog -sne
    amend = commit --amend --no-edit
    squash = "!f(){ git rebase -i HEAD~${1:-3}; };f"
    wtf = "!git-wtf"
    changelog = "!f(){ git log --oneline ${1:-HEAD~10}..HEAD; };f"
```

## Aliases Explained

### Most Used Aliases

| Alias | Command | When to Use |
|-------|---------|-------------|
| `gs` | `git status -sb` | Quick status check |
| `ga` | `git add` | Stage files |
| `gc "msg"` | `git commit -m "msg"` | Commit with message |
| `gp` | `git push` | Push to remote |
| `gl` | `git log --oneline --graph -30` | View recent history |
| `gd` | `git diff` | See changes |
| `gds` | `git diff --staged` | See staged changes |
| `gco` | `git checkout` | Switch branches |
| `gf` | `git fetch --all --prune` | Fetch and prune |
| `undo` | `git reset HEAD~1 --mixed` | Undo last commit (keep changes) |
| `unstage` | `git reset HEAD --` | Unstage all files |

### Dangerous Aliases (Use Carefully)

| Alias | Command | Warning |
|-------|---------|---------|
| `undohard` | `git reset HEAD~1 --hard` | Loses all uncommitted changes |
| `bdd` | `git branch -D` | Force-deletes unmerged branch |
| `gclean` | `git clean -fd` | Removes all untracked files |

## GPG Signing Setup

```bash
# 1. Generate a GPG key
gpg --full-generate-key
# Choose: RSA and RSA, 4096 bits, no expiration
# Use the same email as your git config

# 2. Get your key ID
gpg --list-secret-keys --keyid-format=long
# sec   rsa4096/ABC123DEF456 2025-01-01 [SC]

# 3. Add to git
git config --global user.signingkey ABC123DEF456
git config --global commit.gpgsign true
git config --global tag.gpgsign true

# 4. Export public key for GitHub
gpg --armor --export ABC123DEF456
# Paste the output into GitHub → Settings → SSH and GPG keys → New GPG key

# 5. Configure gpg-agent for caching
echo "default-cache-ttl 7200" >> ~/.gnupg/gpg-agent.conf
echo "max-cache-ttl 86400" >> ~/.gnupg/gpg-agent.conf
```

## SSH Signing Setup

```bash
# 1. Generate an SSH key (if you don't have one)
ssh-keygen -t ed25519 -C "your-email@example.com"

# 2. Tell git to use SSH signing
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
git config --global tag.gpgsign true

# 3. Create allowed signers file
echo "your-email@example.com $(cat ~/.ssh/id_ed25519.pub)" >> ~/.ssh/allowed_signers
git config --global gpg.ssh.allowedSignersFile ~/.ssh/allowed_signers

# 4. Add SSH key to GitHub
# GitHub → Settings → SSH and GPG keys → New SSH key
# Select "Signing Key" as the key type
```

## Diff and Merge Tools

Delta is the recommended diff/pager:

```bash
# Install delta
brew install git-delta    # macOS
cargo install git-delta   # From source (any OS)

# Install nvim as merge tool
brew install neovim       # macOS
```

## Git Hooks

Pre-commit hook (`~/.git-templates/hooks/pre-commit`):

```bash
#!/bin/bash
# Check for trailing whitespace
if git diff --cached --check; then
    echo "Trailing whitespace detected. Fix before committing."
    exit 1
fi

# Check for merge conflict markers
if git diff --cached | grep -E '^[<>=]{7}( |$)'; then
    echo "Merge conflict markers found. Resolve before committing."
    exit 1
fi

# Check for accidentally committed secrets
if git diff --cached --diff-filter=d -p | grep -iE '(api_key|apikey|secret|password|token).*[=:].*["\x27][A-Za-z0-9+/=]{20,}'; then
    echo "WARNING: Possible secret detected in staged changes."
    echo "Use 'git commit --no-verify' to bypass this check."
    exit 1
fi
```

```bash
# Set up the hooks template
mkdir -p ~/.git-templates/hooks
# (copy the hook above to ~/.git-templates/hooks/pre-commit)
chmod +x ~/.git-templates/hooks/pre-commit
git config --global init.templatedir '~/.git-templates'
```

## Conditional Includes

Use different configs for different directories:

```ini
# In ~/.gitconfig — use work email for work projects
[includeIf "gitdir:~/Work/"]
    path = ~/.gitconfig-work

[includeIf "gitdir:~/Personal/"]
    path = ~/.gitconfig-personal
```

```ini
# ~/.gitconfig-work
[user]
    name = Your Name
    email = you@company.com
    signingkey = WORK_GPG_KEY
```

## Useful Git Functions

Add these to your `.zshrc`:

```bash
# Interactive rebase onto main
grebase() {
  git rebase -i $(git merge-base HEAD main)
}

# Create a PR-ready branch
gpr() {
  git checkout -b "feat/$1" && git push -u origin "feat/$1"
}

# Show file history
gfile() {
  git log --oneline --follow -- "$1"
}

# Show who changed each line of a file
gblame() {
  git blame -L "$2","$3" "$1"
}

# Squash last N commits
gsquash() {
  git reset --soft "HEAD~${1:-3}" && git commit -m "${2:-Squashed commits}"
}

# Clean merged branches
gcleanmerged() {
  git branch --merged main | grep -v 'main\|develop\|\*' | xargs -n 1 git branch -d
}
```

## Troubleshooting

**Signing not working?**
```bash
gpg --list-keys                    # Check keys exist
git config --global -l | grep sign # Check git config
echo "test" | gpg --sign           # Test GPG directly
```

**Push rejected?**
```bash
git pull --rebase origin main     # Rebase on top of remote
git push --force-with-lease       # Safe force push (respects remote changes)
```

**Merge conflicts?**
```bash
git mergetool                      # Open configured merge tool
git diff --name-only --diff-filter=U  # List conflicted files
```
