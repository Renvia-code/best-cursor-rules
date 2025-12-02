# Contributing to Best Cursor Rules

Thanks for wanting to contribute! Here's how to add or improve rules.

---

## Quick Start

1. **Fork & Clone**
   ```bash
   git clone https://github.com/YOUR_USERNAME/best-cursor-rules.git
   cd best-cursor-rules
   ```

2. **Create a Branch**
   ```bash
   git checkout -b add-remix-rule
   ```

3. **Add/Edit Rules** in `rules/`

4. **Submit a PR**

---

## Rule Format

Every rule must follow the MDC format. See `.cursor/rules/01-rule-format.mdc` for the full spec.

### Basic Structure

```markdown
---
description: One-line description for AI context
globs: ["**/*.tsx", "**/*.ts"]
alwaysApply: false
---

# Rule Title

## Overview

| Aspect | Recommendation |
|--------|----------------|
| Thing | Recommendation |

---

## Section Name

### Pattern Name

```tsx
// Code example
```

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Bad thing | Good thing |
```

### Frontmatter Fields

| Field | Required | Description |
|-------|----------|-------------|
| `description` | Yes | 1-2 sentences explaining when to use this rule |
| `globs` | Yes | Array of file patterns (use `[]` for manual-only) |
| `alwaysApply` | No | Set `true` for rules that should always load |

### Globs Examples

```yaml
# TypeScript/React
globs: ["**/*.tsx", "**/*.ts"]

# Python
globs: ["**/*.py"]

# Specific folders
globs: ["src/components/**/*", "app/**/*"]

# Always manual
globs: []
```

---

## Content Guidelines

### ✅ DO

- Use clear `##` and `###` headings
- Include practical code examples
- Use tables for quick reference
- Add ✅/❌ for do/don't patterns
- Keep sections scannable
- Target 2025 framework versions

### ❌ DON'T

- Write walls of text
- Use vague language ("consider doing X")
- Include outdated patterns
- Repeat info from other rules
- Use corporate/AI clichés
- Exceed 500 lines

---

## File Naming

| Category | Pattern | Example |
|----------|---------|---------|
| Frameworks | `{name}-{version}.mdc` | `nextjs-15.mdc` |
| Languages | `{name}.mdc` | `typescript.mdc` |
| Stacks | `{name}-stack.mdc` or `{tech1}-{tech2}.mdc` | `t3-stack.mdc` |
| Practices | `{topic}.mdc` | `clean-code.mdc` |

---

## Testing Your Rules

1. **Copy to a test project**
   ```bash
   mkdir -p test-project/.cursor/rules
   cp rules/frameworks/your-rule.mdc test-project/.cursor/rules/
   ```

2. **Open in Cursor** and try coding

3. **Check if the AI follows your patterns**

4. **Adjust globs** if rules aren't activating

---

## Quality Checklist

Before submitting, verify:

- [ ] Frontmatter is valid YAML
- [ ] Description is clear and specific
- [ ] Globs target the correct file types
- [ ] Code examples are tested and work
- [ ] No outdated patterns (check current docs)
- [ ] Under 500 lines
- [ ] Follows existing style
- [ ] No AI-generated filler

---

## Categories

Put your rule in the right folder:

| Folder | Contents |
|--------|----------|
| `rules/frameworks/` | Next.js, React, Vue, Svelte, etc. |
| `rules/languages/` | TypeScript, Python, Go, Rust |
| `rules/backends/` | Supabase, FastAPI, Node.js |
| `rules/mobile/` | React Native, Flutter, SwiftUI |
| `rules/styling/` | Tailwind, shadcn/ui |
| `rules/testing/` | Vitest, Playwright, Jest |
| `rules/best-practices/` | Clean code, security, a11y |
| `rules/stacks/` | Combined presets (T3, MERN, etc.) |

---

## Pull Request Process

1. **One rule per PR** (unless closely related)

2. **PR Title**: `feat(frameworks): add remix rule` or `fix(supabase): update auth patterns`

3. **Description**: Brief explanation of what the rule covers

4. **Review**: Maintainers will check format and content quality

---

## Updating Existing Rules

When updating a rule:

1. Check it still follows the format spec
2. Update version numbers if frameworks changed
3. Remove deprecated patterns
4. Add new best practices
5. Keep backward compatibility notes if needed

---

## Questions?

Open an issue or check existing rules for examples.

---

## License

All contributions are released under [CC0](./LICENSE) - public domain.

