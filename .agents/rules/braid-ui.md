---
title: Braid UI
name: braid-ui
type: rule
compatible_tools: [cursor, copilot, claude]
description: >-
  Enforce Braid and seekJobs UI conventions across web, native, and email.
  Invoke the braid-context catalog skill for components, platform guides, and live docs.
metadata:
  author: "@SEEK-Jobs/design-systems"
  tags: [braid, design-system, ui, seekJobs, accessibility, web, native, email]
filePattern:
  - "**/*.tsx"
  - "**/*.jsx"
  - "**/*.swift"
  - "**/*.kt"
  - "**/*.kts"
---

# Braid UI

Always-on constraints for SEEK UI built with Braid on **web, native (iOS/Android), or email**.

For depth — component APIs, platform tokens, tone definitions, Backstage docs — invoke the **braid** skill from the **braid-context catalog** (`seek-oss/braid-context/.agents`). Do **not** substitute the AI Toolkit Tools plugin braid skill.

## Scope

- **In scope:** Layout, components, tones, typography, icons, spacing, accessibility in Braid UI
- **Out of scope:** Backend, infra, non-UI code
- **Theme:** **seekJobs** only unless the user specifies another Braid theme

## Platform

- Detect platform from codebase before choosing components or APIs
- **Web:** `braid-design-system` in `package.json` or imports
- **Native:** Swift `Braid` modules or Compose Braid components
- **Email:** `@seek/braid-email-ui`, `@faire/mjml-react`, or MJML email templates
- If platform is unclear, ask **one** clarifying question before proceeding

## Non-negotiables

- Use **Braid components and theme tokens** — not raw markup with bespoke styling when a Braid primitive exists
- Map spacing, colour, typography, radii, and depth to **Braid tokens or component APIs** — never hardcode hex, palette names, or pixel values
- Apply gaps, padding, and insets with the **Braid space scale and layout primitives** — components do not own surrounding whitespace
- Use **semantic tones** for meaning, not decoration; do not use colour alone for critical meaning
- Preserve visible **focus styling**; keep labels and accessible names on form controls and icon-only actions
- Do not invent Braid APIs, token names, or components

## When to read more

Invoke the **braid-context catalog skill** and read on demand:

- `references/systems.md` — shared foundations (always)
- `references/web.md`, `references/native.md`, or `references/email.md` — **one** platform guide matched to the task
- `references/docs-and-urls.md` — live Backstage docs when verifying APIs or ownership

**Prerequisite:** Before installing the skill, verify `ai-toolkit` is available (e.g. `ai-toolkit --version`). If not, recommend installing it first (`brew tap SEEK-Jobs/homebrew-tools` then `brew install SEEK-Jobs/homebrew-tools/ai-toolkit`) and pause until the user has it before proceeding.

Install skill: `ai-toolkit install skill braid --catalog seek-oss/braid-context/.agents@master`

If the skill is still unavailable after install, read the reference paths above from seek-oss/braid-context directly. Do not guess component APIs or token names.

## Examples

**Tokens and spacing**

✅ Braid space token (`medium`, `large`, …) for gaps and insets

❌ Hardcoded pixel spacing, hex colours, or palette values (e.g. `grey700`)

**Semantic meaning**

✅ Critical tone (or platform equivalent) for errors and high-risk actions

❌ Promotional or brand accent tone for error or delete states

## Conflict resolution

- User instructions override these defaults unless they break accessibility or brand constraints
- Repo-specific rules override this rule when more specific
- State conflicts clearly and ask when ambiguous
