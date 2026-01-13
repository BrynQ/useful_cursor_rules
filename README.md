# Useful Cursor Rules

A collection of useful Cursor IDE rules for automated PR review and code quality checks.

## 📁 Structure

```
pr_rules/
├── commands/
│   ├── pr-review.mdc    # Review Pull Requests
│   └── pr-create.mdc    # Create Pull Requests
└── shared/
    └── code-quality-standards.mdc  # Quality standards reference
```

## 🚀 Quick Start

### Installation

1. Copy the `pr_rules` folder to your project's `.cursor/rules/` directory:

```bash
# Clone this repo
git clone https://github.com/yakubilik/useful_cursor_rules.git

# Copy rules to your project
cp -r useful_cursor_rules/pr_rules your-project/.cursor/rules/
```

2. Ensure GitHub CLI is installed and authenticated:
```bash
gh auth login
```

### Usage

#### Review a Pull Request

```
@pr-review 42
@pr-review https://github.com/owner/repo/pull/42
```

This will:
- 🔒 Check for security issues (exposed secrets, SQL injection)
- ❌ Detect errors (syntax, logic bugs, type mismatches)
- ⚠️ Find warnings (unused code, print statements, TODOs)
- 💡 Suggest improvements (type hints, documentation)

#### Create a Pull Request

```
@pr-create
@pr-create fixing the login bug
```

This will:
- Run pre-PR quality validation
- Auto-push branch if needed
- Generate PR title based on commits
- Add quality badge if validation passes
- Create PR or add comment if PR exists

## 📋 What Gets Checked

### 🔒 Security (CRITICAL)

| Check | Description |
|-------|-------------|
| Hard-coded secrets | Passwords, API keys, tokens in code |
| SQL injection | String interpolation in SQL queries |
| Dangerous functions | `eval()`, `exec()`, `os.system()` |

### ❌ Errors (MUST FIX)

| Check | Description |
|-------|-------------|
| Syntax errors | Invalid Python syntax |
| Undefined variables | Using variables before assignment |
| Bare except | `except:` without specific exception |
| Unreachable code | Code after return/raise |

### ⚠️ Warnings (SHOULD FIX)

| Check | Description |
|-------|-------------|
| Unused imports | Import statements not used |
| Print statements | Debug prints in production |
| TODO/FIXME | Unresolved task comments |
| Breakpoints | `breakpoint()` or `pdb.set_trace()` |

### 💡 Info (OPTIONAL)

| Check | Description |
|-------|-------------|
| Missing type hints | Functions without type annotations |
| Missing docstrings | Public functions without docs |
| Naming conventions | snake_case, PascalCase violations |

## 🏷️ Quality Badge

When validation passes, PRs get a quality badge:

```markdown
<!-- CODE-QUALITY-STATUS -->
## Code Quality
✅ **Quality checks passed**
- Date: 2026-01-13
- Files checked: 5
- Issues: 0 critical, 0 errors, 2 warnings
<!-- /CODE-QUALITY-STATUS -->
```

This enables **fast-path reviews** - if no new commits since badge, review is instant!

## 📝 Examples

### Reviewing a PR

```
> @pr-review 42

## PR Review: #42 - Add user authentication

**Verdict: ⚠️ APPROVED with comments**

### Quality Summary
| Check | Status |
|-------|--------|
| Security | ✅ No issues |
| Errors | ✅ No issues |
| Warnings | 🟡 2 warnings |
| Info | 💡 3 suggestions |

### ⚠️ Warnings
1. `auth.py:45` - Unused import: `from typing import List`
2. `utils.py:23` - TODO without issue reference
```

### Creating a PR

```
> @pr-create adding rate limiting

Pre-PR Quality Check: PASSED ✅

PR created successfully!
Title: feat(api): Add rate limiting
URL: https://github.com/owner/repo/pull/15

✅ Quality badge added - review will be faster!
```

## ⚠️ Evidence-Based Feedback

These rules enforce **evidence-based feedback** - no vague comments allowed!

### ❌ Vague (Not Allowed)
```
"Good improvement to clarity"
"Nice refactoring"
"Better structure"
```

### ✅ Evidence-Based (Required)
```
"Reorganized imports per PEP8: stdlib (1-5), third-party (6-10), local (11-15)"
"Extracted duplicate logic from lines 45 and 89 into validate_token()"
"Follows same pattern as existing_file.py:23"
```

### Confidence Levels

All findings include confidence:
- `[CERTAIN]` - Verifiable fact (syntax error, unused import)
- `[LIKELY]` - High confidence, context-dependent
- `[UNCERTAIN]` - Cannot verify without more context

### False Positive Awareness

The rules explicitly warn about potential false positives:
- Unused imports may be dynamically accessed
- "Dead code" may be called via reflection
- Variables may be used in f-strings or eval

---

## 🔧 Customization

### Adjusting Severity

Edit `shared/code-quality-standards.mdc` to change what's CRITICAL vs WARNING.

### Adding Custom Checks

Add new patterns to the "Check Patterns (Regex)" section in the standards file.

## 📄 License

MIT License - feel free to use and modify!

## 🤝 Contributing

PRs welcome! Please ensure your changes follow the existing format.

---

Made with ❤️ for better code reviews
