# PROJECT_CONTEXT.md

## Project Goal

Rebuild the existing filmmaker/editor portfolio as a modern, maintainable single-page website using:

- React
- Vite
- TypeScript / TSX
- Tailwind CSS v4

The final result should preserve the old portfolio’s identity:

- dark cinematic theme
- glassmorphism cards
- violet/pink gradient accents
- premium creative portfolio feel
- smooth section-based scrolling

but with a cleaner architecture and no mixed styling systems.

---

## Old Project Summary

Old project path:

    C:\__d9p__\portfolio_template

Old stack:

- React 19
- Vite
- Bootstrap 5
- styled-components
- global styled-components tokens
- JavaScript, not TypeScript

Old architecture strengths:

- all content centralized in `src/data/portfolio.js`
- components are mostly presentational
- simple one-way data flow
- clear section composition

Old architecture problems:

- Bootstrap + styled-components + plain/global CSS are mixed
- no TypeScript
- dead code in Contact and About
- Navbar links not centralized in data file
- placeholder social/project links
- no real contact form backend
- possible filename mismatch between `Project.jsx` and `Projects.jsx`

---

## Target Project

New target stack:

- React
- Vite
- TypeScript
- TSX components
- Tailwind CSS v4
- `@tailwindcss/vite`
- CSS-first theme configuration using `@theme`
- custom utilities using `@utility`

Target principles:

- mobile-first responsive layout
- grid/flexbox layout
- OKLCH-friendly dynamic color palette
- simple TypeScript types
- content-driven data file
- reusable section components
- no Bootstrap
- no styled-components
- minimal plain CSS

---

## Target Directory Structure

Recommended new structure:

    src/
    ├── main.tsx
    ├── App.tsx
    ├── index.css
    ├── assets/
    │   ├── heroSection.png
    │   ├── aboutSection.png
    │   └── contactSection.png
    ├── components/
    │   ├── ui/
    │   │   ├── SectionHeading.tsx
    │   │   ├── GlassCard.tsx
    │   │   ├── GradientButton.tsx
    │   │   └── GhostButton.tsx
    │   └── sections/
    │       ├── Navbar.tsx
    │       ├── Hero.tsx
    │       ├── About.tsx
    │       ├── Projects.tsx
    │       ├── Skills.tsx
    │       ├── Services.tsx
    │       ├── Contact.tsx
    │       └── Footer.tsx
    ├── data/
    │   └── portfolio.ts
    └── types/
        └── portfolio.ts

---

## Page Composition

The page remains a single-page scrolling portfolio.

Order:

1. Navbar
2. Hero, id `home`
3. About, id `about`
4. Projects, id `projects`
5. Skills, id `skills`
6. Services, id `services`
7. Contact, id `contact`
8. Footer

Navigation uses anchor links:

    #home
    #about
    #projects
    #skills
    #services
    #contact

Global scroll behavior:

- smooth scroll
- sections have scroll margin to clear fixed navbar
- overflow-x hidden on body

---

## Design System

### Visual Identity

The UI must remain:

- dark-only
- glassy
- cinematic
- violet/pink gradient
- soft glow accents
- rounded cards
- subtle borders
- smooth hover lift

### Color Intent

Original tokens:

- background: `#0b0b12`
- surface: `#14141f`
- surface-2: `#1b1b2a`
- border: `rgba(255,255,255,0.08)`
- accent: `#8b5cf6`
- accent-2: `#ec4899`
- text: `#eceaf6`
- muted: `#9b97b0`
- glass background: `rgba(20,20,31,0.7)`
- glass border: `rgba(255,255,255,0.1)`
- glass blur: `20px`

Target: preserve the same visual feeling, but define colors in Tailwind v4 theme. OKLCH values may be used and adjusted visually.

### Recommended Tailwind v4 Theme Names

Use semantic names:

- `base` for page background
- `surface`
- `surface-2`
- `ink` for primary text
- `muted`
- `line` for borders
- `accent`
- `accent-2`
- `success`

Example theme variable names:

    --color-base
    --color-surface
    --color-surface-2
    --color-ink
    --color-muted
    --color-line
    --color-accent
    --color-accent-2
    --color-success

### Glass Recipe

Reusable glass style:

- semi-transparent dark background
- backdrop blur
- subtle border
- soft shadow
- rounded corners
- hover lift

Suggested Tailwind utility names:

    glass
    glass-hover
    gradient-text
    gradient-surface

Example usage:

    <div class="glass glass-hover rounded-card p-6">
      content
    </div>

### Gradient Recipe

Text gradient:

- direction: 90deg
- from accent
- to accent-2

Button/cover gradient:

- direction: 135deg
- from accent
- to accent-2

---

## Tailwind v4 Implementation Notes

Use one main CSS file, for example `src/index.css`.

Main CSS should start with:

    @import "tailwindcss";

Define theme tokens in:

    @theme {
      ...
    }

Define custom utilities in:

    @utility glass {
      ...
    }

Do not use old v3 directives.

Use Vite plugin:

    import tailwindcss from "@tailwindcss/vite";

Recommended Vite config plugins:

- react plugin
- tailwindcss plugin

Recommended dev server port:

    5174

---

## TypeScript Rules

Use simple types.

Prefer:

    string
    number
    boolean
    string[]
    number[]
    interface

For component props, use inline types or local interfaces.

Example:

    interface SectionHeadingProps {
      tag: string;
      title: string;
      sub?: string;
    }

Avoid complex generics unless necessary.

Use `any` only temporarily if needed.

---

## Data Model

All site content should live in typed data files.

Recommended files:

    src/types/portfolio.ts
    src/data/portfolio.ts

### Core Types

    export interface Stat {
      value: string;
      label: string;
    }

    export interface Profile {
      name: string;
      devName: string;
      role: string;
      tagline: string;
      location: string;
      email: string;
      bio: string[];
      stats: Stat[];
    }

    export interface Photo {
      heroImg: string;
      aboutImg: string;
      contImg: string;
    }

    export interface NavLink {
      label: string;
      href: string;
    }

    export interface Project {
      id: string;
      title: string;
      category: string;
      year: number;
      colors: string[];
    }

    export interface Skill {
      name: string;
      level: number;
    }

    export interface Service {
      icon: string;
      title: string;
      text: string;
    }

    export interface Social {
      name: string;
      href: string;
    }

    export interface DevCredit {
      name: string;
      href: string;
    }

### Data Rules

- all copy/content should be in `src/data/portfolio.ts`
- components should not hardcode nav links
- components should import data directly
- no unnecessary prop drilling
- only shared presentational components receive props

---

## Component Specifications

### App.tsx

Responsibility:

- composition root
- renders Navbar, main sections, Footer
- default export

Structure:

    Navbar
    main
      Hero
      About
      Projects
      Skills
      Services
      Contact
    Footer

---

### Navbar.tsx

Requirements:

- fixed top
- glass background
- high z-index
- inner height around 68px
- brand links to `#home`
- brand name uses gradient text
- desktop links hidden below `lg`
- burger menu visible below `lg`
- mobile menu closes when link clicked
- CTA “Let’s talk” hidden on very small screens
- links must come from data file

State:

- `open: boolean`

Known issue to fix:

- move navbar links into data file

---

### Hero.tsx

Requirements:

- section id `home`
- min-height screen
- top padding larger than normal section
- decorative violet/pink blurred glow orbs
- left column:
  - eyebrow glass pill with animated green dot
  - role and availability text
  - large heading with gradient highlight
  - primary gradient CTA to `#projects`
  - ghost glass CTA to `#contact`
- right column:
  - stacked rotated cards
  - hero image
  - hidden below `lg`

Known issue to fix:

- do not duplicate the same tagline twice

---

### About.tsx

Requirements:

- section id `about`
- SectionHeading:
  - tag: About
  - title: Film maker, editor & visual storyteller
- left:
  - portrait image card
- right:
  - bio paragraphs
  - stats cards
- stats values use gradient text

Known issue to fix:

- remove dead code like unused initials or commented overlay

---

### Projects.tsx

Requirements:

- section id `projects`
- surface band background
- top and bottom borders
- SectionHeading:
  - tag: Portfolio
  - title: Selected projects
- category filter chips
- active chip uses gradient background
- inactive chips use glass style
- project grid responsive
- project card:
  - glass card
  - gradient cover generated from project colors
  - category label
  - title
  - meta: category and year
- hover lift with violet glow

State:

- active category filter

Known issue to fix:

- use correct filename `Projects.tsx`

---

### Skills.tsx

Requirements:

- section id `skills`
- left column:
  - SectionHeading
  - tool pills
- right column:
  - glass panel
  - skill rows
- each skill row:
  - name
  - percentage
  - progress track
  - gradient fill based on level

Implementation note:

- use inline style width for dynamic level:

      style={{ width: `${skill.level}%` }}

Optional improvement:

- animate bars on reveal, but not required for MVP

---

### Services.tsx

Requirements:

- section id `services`
- surface band background
- SectionHeading:
  - tag: Services
  - title: What I can do for you
- responsive card grid
- each card:
  - glass card
  - emoji icon
  - title
  - muted text
- hover:
  - lift
  - pink glow instead of violet glow

---

### Contact.tsx

Requirements:

- section id `contact`
- SectionHeading:
  - tag: Contact
  - title: Let’s build something great
- left:
  - lead text
  - email link
  - social pills
- right:
  - contact form

Contact form MVP:

- name field
- email field
- message field
- submit button
- accessible labels
- simple form status message
- backend/service integration can be connected later

Known issue to fix:

- remove old dead `sent` state and unused `react-dom` import
- replace dead form logic with intentional form UI

---

### Footer.tsx

Requirements:

- glass footer
- top border
- copyright text
- developed by credit
- credit may use gradient text
- hover states should actually work

Known issue to fix:

- remove empty spacer element
- do not let gradient parent kill link hover color

---

### SectionHeading.tsx

Props:

    interface SectionHeadingProps {
      tag: string;
      title: string;
      sub?: string;
    }

Requirements:

- optional tag pill
- large responsive title
- optional muted subtitle
- consistent bottom margin

---

## Known Issues From Old Project To Fix

| Issue | Fix in new project |
|---|---|
| `Project.jsx` vs `Projects.jsx` mismatch | Use `Projects.tsx` |
| Contact dead state and unused import | Implement intentional contact form or remove dead code |
| About dead initials/overlay code | Remove dead code |
| Footer empty spacer and broken hover | Rebuild footer cleanly |
| Hero duplicates tagline | Use one clear hero message |
| Navbar links inside component | Move nav links to data file |
| Placeholder social links | Keep typed placeholders but mark TODO |
| Static skill bars | Keep static for MVP, optional animation later |
| No TypeScript | Use TSX and typed data |
| Mixed styling systems | Use Tailwind v4 only |

---

## Content Migration Source

Copy content from old project:

    src/data/portfolio.js

Into new typed file:

    src/data/portfolio.ts

Preserve:

- profile
- photo imports
- projects
- skills
- services
- socials
- dev credit

Add:

- navLinks

---

## Accessibility Requirements

Every component should include:

- semantic HTML elements
- proper heading hierarchy
- alt text for meaningful images
- labels for form fields
- aria-label for burger menu
- visible focus states
- sufficient contrast
- keyboard operable navigation and form

---

## Performance Requirements

- avoid unnecessary dependencies
- lazy-load below-the-fold images if useful
- keep animations subtle
- avoid large global CSS
- use Tailwind utilities and small custom utilities
- ensure production build passes

---

## Verification Commands

Use:

    npm run dev

Use:

    npm run build

Use TypeScript check if available:

    npx tsc --noEmit

Manual checks:

- mobile 360px
- tablet 768px
- laptop 1024px
- desktop 1440px
- navbar anchor navigation
- project filter behavior
- contact form usability
- hover/focus states