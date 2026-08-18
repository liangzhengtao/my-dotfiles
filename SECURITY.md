# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please report it responsibly.

**Do NOT open a public issue for security vulnerabilities.**

Instead, please send an email to the project maintainer with:

- A description of the vulnerability
- Steps to reproduce the issue
- Potential impact assessment
- Suggested fix (if available)

## Response Timeline

- **Acknowledgment**: Within 48 hours
- **Initial assessment**: Within 1 week
- **Fix or mitigation**: Depends on severity

## Scope

This project contains development environment configurations. While there are no runtime services, we take the following seriously:

- **No secrets in configs**: API keys, tokens, passwords, and SSH keys must never be committed
- **Sanitized examples**: All config examples use placeholder values (e.g., `YOUR_API_KEY`, `your-email@example.com`)
- **Git signing**: Configs that include GPG/SSH signing should use placeholder key IDs
- **Private paths**: User-specific paths should use generic placeholders (e.g., `~/.config/...`)

## Best Practices for Users

When using these dotfiles:

1. **Never commit your real API keys or tokens** — use environment variables instead
2. **Review configs before applying** — understand what each setting does
3. **Backup existing configs** before overwriting
4. **Use `.local` or `.private` files** for personal settings that shouldn't be shared
5. **Keep your tools updated** to patch known vulnerabilities
