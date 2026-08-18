# Tmux 配置指南 / Tmux Configuration Guide

[返回目录 / Back to Index](../README.md)

## 目录 / Table of Contents

- [简介 / Introduction](#简介--introduction)
- [安装 / Installation](#安装--installation)
- [配置文件 / Configuration File](#配置文件--configuration-file)
- [基本配置 / Basic Configuration](#基本配置--basic-configuration)
- [快捷键配置 / Keybinding Configuration](#快捷键配置--keybinding-configuration)
- [状态栏配置 / Status Bar Configuration](#状态栏配置--status-bar-configuration)
- [插件管理 / Plugin Management](#插件管理--plugin-management)
- [会话管理 / Session Management](#会话管理--session管理)
- [窗口和面板 / Windows and Panes](#窗口和面板--windows-and-panes)
- [自定义选项 / Customization Options](#自定义选项--customization-options)
- [常见问题 / Common Issues](#常见问题--common-issues)
- [参考资源 / References](#参考资源--references)

## 简介 / Introduction

Tmux 是一个终端复用器，允许你在单个终端窗口中管理多个终端会话。

Tmux is a terminal multiplexer that allows you to manage multiple terminal sessions within a single terminal window.

### 为什么选择 Tmux？ / Why Choose Tmux?

- 🚀 **多任务处理** - 在一个终端中运行多个会话
- 🔌 **会话持久化** - 断开连接后保持会话运行
- 📝 **窗口分割** - 水平和垂直分割窗口
- 🎨 **高度可定制** - 自定义快捷键、状态栏等
- 🔧 **脚本化** - 可以通过脚本自动化配置

- 🚀 **Multitasking** - Run multiple sessions in one terminal
- 🔌 **Session Persistence** - Keep sessions running after disconnect
- 📝 **Window Splitting** - Split windows horizontally and vertically
- 🎨 **Highly Customizable** - Customize keybindings, status bar, etc.
- 🔧 **Scriptable** - Automate configuration through scripts

## 安装 / Installation

### 安装 Tmux / Install Tmux

```bash
# macOS (使用 Homebrew)
brew install tmux

# Ubuntu/Debian
sudo apt update
sudo apt install tmux

# CentOS/RHEL
sudo yum install tmux

# Windows (使用 WSL)
# 在 WSL 中运行上述命令
```

### 安装 TPM (Tmux Plugin Manager) / Install TPM

```bash
# 克隆 TPM / Clone TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

## 配置文件 / Configuration File

### 完整配置 / Full Configuration

```bash
# ~/.tmux.conf - Tmux 配置文件 / Tmux Configuration File

# ============================================================
# 基础配置 / Basic Configuration
# ============================================================

# 设置默认 Shell / Set default shell
set -g default-shell /bin/zsh

# 设置默认终端 / Set default terminal
set -g default-terminal "screen-256color"
set -ga terminal-overrides ",*256col*:Tc"

# 设置历史记录限制 / Set history limit
set -g history-limit 50000

# 设置窗口和面板索引从 1 开始 / Set window and pane index to start from 1
set -g base-index 1
setw -g pane-base-index 1

# 立即重命名窗口 / Rename window immediately
set -g allow-rename off
set -g automatic-rename on

# 设置状态栏刷新间隔 / Set status bar refresh interval
set -g status-interval 5

# 启用鼠标支持 / Enable mouse support
set -g mouse on

# 设置 Escape 键延迟 / Set Escape key delay
set -sg escape-time 0

# 设置焦点事件 / Set focus events
set -g focus-events on

# 设置活动窗口样式 / Set active window style
setw -g monitor-activity on
set -g visual-activity off

# ============================================================
# 前缀键配置 / Prefix Key Configuration
# ============================================================

# 将前缀键从 Ctrl+b 改为 Ctrl+a / Change prefix from Ctrl+b to Ctrl+a
set -g prefix C-a
unbind C-b
bind C-a send-prefix

# ============================================================
# 快捷键配置 / Keybinding Configuration
# ============================================================

# 重新加载配置文件 / Reload configuration file
bind r source-file ~/.tmux.conf \; display-message "Config reloaded!"

# 分割窗口 / Split windows
bind | split-window -h -c "#{pane_current_path}"
bind - split-window - v -c "#{pane_current_path}"
bind _ split-window - v -c "#{pane_current_path}"

# 创建新窗口 / Create new window
bind c new-window -c "#{pane_current_path}"

# 窗口导航 / Window navigation
bind -n M-Left previous-window
bind -n M-Right next-window
bind -n M-1 select-window -t 1
bind -n M-2 select-window -t 2
bind -n M-3 select-window -t 3
bind -n M-4 select-window -t 4
bind -n M-5 select-window -t 5
bind -n M-6 select-window -t 6
bind -n M-7 select-window -t 7
bind -n M-8 select-window -t 8
bind -n M-9 select-window -t 9

# 面板导航（Vim 风格）/ Pane navigation (Vim style)
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# 面板导航（Alt + 方向键）/ Pane navigation (Alt + arrow keys)
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# 调整面板大小（Vim 风格）/ Resize panes (Vim style)
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# 调整面板大小（Ctrl + 方向键）/ Resize panes (Ctrl + arrow keys)
bind -r C-Left resize-pane -L 5
bind -r C-Right resize-pane -R 5
bind -r C-Up resize-pane -U 5
bind -r C-Down resize-pane -D 5

# 最大化/恢复面板 / Maximize/restore pane
bind z resize-pane -Z

# 关闭面板 / Close pane
bind x kill-pane

# 关闭窗口 / Close window
bind X kill-window

# 循环切换面板布局 / Cycle pane layouts
bind Space next-layout

# 面板同步 / Pane synchronization
bind S setw synchronize-panes \; display-message "Pane sync: #{?pane_synchronized,on,off}"

# 复制模式 / Copy mode
bind [ copy-mode
bind ] paste-buffer

# Vi 模式 / Vi mode
setw -g mode-keys vi

# 复制模式快捷键 / Copy mode keybindings
bind -T copy-mode-vi v send -X begin-selection
bind -T copy-mode-vi y send -X copy-selection-and-cancel
bind -T copy-mode-vi C-v send -X rectangle-toggle
bind -T copy-mode-vi Escape send -X cancel

# ============================================================
# 状态栏配置 / Status Bar Configuration
# ============================================================

# 状态栏位置 / Status bar position
set -g status-position bottom

# 状态栏样式 / Status bar style
set -g status-style "bg=colour235,fg=colour136"

# 左侧状态栏 / Left status bar
set -g status-left-length 40
set -g status-left "#[fg=green,bold]#S #[fg=blue]│ "

# 右侧状态栏 / Right status bar
set -g status-right-length 60
set -g status-right "#[fg=blue]│ #[fg=yellow]%Y-%m-%d #[fg=green]%H:%M #[fg=blue]│ #[fg=cyan]#H"

# 窗口状态栏格式 / Window status format
setw -g window-status-format "#[fg=colour240]#I:#W"
setw -g window-status-current-format "#[fg=white,bold]#I:#W#[fg=colour240]*"
setw -g window-status-separator " "

# 活动窗口样式 / Active window style
setw -g window-status-current-style "fg=white,bold,bg=colour238"

# 非活动窗口样式 / Inactive window style
setw -g window-status-style "fg=colour240"

# 面板边框样式 / Pane border style
set -g pane-border-style "fg=colour238"
set -g pane-active-border-style "fg=green"

# 消息样式 / Message style
set -g message-style "fg=white,bg=colour235"

# 时钟模式 / Clock mode
setw -g clock-mode-colour green
setw -g clock-mode-style 24

# ============================================================
# 插件配置 / Plugin Configuration
# ============================================================

# TPM 插件列表 / TPM plugin list
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @plugin 'tmux-plugins/tmux-yank'
set -g @plugin 'tmux-plugins/tmux-copycat'
set -g @plugin 'tmux-plugins/tmux-open'
set -g @plugin 'tmux-plugins/tmux-prefix-highlight'
set -g @plugin 'tmux-plugins/tmux-battery'
set -g @plugin 'tmux-plugins/tmux-cpu'
set -g @plugin 'tmux-plugins/tmux-net-speed'
set -g @plugin 'jimeh/tmux-themepack'

# 插件配置 / Plugin configuration

# tmux-resurrect / tmux-resurrect
set -g @resurrect-strategy-vim 'session'
set -g @resurrect-strategy-nvim 'session'
set -g @resurrect-capture-pane-contents 'on'
set -g @resurrect-processes 'ssh psql mysql sqlite3'

# tmux-continuum / tmux-continuum
set -g @continuum-restore 'on'
set -g @continuum-save-interval '15'
set -g @continuum-boot 'on'
set -g @continuum-boot-options 'iterm,fullscreen'

# tmux-yank / tmux-yank
set -g @yank_selection 'clipboard'
set -g @yank_action 'copy-pipe-and-cancel'

# tmux-prefix-highlight / tmux-prefix-highlight
set -g @prefix_highlight_fg 'white'
set -g @prefix_highlight_bg 'blue'
set -g @prefix_highlight_show_copy_mode 'on'
set -g @prefix_highlight_copy_mode_attr 'fg=black,bg=yellow,bold'
set -g @prefix_highlight_prefix_prompt 'PREFIX'
set -g @prefix_highlight_copy_prompt 'COPY'

# tmux-battery / tmux-battery
set -g @batt_charged_icon "🔌"
set -g @batt_charging_icon "⚡"
set -g @batt_discharging_icon "🔋"
set -g @batt_attached_icon "🔌"
set -g @batt_full_charge_icon "💯"
set -g @batt_high_charge_icon "🔋"
set -g @batt_medium_charge_icon "🔋"
set -g @batt_low_charge_icon "🔋"

# tmux-cpu / tmux-cpu
set -g @cpu_percentage_format "%5.1f%%"
set -g @cpu_low_icon "🟢"
set -g @cpu_medium_icon "🟡"
set -g @cpu_high_icon "🔴"

# tmux-net-speed / tmux-net-speed
set -g @net_speed_format "↓%10s ↑%10s"

# ============================================================
# 初始化 TPM（必须放在最后）/ Initialize TPM (must be at the end)
# ============================================================

run '~/.tmux/plugins/tpm/tpm'
```

## 基本配置 / Basic Configuration

### Shell 和终端 / Shell and Terminal

```bash
# 设置默认 Shell / Set default shell
set -g default-shell /bin/zsh

# 设置默认终端 / Set default terminal
set -g default-terminal "screen-256color"
set -ga terminal-overrides ",*256col*:Tc"
```

### 窗口和面板索引 / Window and Pane Index

```bash
# 设置窗口索引从 1 开始 / Set window index to start from 1
set -g base-index 1

# 设置面板索引从 1 开始 / Set pane index to start from 1
setw -g pane-base-index 1

# 重新编号窗口 / Renumber windows
set -g renumber-windows on
```

### 鼠标支持 / Mouse Support

```bash
# 启用鼠标支持 / Enable mouse support
set -g mouse on

# 鼠标滚动 / Mouse scrolling
bind -T root WheelUpPane if-shell -F -t = "#{alternate_screen}" "send -M" "copy-mode -e"
bind -T root WheelDownPane if-shell -F -t = "#{alternate_screen}" "send -M"
```

## 快捷键配置 / Keybinding Configuration

### 前缀键 / Prefix Key

```bash
# 将前缀键改为 Ctrl+a / Change prefix to Ctrl+a
set -g prefix C-a
unbind C-b
bind C-a send-prefix
```

### 窗口分割 / Window Splitting

```bash
# 水平分割 / Horizontal split
bind | split-window -h -c "#{pane_current_path}"

# 垂直分割 / Vertical split
bind - split-window - v -c "#{pane_current_path}"
```

### 面板导航 / Pane Navigation

```bash
# Vim 风格导航 / Vim style navigation
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# Alt + 方向键导航 / Alt + arrow key navigation
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D
```

### 面板调整大小 / Pane Resizing

```bash
# Vim 风格调整大小 / Vim style resizing
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# Ctrl + 方向键调整大小 / Ctrl + arrow key resizing
bind -r C-Left resize-pane -L 5
bind -r C-Right resize-pane -R 5
bind -r C-Up resize-pane -U 5
bind -r C-Down resize-pane -D 5
```

## 状态栏配置 / Status Bar Configuration

### 基本状态栏 / Basic Status Bar

```bash
# 状态栏位置 / Status bar position
set -g status-position bottom

# 状态栏样式 / Status bar style
set -g status-style "bg=colour235,fg=colour136"

# 左侧状态栏 / Left status bar
set -g status-left-length 40
set -g status-left "#[fg=green,bold]#S #[fg=blue]│ "

# 右侧状态栏 / Right status bar
set -g status-right-length 60
set -g status-right "#[fg=blue]│ #[fg=yellow]%Y-%m-%d #[fg=green]%H:%M #[fg=blue]│ #[fg=cyan]#H"
```

### 窗口状态格式 / Window Status Format

```bash
# 窗口状态格式 / Window status format
setw -g window-status-format "#[fg=colour240]#I:#W"

# 当前窗口状态格式 / Current window status format
setw -g window-status-current-format "#[fg=white,bold]#I:#W#[fg=colour240]*"

# 窗口状态分隔符 / Window status separator
setw -g window-status-separator " "
```

### 高级状态栏配置 / Advanced Status Bar Configuration

```bash
# 带电池和 CPU 的状态栏 / Status bar with battery and CPU
set -g status-right "#[fg=blue]│ #[fg=yellow]%Y-%m-%d #[fg=green]%H:%M #[fg=blue]│ #[fg=cyan]#H #[fg=blue]│ #{battery_icon} #{battery_percentage} #[fg=blue]│ #{cpu_icon} #{cpu_percentage}"
```

## 插件管理 / Plugin Management

### TPM 基础用法 / TPM Basic Usage

```bash
# 安装插件 / Install plugins
# 在 ~/.tmux.conf 中添加插件，然后按 prefix + I

# 更新插件 / Update plugins
# 按 prefix + U

# 卸载插件 / Uninstall plugins
# 从 ~/.tmux.conf 中删除插件，然后按 prefix + alt + u
```

### 推荐插件 / Recommended Plugins

| 插件 / Plugin | 说明 / Description |
|---------------|-------------------|
| tpm | Tmux 插件管理器 / Tmux plugin manager |
| tmux-sensible | 合理的默认设置 / Sensible defaults |
| tmux-resurrect | 会话保存和恢复 / Session save and restore |
| tmux-continuum | 自动保存和恢复 / Auto save and restore |
| tmux-yank | 复制到系统剪贴板 / Copy to system clipboard |
| tmux-copycat | 正则搜索 / Regex search |
| tmux-open | 快速打开文件/URL / Quick open files/URLs |
| tmux-prefix-highlight | 前缀键高亮 / Prefix key highlight |
| tmux-battery | 电池状态 / Battery status |
| tmux-cpu | CPU 使用率 / CPU usage |
| tmux-net-speed | 网络速度 / Network speed |

### 插件配置示例 / Plugin Configuration Examples

```bash
# tmux-resurrect 配置 / tmux-resurrect configuration
set -g @resurrect-strategy-vim 'session'
set -g @resurrect-strategy-nvim 'session'
set -g @resurrect-capture-pane-contents 'on'
set -g @resurrect-processes 'ssh psql mysql sqlite3'

# tmux-continuum 配置 / tmux-continuum configuration
set -g @continuum-restore 'on'
set -g @continuum-save-interval '15'
set -g @continuum-boot 'on'
set -g @continuum-boot-options 'iterm,fullscreen'

# tmux-yank 配置 / tmux-yank configuration
set -g @yank_selection 'clipboard'
set -g @yank_action 'copy-pipe-and-cancel'
```

## 会话管理 / Session Management

### 会话命令 / Session Commands

```bash
# 创建新会话 / Create new session
tmux new -s session_name

# 列出会话 / List sessions
tmux ls

# 分离会话 / Detach session
# 按 prefix + d

# 连接到会话 / Attach to session
tmux attach -t session_name

# 杀死会话 / Kill session
tmux kill-session -t session_name
```

### 会话脚本化 / Session Scripting

```bash
#!/bin/bash
# 创建开发会话 / Create development session

# 创建会话 / Create session
tmux new-session -d -s dev -n editor

# 设置第一个窗口 / Setup first window
tmux send-keys -t dev:1 'nvim' C-m

# 创建第二个窗口 / Create second window
tmux new-window -t dev -n terminal

# 创建第三个窗口 / Create third window
tmux new-window -t dev -n server

# 分割第三个窗口 / Split third window
tmux split-window -h -t dev:3
tmux send-keys -t dev:3.1 'npm run dev' C-m
tmux send-keys -t dev:3.2 'npm run test:watch' C-m

# 选择第一个窗口 / Select first window
tmux select-window -t dev:1

# 连接到会话 / Attach to session
tmux attach-session -t dev
```

## 窗口和面板 / Windows and Panes

### 窗口命令 / Window Commands

```bash
# 创建新窗口 / Create new window
# 按 prefix + c

# 切换窗口 / Switch windows
# 按 prefix + 0-9

# 下一个窗口 / Next window
# 按 prefix + n

# 上一个窗口 / Previous window
# 按 prefix + p

# 重命名窗口 / Rename window
# 按 prefix + ,

# 关闭窗口 / Close window
# 按 prefix + &
```

### 面板命令 / Pane Commands

```bash
# 水平分割 / Horizontal split
# 按 prefix + |

# 垂直分割 / Vertical split
# 按 prefix + -

# 切换面板 / Switch panes
# 按 prefix + 方向键

# 最大化/恢复面板 / Maximize/restore pane
# 按 prefix + z

# 关闭面板 / Close pane
# 按 prefix + x

# 面板同步 / Pane synchronization
# 按 prefix + S
```

### 面板布局 / Pane Layouts

```bash
# 切换布局 / Switch layouts
# 按 prefix + Space

# 预定义布局 / Predefined layouts
# 按 prefix + Alt+1 (even-horizontal)
# 按 prefix + Alt+2 (even-vertical)
# 按 prefix + Alt+3 (main-horizontal)
# 按 prefix + Alt+4 (main-vertical)
# 按 prefix + Alt+5 (tiled)
```

## 自定义选项 / Customization Options

### 颜色配置 / Color Configuration

```bash
# 256 色支持 / 256 color support
set -g default-terminal "screen-256color"
set -ga terminal-overrides ",*256col*:Tc"

# 状态栏颜色 / Status bar colors
set -g status-style "bg=colour235,fg=colour136"

# 窗口颜色 / Window colors
setw -g window-status-current-style "fg=white,bold,bg=colour238"

# 面板边框颜色 / Pane border colors
set -g pane-border-style "fg=colour238"
set -g pane-active-border-style "fg=green"
```

### 键绑定模式 / Key Binding Mode

```bash
# Vi 模式 / Vi mode
setw -g mode-keys vi

# Emacs 模式 / Emacs mode
setw -g mode-keys emacs
```

### 复制模式 / Copy Mode

```bash
# 进入复制模式 / Enter copy mode
# 按 prefix + [

# Vi 模式复制 / Vi mode copy
bind -T copy-mode-vi v send -X begin-selection
bind -T copy-mode-vi y send -X copy-selection-and-cancel
bind -T copy-mode-vi C-v send -X rectangle-toggle
bind -T copy-mode-vi Escape send -X cancel

# 粘贴 / Paste
# 按 prefix + ]
```

## 常见问题 / Common Issues

### 1. 前缀键不生效 / Prefix key not working

**问题 / Problem**: 前缀键 Ctrl+a 不生效

**解决方案 / Solution**:
```bash
# 1. 检查配置文件 / Check configuration file
cat ~/.tmux.conf

# 2. 重新加载配置 / Reload configuration
tmux source-file ~/.tmux.conf

# 3. 重启 Tmux / Restart Tmux
tmux kill-server
tmux
```

### 2. 鼠标不工作 / Mouse not working

**问题 / Problem**: 鼠标支持不工作

**解决方案 / Solution**:
```bash
# 1. 检查鼠标配置 / Check mouse configuration
set -g mouse on

# 2. 检查终端支持 / Check terminal support
# 确保终端支持鼠标 / Ensure terminal supports mouse

# 3. 重新加载配置 / Reload configuration
tmux source-file ~/.tmux.conf
```

### 3. 颜色显示异常 / Colors displaying incorrectly

**问题 / Problem**: 颜色显示不正确

**解决方案 / Solution**:
```bash
# 1. 检查终端设置 / Check terminal settings
echo $TERM

# 2. 设置正确的终端类型 / Set correct terminal type
set -g default-terminal "screen-256color"
set -ga terminal-overrides ",*256col*:Tc"

# 3. 重启 Tmux / Restart Tmux
tmux kill-server
tmux
```

### 4. 插件不加载 / Plugin not loading

**问题 / Problem**: TPM 插件不加载

**解决方案 / Solution**:
```bash
# 1. 检查 TPM 是否安装 / Check if TPM is installed
ls ~/.tmux/plugins/tpm

# 2. 安装插件 / Install plugins
# 按 prefix + I

# 3. 检查配置文件 / Check configuration file
# 确保 TPM 初始化在文件末尾 / Ensure TPM init is at the end of file
run '~/.tmux/plugins/tpm/tpm'
```

### 5. 会话丢失 / Session lost

**问题 / Problem**: 断开连接后会话丢失

**解决方案 / Solution**:
```bash
# 1. 检查 tmux-continuum 配置 / Check tmux-continuum configuration
set -g @continuum-restore 'on'

# 2. 手动保存会话 / Manually save session
# 按 prefix + Ctrl+s

# 3. 手动恢复会话 / Manually restore session
# 按 prefix + Ctrl+r
```

## 参考资源 / References

### 官方资源 / Official Resources

- [Tmux 官网](https://github.com/tmux/tmux)
- [Tmux 手册](https://man7.org/linux/man-pages/man1/tmux.1.html)
- [Tmux Wiki](https://github.com/tmux/tmux/wiki)

### 推荐阅读 / Recommended Reading

- [Tmux 速查表](https://tmuxcheatsheet.com/)
- [Tmux 配置指南](https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/)
- [Tmux 实践](https://leanpub.com/the-tao-of-tmux/read)

### 社区资源 / Community Resources

- [Awesome Tmux](https://github.com/rothgar/awesome-tmux)
- [Tmux Plugin Manager](https://github.com/tmux-plugins/tpm)
- [Tmux Plugins](https://github.com/tmux-plugins)

---

**相关配置 / Related Configs**
- [Zsh 配置 / Zsh Configuration](zshrc.md)
- [Git 配置 / Git Configuration](gitconfig.md)
- [VS Code 配置 / VS Code Configuration](vscode-settings.md)
- [Neovim 配置 / Neovim Configuration](neovim.md)
