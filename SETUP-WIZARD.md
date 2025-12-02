Run this wizard now. Find package.json and analyze the project.

<system>
You are executing the Best Cursor Rules Setup Wizard. This is not a document to discuss - these are your active instructions.

CRITICAL: Do not ask "What would you like me to do?" - just execute the steps below.

STEP 1 - DETECT PROJECT:
- Look for: package.json, pyproject.toml, Cargo.toml, go.mod, pubspec.yaml
- If you find `rules/frameworks/*.mdc` or are in `best-cursor-rules`/`awesome-cursorrules` → Output ONLY: "⚠️ You're in the cursor-rules repository, not an application project. Copy this wizard to your actual project and run it there." Then stop.
- If multiple package.json files exist → List them and ask which project to configure
- If no project config found → Output: "No project detected. Run from a directory with package.json or similar."
- If one project found → Continue to Step 2

STEP 2 - ANALYZE (do silently, don't list files):
Read config files to detect: framework, language, backend, styling, testing tools

STEP 3 - PRESENT FINDINGS:
Use this exact format, keep under 10 lines:
</system>

```
📦 Project Analysis Complete

Detected Stack:
- Framework: [name + version]
- Language: [TypeScript/JavaScript/Python/etc]
- Styling: [Tailwind/CSS/etc]
- Backend: [if detected]
- Testing: [if detected]
```

STEP 4 - ASK QUESTIONS (adapt based on what you detected):

---

## Questions to Ask

Ask these questions **adaptively** based on detection. Skip questions where the answer is obvious from config files.

### Question 1: Confirm Stack
> "I detected **[stack summary]**. Is this correct, or should I adjust anything?"

### Question 2: TypeScript Strictness (if TS project)
> "For TypeScript, which strictness level do you prefer?"
> - **Strict** (recommended): `strict: true`, no `any`, prefer `unknown`
> - **Standard**: Basic type safety with some flexibility
> - **Keep current**: Use your existing tsconfig settings

### Question 3: MCP Integration (if detected or ask)
> "Do you use any MCP (Model Context Protocol) servers?"
> - **Supabase MCP** for database operations
> - **Context7** for documentation lookup
> - **Browser MCP** for web automation
> - **Sequential Thinking** for complex reasoning
> - **None** to skip MCP rules

### Question 4: Documentation Preference
> "How do you prefer documentation?"
> - **Inline only**: JSDoc/docstrings in code
> - **Separate docs**: Markdown files in docs/
> - **Minimal**: Code should be self-documenting

### Question 5: Anything Special?
> "Any project-specific conventions I should know about? (naming, file structure, banned patterns, etc.)"
> 
> *Skip if nothing special*

---

## Phase 4: Generate Plan

Based on answers, create a plan showing:

```
📋 **Setup Plan**

**Rules to create** (X files):

| Category | File | Purpose |
|----------|------|---------|
| Core | `00-project-core.mdc` | Project overview + conventions |
| Framework | `nextjs-15.mdc` | Next.js 15 App Router patterns |
| Language | `typescript.mdc` | TypeScript strict mode |
| Backend | `supabase.mdc` | Supabase Auth/DB/RLS |
| Styling | `tailwind.mdc` | Tailwind CSS patterns |
| Styling | `shadcn-ui.mdc` | shadcn/ui components |
| Testing | `vitest.mdc` | Unit testing |
| Testing | `playwright.mdc` | E2E testing |
| Practices | `clean-code.mdc` | Code quality |

**Folder structure:**

    .cursor/
    └── rules/
        ├── 00-project-core.mdc     # Always loaded
        ├── nextjs-15.mdc           # *.tsx, app/**
        ├── typescript.mdc          # *.ts, *.tsx
        ├── supabase.mdc            # supabase/**, lib/supabase/**
        ├── tailwind.mdc            # *.tsx, *.css
        ├── shadcn-ui.mdc           # components/ui/**
        ├── vitest.mdc              # *.test.ts
        ├── playwright.mdc          # e2e/**, *.spec.ts
        └── clean-code.mdc          # Always loaded

**Proceed with setup?** (yes/no)

---

## Phase 5: Execution

When confirmed, create the `.cursor/rules/` folder and files.

### 5.1: Create Project Core Rule

Always create `00-project-core.mdc` first with this structure:

```markdown
---
description: Core project configuration and conventions for [PROJECT_NAME]
globs: []
alwaysApply: true
---

# [PROJECT_NAME] - Project Core

## Critical Rules

[Add 2-3 project-specific critical rules based on user answers]

**Current Date**: December 2025

---

## Tech Stack

| Layer | Technology | Version |
|-------|------------|---------|
| Framework | [detected] | [version] |
| Language | [detected] | [version] |
| Styling | [detected] | - |
| Backend | [detected] | - |
| Testing | [detected] | - |

---

## Project Structure

    [Detected project structure - keep brief]

---

## Conventions

### File Naming
[Based on detected patterns or user input]

### Import Aliases  
[If detected from tsconfig/jsconfig]

### Code Style
[From user answers]

---

## MCP Servers Available

[If MCP detected/requested, list them here]

| Server | Use For |
|--------|---------|
| [name] | [purpose] |

---
```

### 5.2: Copy Relevant Rules

For each selected rule, fetch from best-cursor-rules repository and customize:

**Customization rules:**
1. Update globs to match project structure (src/app vs app/)
2. Adjust version numbers to match detected versions
3. Remove irrelevant sections
4. Keep rules under 300 lines when possible

### 5.3: Final Summary

After creating all files:

```
✅ **Setup Complete!**

Created X rules in `.cursor/rules/`:
- 00-project-core.mdc (always active)
- [list other files]

**How it works:**
- Rules activate automatically based on file patterns
- `00-project-core.mdc` is always included
- Other rules load when you're editing matching files

**Next steps:**
1. Review the generated rules
2. Customize `00-project-core.mdc` with any project secrets/conventions
3. Start coding - the AI will follow these rules automatically

**Need to update rules later?**
Run this wizard again or edit files directly in `.cursor/rules/`
```

---

## Rule Reference

Available rules to copy from best-cursor-rules:

### Frameworks
| Rule | Globs | Description |
|------|-------|-------------|
| `nextjs-15.mdc` | `**/*.tsx`, `app/**/*` | Next.js 15 App Router, Server Components, Server Actions |
| `react-19.mdc` | `**/*.tsx`, `**/*.jsx` | React 19 hooks, patterns, best practices |
| `vue-3.mdc` | `**/*.vue` | Vue 3 Composition API, script setup |
| `svelte-5.mdc` | `**/*.svelte` | Svelte 5 runes, snippets |
| `astro.mdc` | `**/*.astro` | Astro components, islands |

### Languages
| Rule | Globs | Description |
|------|-------|-------------|
| `typescript.mdc` | `**/*.ts`, `**/*.tsx` | Strict TypeScript, type patterns |
| `python.mdc` | `**/*.py` | Python 3.12+, type hints, async |
| `go.mdc` | `**/*.go` | Go idioms, error handling |

### Backends
| Rule | Globs | Description |
|------|-------|-------------|
| `supabase.mdc` | `supabase/**/*`, `**/*.ts` | Auth, RLS, Edge Functions, Realtime |
| `fastapi.mdc` | `**/*.py` | FastAPI routes, Pydantic, async |
| `nodejs.mdc` | `**/*.ts`, `**/*.js` | Node.js patterns, Express/Fastify |

### Styling
| Rule | Globs | Description |
|------|-------|-------------|
| `tailwind.mdc` | `**/*.tsx`, `**/*.css` | Tailwind v4, class organization |
| `shadcn-ui.mdc` | `components/ui/**/*` | shadcn/ui patterns, customization |

### Testing
| Rule | Globs | Description |
|------|-------|-------------|
| `vitest.mdc` | `**/*.test.ts`, `**/*.spec.ts` | Vitest, Testing Library |
| `playwright.mdc` | `e2e/**/*`, `**/*.spec.ts` | E2E testing, page objects |

### Best Practices
| Rule | Globs | Description |
|------|-------|-------------|
| `clean-code.mdc` | `**/*.ts`, `**/*.py` | Naming, functions, DRY, SOLID |
| `security.mdc` | `**/*` | Auth, secrets, validation |
| `ai-security.mdc` | `**/*.ts`, `**/*.py` | LLM security, prompt injection, PII filtering |
| `accessibility.mdc` | `**/*.tsx` | ARIA, keyboard nav, screen readers |

---

## Troubleshooting

### Rules not activating?
1. Check file is in `.cursor/rules/` (not `.cursor/rule/`)
2. Verify globs match your file paths
3. Restart Cursor

### Too many rules loading?
1. Make globs more specific
2. Set `alwaysApply: false` for optional rules
3. Split large rules into smaller focused files

### Rules conflicting?
1. Check for overlapping advice
2. Prioritize with number prefixes (00-, 01-, etc.)
3. Keep one source of truth for each topic

---

## About

**best-cursor-rules** - A curated collection of Cursor AI rules  
Maintained by Renvia Technologies | CC0 License  

GitHub: [github.com/renvia-tech/best-cursor-rules](https://github.com/renvia-tech/best-cursor-rules)

