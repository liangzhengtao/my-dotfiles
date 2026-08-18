# Contributing to My Dotfiles

Thank you for your interest in contributing! This project collects practical development environment configurations.

[English](#contributing-to-my-dotfiles) | [中文](#为我的-dotfiles-做贡献)

---

## How to Contribute

### Reporting Issues

- Search [existing issues](../../issues) before opening a new one
- Use the provided issue templates
- Include your OS, shell version, and relevant tool versions
- Describe the problem clearly with steps to reproduce

### Suggesting Improvements

- Open an issue describing the improvement
- Explain why the change would be useful
- Include links to relevant documentation

### Submitting Changes

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/my-improvement`
3. **Make** your changes
4. **Test** your changes (ensure configs work on your system)
5. **Commit** with a clear message: `git commit -m "Add fish shell config"`
6. **Push** to your fork: `git push origin feature/my-improvement`
7. **Open** a Pull Request

## Content Guidelines

### Config Files

- Each config file is a Markdown document containing the actual config content in fenced code blocks
- Include setup instructions and explanations for non-obvious settings
- Provide OS-specific installation commands (macOS, Linux, Windows/WSL)
- Keep configurations practical — only include what you actually use
- Comment your configs generously so others can customize

### Writing Style

- Use clear, concise language
- Include practical examples
- Explain the "why" behind non-obvious settings
- Link to official documentation for tools and plugins

## Adding a New Config

To add a new tool configuration:

1. Create `configs/<tool-name>.md`
2. Follow the existing file structure:
   - Title and description
   - Prerequisites / installation
   - The actual configuration in fenced code blocks
   - Key settings explained
   - Troubleshooting
3. Update `README.md` to include the new config in the table
4. Update `CHANGELOG.md` with your addition

## Code of Conduct

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before participating.

---

# 为我的 Dotfiles 做贡献

感谢你有兴趣参与贡献！本项目收集实用的开发环境配置。

[English](#contributing-to-my-dotfiles) | [中文](#为我的-dotfiles-做贡献)

---

## 如何贡献

### 报告问题

- 在提交新问题前先搜索 [已有问题](../../issues)
- 使用提供的问题模板
- 包含你的操作系统、Shell 版本和相关工具版本
- 清晰描述问题并提供复现步骤

### 建议改进

- 提交 issue 描述改进内容
- 解释为什么这个变更有用
- 包含相关文档的链接

### 提交更改

1. **Fork** 仓库
2. **创建** 特性分支：`git checkout -b feature/my-improvement`
3. **进行** 修改
4. **测试** 你的更改（确保配置在你的系统上可用）
5. **提交** 并写清楚的提交信息：`git commit -m "Add fish shell config"`
6. **推送** 到你的 fork：`git push origin feature/my-improvement`
7. **发起** Pull Request

## 内容规范

### 配置文件

- 每个配置文件是一个 Markdown 文档，在代码块中包含实际配置内容
- 包含设置说明和非显而易见设置的解释
- 提供特定操作系统的安装命令（macOS、Linux、Windows/WSL）
- 保持配置实用 —— 只包含你实际使用的内容
- 大方地添加注释，以便其他人可以自定义

### 添加新配置

要添加新的工具配置：

1. 创建 `configs/<tool-name>.md`
2. 遵循现有文件结构
3. 更新 `README.md` 在表格中包含新配置
4. 更新 `CHANGELOG.md` 记录你的添加

## 行为准则

请在参与之前阅读我们的 [行为准则](CODE_OF_CONDUCT.md)。
