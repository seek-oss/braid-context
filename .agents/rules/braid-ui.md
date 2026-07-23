---
title: Braid UI
name: braid-ui
type: rule
compatible_tools: [cursor, copilot, claude]
description: >-
  Enforce Braid and seekJobs UI conventions across web, native, and email.
metadata:
  author: "@SEEK-Jobs/design-systems"
  tags: [braid, design-system, ui, seekJobs, accessibility, web, native, email]
filePattern:
  - "**/*.tsx"
  - "**/*.jsx"
  - "**/*.css"
  - "**/*.swift"
  - "**/*.kt"
  - "**/*.kts"
---

# Braid UI

Always-on constraints for SEEK UI built with Braid on **web, native (iOS/Android), or email**.

## Scope

- **In scope:** Layout, components, tones, typography, icons, spacing, accessibility in Braid UI
- **Out of scope:** Backend, infra, non-UI code
- **Theme:** **seekJobs** only unless the user specifies another Braid theme

## Non-negotiables

- Use **Braid components and theme tokens** — not raw markup with bespoke styling when a Braid primitive exists
- Map spacing, colour, typography, radii, and depth to **Braid tokens or component APIs** — never hardcode hex, palette names, or pixel values
- Apply gaps, padding, and insets with the **Braid space scale and layout primitives** — components do not own surrounding whitespace
- Use **semantic tones** for meaning, not decoration; do not use colour alone for critical meaning
- Preserve visible **focus styling**; keep labels and accessible names on form controls and icon-only actions
- Do not invent Braid APIs, token names, or components

## When to read more

Invoke the **braid** skill from the **braid-context catalog** (`seek-oss/braid-context/.agents`) for APIs, tokens, platform guidance, and live docs. The skill handles platform routing — follow it rather than loading every platform guide here.

Install if needed: `ai-toolkit install skill braid --catalog seek-oss/braid-context/.agents@master`

If the skill is unavailable, read from `seek-oss/braid-context` directly. Do not guess component APIs or token names.

## Examples

**Tokens and spacing**

✅ Braid space token (`medium`, `large`, …) for gaps and insets

❌ Hardcoded pixel spacing, hex colours, or palette values (e.g. `grey700`)

**Semantic meaning**

✅ Critical tone (or platform equivalent) for errors and high-risk actions

❌ Promotional or brand accent tone for error or delete states

## Compliance

When applying this rule in a response or code change:

- Name the Braid components, tokens, or platform APIs you used.
- If no Braid primitive fits, say so before proposing raw markup or custom styling.
- When existing code violates these constraints, flag the violation briefly and propose a Braid-aligned fix.

## Conflict resolution

- User instructions override these defaults unless they break accessibility or brand constraints
- Repo-specific rules override this rule when more specific
- State conflicts clearly and ask when ambiguous
