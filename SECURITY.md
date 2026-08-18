# 安全政策 / Security Policy

## 报告漏洞 / Reporting a Vulnerability

如果你发现本项目存在安全漏洞，请通过以下方式报告：

If you discover a security vulnerability in this project, please report it through:

### 报告方式 / Reporting Methods

1. **私密报告** / Private Report
   - 发送邮件至：security@liangzhengtao.com
   - 请包含以下信息：
     - 漏洞描述
     - 复现步骤
     - 影响范围
     - 修复建议（如有）

   - Send email to: security@liangzhengtao.com
   - Please include:
     - Vulnerability description
     - Steps to reproduce
     - Impact scope
     - Fix suggestions (if any)

2. **GitHub Security Advisories** / GitHub Security Advisories
   - 通过 GitHub 的安全漏洞报告功能
   - Use GitHub's security vulnerability reporting feature

### 响应时间 / Response Time

- 我们会在 **48 小时内** 确认收到报告
- 我们会在 **7 个工作日内** 提供初步评估
- 我们会在 **30 天内** 发布修复版本（如果需要）

- We will acknowledge receipt within **48 hours**
- We will provide an initial assessment within **7 business days**
- We will release a fix within **30 days** (if necessary)

### 漏洞处理流程 / Vulnerability Handling Process

1. **接收报告** / Receive Report
   - 确认收到并记录
   - Acknowledge receipt and record

2. **验证漏洞** / Verify Vulnerability
   - 复现并确认漏洞
   - Reproduce and confirm vulnerability

3. **评估影响** / Assess Impact
   - 确定严重程度和影响范围
   - Determine severity and impact scope

4. **制定修复方案** / Develop Fix
   - 创建修复补丁
   - Create fix patch

5. **测试修复** / Test Fix
   - 验证修复是否有效
   - Verify fix effectiveness

6. **发布更新** / Release Update
   - 发布新版本
   - Release new version

7. **公开披露** / Public Disclosure
   - 在修复发布后公开漏洞详情
   - Disclose vulnerability details after fix release

## 安全最佳实践 / Security Proven Patterns

### 对于用户 / For Users

1. **保持更新** / Stay Updated
   - 始终使用最新版本
   - Always use the latest version

2. **检查配置** / Check Configuration
   - 定期检查配置文件的安全性
   - Regularly check configuration files for security

3. **报告问题** / Report Issues
   - 发现问题及时报告
   - Report issues promptly when discovered

### 对于贡献者 / For Contributors

1. **代码审查** / Code Review
   - 所有配置必须经过审查
   - All configurations must be reviewed

2. **安全测试** / Security Testing
   - 测试配置的安全性
   - Test configuration security

3. **依赖管理** / Dependency Management
   - 使用安全的依赖版本
   - Use secure dependency versions

## 安全相关配置 / Security-Related Configuration

### Git 安全 / Git Security

```bash
# 启用 Git 签名 / Enable Git signing
git config --global commit.gpgsign true

# 设置 GPG 密钥 / Set GPG key
git config --global user.signingkey YOUR_GPG_KEY_ID

# 使用 SSH 代替 HTTPS / Use SSH instead of HTTPS
git config --global url."git@github.com:".insteadOf "https://github.com/"
```

### SSH 安全 / SSH Security

```bash
# 生成 SSH 密钥 / Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# 添加 SSH 密钥到 ssh-agent / Add SSH key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# 配置 SSH / Configure SSH
# ~/.ssh/config
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519
  AddKeysToAgent yes
```

### Shell 安全 / Shell Security

```bash
# 检查 Shell 配置权限 / Check shell config permissions
ls -la ~/.zshrc
# 应该是 644 或 600 / Should be 644 or 600

# 设置安全的权限 / Set secure permissions
chmod 600 ~/.zshrc
chmod 700 ~/.ssh
chmod 600 ~/.ssh/*
```

### Neovim 安全 / Neovim Security

```lua
-- 禁用不安全的模型ine / Disable unsafe modeline
vim.opt.modeline = false

-- 限制插件加载 / Limit plugin loading
vim.g.loaded_netrwPlugin = 1
vim.g.loaded_netrw = 1
```

### Tmux 安全 / Tmux Security

```bash
# 限制访问 / Limit access
set -g remain-on-exit off

# 设置安全的默认 Shell / Set secure default shell
set -g default-shell /bin/zsh
```

## 安全更新日志 / Security Update Log

### 最近的安全更新 / Recent Security Updates

- **2024-01-01**: 无安全更新 / No security updates

## 安全联系人 / Security Contact

- **主要联系人** / Primary Contact
  - 姓名 / Name: liangzhengtao
  - 邮箱 / Email: security@liangzhengtao.com

- **备用联系人** / Backup Contact
  - 姓名 / Name: liangzhengtao
  - 邮箱 / Email: backup-security@liangzhengtao.com

## 致谢 / Acknowledgements

感谢所有报告安全漏洞的研究人员和用户。

Thanks to all researchers and users who report security vulnerabilities.

## 法律声明 / Legal Notice

本安全政策遵循 [负责任的漏洞披露原则](https://en.wikipedia.org/wiki/Responsible_disclosure)。

This security policy follows the [Responsible Disclosure](https://en.wikipedia.org/wiki/Responsible_disclosure) principle.

---

**感谢你帮助我们保持项目安全！**

**Thank you for helping us keep the project secure!**
