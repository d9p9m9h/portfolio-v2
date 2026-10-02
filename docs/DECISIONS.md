# DECISIONS.md

## D-001 — Rewrite instead of patching old project

Decision:

Build a new clean project using React + Vite + TSX + Tailwind CSS v4.

Reason:

The old project mixes Bootstrap, styled-components, and global/plain styling. A clean rewrite avoids carrying unnecessary complexity.

---

## D-002 — Tailwind CSS v4 is the only styling system

Decision:

Use Tailwind CSS v4 only.

Forbidden:

- Bootstrap
- styled-components
- large plain CSS files

Reason:

A single styling system prevents architecture drift and improves maintainability.

---

## D-003 — Use CSS-first Tailwind configuration

Decision:

Use:

- `@import "tailwindcss"`
- `@theme`
- `@utility`

Reason:

Tailwind v4 prefers CSS-first configuration and the Vite plugin.

---

## D-004 — Keep TypeScript simple

Decision:

Use simple interfaces and primitive types.

Reason:

The project is a portfolio, not a complex domain app. Simple types improve readability and reduce context overhead.

---

## D-005 — Preserve original visual identity

Decision:

Keep:

- dark theme
- glassmorphism
- violet/pink gradients
- rounded cards
- hover lift
- cinematic feel

Reason:

The old design identity is the product’s main value.

---

## D-006 — Content remains centralized

Decision:

All content should live in typed data files.

Reason:

This was a strength of the old project and makes future edits easier.

---

## D-007 — Navbar links move into data

Decision:

Add `navLinks` to `src/data/portfolio.ts`.

Reason:

Old project had navbar links inside the component, breaking the content-centralization rule.

---

## D-008 — Contact form MVP first

Decision:

Implement an accessible contact form UI first. Backend/service integration can be added later.

Reason:

The old contact form logic was dead code. The new project should have an intentional form state.

---

## D-009 — Dev server port remains 5174

Decision:

Use port 5174.

Reason:

This matches the old project convention and avoids clash with another local app.