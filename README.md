# Useful Cursor Rules

A community-driven collection of useful Cursor IDE rules to boost productivity. Each rule set is designed to be **plug-and-play** - just copy to your `.cursor/rules/` folder and start using.

---

## 🎯 What's This?

Cursor IDE allows you to create custom AI-powered commands using `.mdc` rule files. This repository collects practical, battle-tested rules that solve real problems.

**Philosophy:**
- 📦 **Modular** - Take only what you need
- 🔌 **Plug-and-play** - Copy, paste, use
- 📝 **Well-documented** - Each rule set has its own README
- 🧪 **Tested** - Used in production projects

---

## 📁 Available Rule Sets

| Rule Set | Description | Commands |
|----------|-------------|----------|
| [**pr_rules**](./pr_rules/) | PR review & creation with code quality checks | `@pr-review`, `@pr-create` |

> 💡 More rule sets coming soon! Feel free to contribute.

---

## 🚀 Quick Start

### Option 1: Clone specific rules

```bash
# Clone the repo
git clone https://github.com/BrynQ/useful_cursor_rules.git

# Copy only what you need to your project
cp -r useful_cursor_rules/pr_rules your-project/.cursor/rules/
```

### Option 2: Clone everything

```bash
# Clone into your project's .cursor/rules directory
cd your-project/.cursor/rules
git clone https://github.com/BrynQ/useful_cursor_rules.git
```

### Option 3: Manual download

1. Go to the rule set folder (e.g., `pr_rules/`)
2. Download the files you need
3. Copy to your `.cursor/rules/` directory

---

## 📋 Rule Sets Overview

### 🔍 PR Rules (`pr_rules/`)

Automate PR creation and review with built-in code quality checks.

**Commands:**
- `@pr-review <PR_NUMBER>` - Review a PR for security, errors, and code quality
- `@pr-create` - Create a PR with automatic validation

**Features:**
- Security scanning (secrets, SQL injection, dangerous functions)
- Error detection (syntax, logic, types)
- Code quality checks (unused code, debug artifacts)
- Evidence-based feedback (no vague comments!)
- False positive awareness
- Quality badge system for faster reviews

[📖 Full documentation](./pr_rules/README.md)

---

## 🤝 Contributing

We welcome contributions! Here's how:

### Adding a new rule set

1. Create a folder with a descriptive name (e.g., `test_rules/`)
2. Add your `.mdc` files following the structure:
   ```
   your_rules/
   ├── commands/
   │   └── your-command.mdc
   ├── shared/
   │   └── your-standards.mdc (optional)
   └── README.md
   ```
3. Write a comprehensive README for your rule set
4. Submit a PR

### Improving existing rules

1. Fork the repo
2. Make your changes
3. Test thoroughly
4. Submit a PR with clear explanation

### Rule Quality Guidelines

- ✅ **Evidence-based** - No vague feedback (see pr_rules for example)
- ✅ **Well-documented** - Each command should have clear usage examples
- ✅ **Modular** - Rules should work independently
- ✅ **Tested** - Test your rules before submitting

---

## 📂 Repository Structure

```
useful_cursor_rules/
├── README.md              # This file
├── pr_rules/              # PR review & creation
│   ├── README.md          # PR rules documentation
│   ├── commands/
│   │   ├── pr-review.mdc
│   │   └── pr-create.mdc
│   └── shared/
│       └── code-quality-standards.mdc
├── [future_rules]/        # More rule sets coming...
│   └── ...
└── CONTRIBUTING.md        # (coming soon)
```

---

## 💡 Ideas for Future Rule Sets

Want to contribute? Here are some ideas:

| Idea | Description |
|------|-------------|
| `test_rules` | Generate and review unit tests |
| `doc_rules` | Auto-generate documentation |
| `refactor_rules` | Suggest and apply refactoring |
| `deploy_rules` | Deployment checklists and validation |
| `security_rules` | Deep security scanning |
| `performance_rules` | Performance analysis and suggestions |

---

## 📜 License

MIT License - feel free to use, modify, and distribute!

---

## ⭐ Star This Repo

If you find these rules useful, please star ⭐ the repo! It helps others discover it.

---

Made with ❤️ by the BrynQ team
