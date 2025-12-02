<picture>
  <source media="(prefers-color-scheme: dark)" srcset=".github/assets/logo-dark.png">
  <source media="(prefers-color-scheme: light)" srcset=".github/assets/logo-light.png">
  <img alt="Best Cursor Rules" src=".github/assets/logo-light.png" width="400">
</picture>

# Best Cursor Rules

**A curated collection of Cursor AI rules that actually work.**

Skip the guesswork. These rules are battle-tested, framework-specific, and ready to drop into your project.

---

## Quick Start

**Option A: Use the Setup Wizard (recommended)**

1. Open your project in Cursor
2. Switch to **Agent Mode** 
3. Paste the contents of [`SETUP-WIZARD.md`](./SETUP-WIZARD.md) into the chat
4. Answer a few questions about your stack
5. Done! The AI creates your `.cursor/rules/` folder automatically

<table>
<tr>
<td>

### 💎 Pro Tip: Use the Best Model

**Use Claude Opus 4 or Sonnet 4 for setup.** One well-executed conversation with a frontier model saves more time than ten attempts with a weaker one.

The wizard analyzes your entire project, asks intelligent questions, and generates perfectly customized rules. This is exactly the kind of complex, multi-step task where model quality compounds—every better decision cascades into better code for months.

*Invest 5 minutes with the best model. Save 50 hours of corrections later.*

</td>
</tr>
</table>

> *"Talk is cheap. Show me the code."*
>
> — **Linus Torvalds**, creator of Linux and Git

---

**Option B: Manual Setup**

1. Create `.cursor/rules/` in your project root
2. Copy the rules you need from the [`rules/`](./rules/) folder
3. Update the `globs` in each file to match your project structure

---

## Available Rules

### Frameworks

| Rule | Description |
|------|-------------|
| [`nextjs-15.mdc`](rules/frameworks/nextjs-15.mdc) | Next.js 15 App Router, Server Components, Server Actions |
| [`react-19.mdc`](rules/frameworks/react-19.mdc) | React 19 patterns, hooks, and best practices |
| [`vue-3.mdc`](rules/frameworks/vue-3.mdc) | Vue 3 Composition API and script setup |
| [`svelte-5.mdc`](rules/frameworks/svelte-5.mdc) | Svelte 5 runes and modern patterns |
| [`astro.mdc`](rules/frameworks/astro.mdc) | Astro components and island architecture |

### Languages

| Rule | Description |
|------|-------------|
| [`typescript.mdc`](rules/languages/typescript.mdc) | Strict TypeScript with modern type patterns |
| [`python.mdc`](rules/languages/python.mdc) | Python 3.12+ with type hints and async |
| [`go.mdc`](rules/languages/go.mdc) | Go idioms and error handling |

### Backends

| Rule | Description |
|------|-------------|
| [`supabase.mdc`](rules/backends/supabase.mdc) | Auth, RLS, Edge Functions, Realtime |
| [`fastapi.mdc`](rules/backends/fastapi.mdc) | FastAPI routes, Pydantic, async patterns |
| [`nodejs.mdc`](rules/backends/nodejs.mdc) | Node.js with Express/Fastify |

### Styling

| Rule | Description |
|------|-------------|
| [`tailwind.mdc`](rules/styling/tailwind.mdc) | Tailwind CSS v4 patterns and organization |
| [`shadcn-ui.mdc`](rules/styling/shadcn-ui.mdc) | shadcn/ui component patterns |

### Testing

| Rule | Description |
|------|-------------|
| [`vitest.mdc`](rules/testing/vitest.mdc) | Vitest with Testing Library |
| [`playwright.mdc`](rules/testing/playwright.mdc) | E2E testing with page objects |

### Best Practices

| Rule | Description |
|------|-------------|
| [`clean-code.mdc`](rules/best-practices/clean-code.mdc) | Naming, functions, DRY, SOLID |
| [`security.mdc`](rules/best-practices/security.mdc) | Auth patterns, secrets, validation |
| [`ai-security.mdc`](rules/best-practices/ai-security.mdc) | LLM security, prompt injection, PII filtering |
| [`accessibility.mdc`](rules/best-practices/accessibility.mdc) | ARIA, keyboard nav, screen readers |

### Stack Presets

These combine multiple rules for common technology combinations:

| Rule | Stack |
|------|-------|
| [`t3-stack.mdc`](rules/stacks/t3-stack.mdc) | Next.js + tRPC + Prisma + Tailwind |
| [`nextjs-supabase.mdc`](rules/stacks/nextjs-supabase.mdc) | Next.js + Supabase + shadcn/ui |
| [`mern-stack.mdc`](rules/stacks/mern-stack.mdc) | MongoDB + Express + React + Node.js |
| [`python-fastapi.mdc`](rules/stacks/python-fastapi.mdc) | FastAPI + PostgreSQL + SQLAlchemy |
| [`django-htmx.mdc`](rules/stacks/django-htmx.mdc) | Django + HTMX + Tailwind |

---

## How the Wizard Works

The Setup Wizard is a special prompt that turns Cursor into a project analyzer:

1. **Detection** - It reads your `package.json`, `tsconfig.json`, config files, etc.
2. **Questions** - Asks 4-6 questions to understand your preferences
3. **Planning** - Shows you exactly which rules will be created
4. **Execution** - Creates `.cursor/rules/` with customized rules

The wizard adapts to your project. Using Supabase? It includes those patterns. TypeScript strict mode? It adjusts accordingly. It's not a one-size-fits-all dump of rules.

> [!TIP]
> **Why Agent Mode?** The wizard needs to read files and create your rules folder. Agent Mode gives the AI the permissions it needs to analyze your project and write the customized rules.

---

## Rule Format

Each rule uses the MDC (Markdown + Config) format:

```markdown
---
description: Brief description for AI context
globs: ["**/*.tsx", "**/*.ts"]
alwaysApply: false
---

# Rule Title

## Section
Content, code examples, tables, etc.
```

- **`description`** - Helps the AI understand when to apply this rule
- **`globs`** - File patterns that trigger this rule (empty = manual only)
- **`alwaysApply`** - If true, always included regardless of file type

Rules are written to be concise and scannable. No fluff, just patterns and examples.

---

## Contributing

Want to add a rule or fix something? Check out [CONTRIBUTING.md](./CONTRIBUTING.md).

The short version:
1. Fork the repo
2. Add/edit rules in `rules/`
3. Follow the format in `.cursor/rules/01-rule-format.mdc`
4. Submit a PR

---

## Why This Exists

Cursor's AI is powerful, but it doesn't know your stack. These rules give it the context it needs:

- "Use Server Components by default" (Next.js 15)
- "Always enable RLS on tables" (Supabase)  
- "Prefer `unknown` over `any`" (TypeScript)

Without rules, you end up correcting the AI constantly. With the right rules, it writes code the way you want it.

---

## Credits

Maintained by [Renvia Technologies](https://renvia.tech) with contributions from the community.

Licensed under [CC0](./LICENSE) - do whatever you want with these rules.

---

<p align="center">
  <sub>Built with ☕ and too many terminal tabs</sub>
</p>

