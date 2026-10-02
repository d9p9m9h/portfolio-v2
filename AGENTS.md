# AGENTS.md — Portfolio Rewrite Project

## Mission

This project is being rebuilt from an older portfolio into a modern single-page portfolio using:

- React
- Vite
- TypeScript / TSX
- Tailwind CSS v4

The old project used:

- React
- Bootstrap 5
- styled-components
- global/plain CSS-like tokens

The new project must not mix old styling systems into the new codebase.

---

## Source of Truth

Always read these files in this order before doing any implementation work:

1. `docs/SESSION_STATE.md`
2. `docs/PROJECT_CONTEXT.md`
3. `docs/IMPLEMENTATION_PLAN.md`
4. `docs/DECISIONS.md`

If any file conflicts with chat memory, trust the files.

---

## Session Rules

### 1. Do not rely on previous chat memory

A new chat session must be able to continue safely.

Always resume from:

- current phase
- next task
- completed tasks
- blocked issues

inside `docs/SESSION_STATE.md`.

### 2. Work task-by-task

Do not attempt the whole project at once.

Continue only the **Next Task** listed in `docs/SESSION_STATE.md`.

If the next task is unclear, stop and ask.

### 3. One task, one clear output

For each task, provide:

1. Task ID
2. Files to create/change
3. Implementation
4. Verification steps
5. Updated `SESSION_STATE.md` block

### 4. Preserve the design language

The visual identity must remain:

- dark-only
- cinematic
- glassmorphism
- violet/pink gradient
- modern, clean, premium
- mobile-first responsive

Do not make it look like a generic Bootstrap template.

### 5. Use the target stack only

Allowed:

- React
- Vite
- TypeScript
- TSX
- Tailwind CSS v4
- CSS-first Tailwind theme via `@theme`
- custom Tailwind utilities using `@utility`

Forbidden in new code:

- Bootstrap classes
- styled-components
- large global CSS files
- component-scoped plain CSS unless absolutely necessary
- unnecessary dependencies

---

## TypeScript Rules

Keep types simple.

Prefer:

- `string`
- `number`
- `boolean`
- arrays
- simple interfaces
- inline prop types

Example:

    interface SectionHeadingProps {
      tag: string;
      title: string;
      sub?: string;
    }

Do not over-engineer types.

Use `any` only as a temporary escape hatch when external data or runtime behavior becomes too complex.

---

## Tailwind CSS v4 Rules

Use Tailwind v4 CSS-first configuration.

Main CSS should use:

    @import "tailwindcss";

Theme tokens should be defined in `@theme`.

Custom reusable utilities should use `@utility`.

Do not use deprecated v3 directives:

    @tailwind base;
    @tailwind components;
    @tailwind utilities;

Use Vite plugin:

    @tailwindcss/vite

---

## Quality Guardrails

Every implemented task must satisfy:

- TypeScript compiles without errors
- no Bootstrap classes introduced
- no styled-components introduced
- responsive on mobile, tablet, desktop
- preserves dark glass/violet/pink aesthetic
- uses content from typed data file where applicable
- accessible semantics:
  - proper headings
  - labels
  - alt text
  - aria-label for icon-only controls
  - visible focus states
- no dead code intentionally left behind

---

## State Updating Rule

After completing any task, always output an updated version of:

    docs/SESSION_STATE.md

The update must include:

- last updated date
- current phase
- completed task
- next task
- files changed
- verification result
- blockers
- notes for next session

---

## Definition of Done

A task is done only when:

1. requested code is implemented
2. it follows target stack rules
3. it preserves design intent
4. it is typed
5. it is responsive
6. verification steps are provided
7. `SESSION_STATE.md` is updated