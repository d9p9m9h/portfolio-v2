# IMPLEMENTATION_PLAN.md

## Overview

This plan converts the old portfolio into a new React + Vite + TSX + Tailwind CSS v4 project.

The work is divided into small tasks so that a new chat session can continue without losing quality.

Always update `SESSION_STATE.md` after completing a task.

---

## Phase 0 — Context Bootstrap

Goal: make the project understandable across chat sessions.

### T-000 Create project context files

Files:

- AGENTS.md
- docs/PROJECT_CONTEXT.md
- docs/IMPLEMENTATION_PLAN.md
- docs/SESSION_STATE.md
- docs/DECISIONS.md
- docs/HANDOFF_PROMPT.md

Done when:

- all context files exist
- session state has a clear next task
- new chat can resume from files

---

## Phase 1 — Project Scaffold

Goal: create the new app foundation.

### T-010 Scaffold Vite React TypeScript project

Commands:

    npm create vite@latest portfolio-v2 -- --template react-ts
    cd portfolio-v2
    npm install

Done when:

- project runs
- default Vite React TS app loads

---

### T-020 Install and configure Tailwind CSS v4

Commands:

    npm install tailwindcss @tailwindcss/vite

Files:

- vite.config.ts
- src/index.css
- src/App.tsx

Requirements:

- add Tailwind Vite plugin
- use single Tailwind import
- remove default CSS noise
- set dev port to 5174

Done when:

- Tailwind utilities work
- `npm run dev` works
- no old v3 directives are used

---

### T-030 Define design system theme

File:

- src/index.css

Requirements:

- define color tokens in `@theme`
- define radius tokens
- define shadow tokens
- define font stack
- define base body styles
- define smooth scroll
- define section scroll margin
- define selection color
- define custom utilities:
  - glass
  - glass-hover
  - gradient-text
  - gradient-surface

Done when:

- utility classes are available
- body has dark cinematic background
- custom utilities can be used in components

---

### T-040 Copy assets from old project

Files:

- src/assets/heroSection.png
- src/assets/aboutSection.png
- src/assets/contactSection.png

Done when:

- images exist in new project
- imports work

---

## Phase 2 — Types and Data

Goal: create typed content source.

### T-050 Create portfolio types

Files:

- src/types/portfolio.ts

Types:

- Stat
- Profile
- Photo
- NavLink
- Project
- Skill
- Service
- Social
- DevCredit

Done when:

- all types compile
- types are simple and readable

---

### T-060 Create typed portfolio data

File:

- src/data/portfolio.ts

Requirements:

- migrate old content from `portfolio.js`
- add `navLinks`
- type all exports
- keep placeholder hrefs where old data had placeholders
- import images from assets

Done when:

- data file compiles
- content matches old project intent
- nav links are centralized

---

## Phase 3 — Shared UI

Goal: build reusable primitives.

### T-070 Create SectionHeading component

File:

- src/components/ui/SectionHeading.tsx

Props:

- tag
- title
- sub optional

Done when:

- component is typed
- responsive heading looks correct
- tag pill and subtitle styles match design

---

### T-080 Create shared button/card primitives

Files:

- src/components/ui/GlassCard.tsx
- src/components/ui/GradientButton.tsx
- src/components/ui/GhostButton.tsx

Done when:

- primitives are typed
- classes are reusable
- hover/focus states work

---

## Phase 4 — Sections

Goal: implement page sections one by one.

### T-090 Implement App shell

File:

- src/App.tsx

Requirements:

- render section placeholders or actual sections as they become available
- keep correct page order

Done when:

- App composes all planned sections
- page scroll order is correct

---

### T-100 Implement Navbar

File:

- src/components/sections/Navbar.tsx

Requirements:

- fixed glass navbar
- brand gradient text
- desktop links
- mobile burger
- mobile menu state
- links from data
- accessible toggle

Done when:

- navigation works
- mobile menu works
- no Bootstrap is used

---

### T-110 Implement Hero

File:

- src/components/sections/Hero.tsx

Requirements:

- full-height hero
- glow orbs
- eyebrow pill
- gradient headline
- CTA buttons
- stacked artboard on large screens
- hidden artboard on mobile
- no duplicated tagline

Done when:

- hero matches design intent
- responsive behavior works

---

### T-120 Implement About

File:

- src/components/sections/About.tsx

Requirements:

- portrait card
- bio paragraphs
- stat cards
- gradient stat values
- responsive two-column layout

Done when:

- content comes from data
- layout is responsive
- dead old code is not carried over

---

### T-130 Implement Projects

File:

- src/components/sections/Projects.tsx

Requirements:

- category filter state
- filter chips
- responsive project grid
- project cards
- gradient covers from project colors
- hover lift

Done when:

- filtering works
- cards render from typed data
- layout is responsive

---

### T-140 Implement Skills

File:

- src/components/sections/Skills.tsx

Requirements:

- left heading/tool list
- right glass skill panel
- progress bars using level percentage
- typed data

Done when:

- bars render correct widths
- layout is responsive

---

### T-150 Implement Services

File:

- src/components/sections/Services.tsx

Requirements:

- responsive service grid
- glass cards
- emoji icons
- pink hover glow

Done when:

- cards render from data
- hover style is distinct from project cards

---

### T-160 Implement Contact

File:

- src/components/sections/Contact.tsx

Requirements:

- contact heading
- email link
- social pills
- contact form MVP
- accessible labels
- simple status message
- no dead code

Done when:

- form UI is accessible
- layout is responsive
- submission behavior is intentionally defined

---

### T-170 Implement Footer

File:

- src/components/sections/Footer.tsx

Requirements:

- glass footer
- copyright
- dev credit
- working hover states

Done when:

- footer is responsive
- no empty spacer
- hover states work

---

## Phase 5 — Polish and QA

Goal: stabilize quality.

### T-180 Responsive QA

Checks:

- 360px
- 768px
- 1024px
- 1440px

Done when:

- no horizontal overflow
- spacing feels intentional
- navbar and menus work
- sections clear fixed navbar

---

### T-190 Accessibility QA

Checks:

- keyboard navigation
- focus visibility
- form labels
- alt text
- aria-labels
- heading order

Done when:

- major accessibility issues are resolved

---

### T-200 Build verification

Commands:

    npm run build
    npm run preview

Done when:

- production build succeeds
- preview works
- no TypeScript errors
- no console errors

---

## Phase 6 — Optional Enhancements

These are not required for MVP.

### T-210 Optional scroll-spy

Add active nav highlighting based on visible section.

### T-220 Optional skill bar reveal animation

Animate bars when section enters viewport.

### T-230 Optional real project links/thumbnails

Replace gradient covers and placeholder links.

### T-240 Optional contact backend

Connect form to:

- Formspree
- EmailJS
- custom API

---

## Task Execution Contract

For every task:

1. Read `SESSION_STATE.md`
2. Identify next task
3. Implement only that task
4. Verify
5. Output updated `SESSION_STATE.md`

Do not jump ahead unless explicitly instructed.