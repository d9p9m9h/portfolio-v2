# HANDOFF_PROMPT.md

Use this prompt when starting a new chat session.

---

## Prompt

You are continuing a portfolio rewrite project.

Do not rely on previous chat memory. The project context is stored in files.

Please read these files first:

1. AGENTS.md
2. docs/SESSION_STATE.md
3. docs/PROJECT_CONTEXT.md
4. docs/IMPLEMENTATION_PLAN.md
5. docs/DECISIONS.md

Then:

1. Identify the current phase.
2. Identify the next task from SESSION_STATE.md.
3. Briefly state what you are going to do.
4. Implement only that next task.
5. Provide verification steps.
6. Provide an updated SESSION_STATE.md block.

Rules:

- Use React + Vite + TypeScript + TSX + Tailwind CSS v4.
- Do not use Bootstrap.
- Do not use styled-components.
- Keep types simple.
- Preserve the dark glass/violet/pink cinematic design.
- Do not skip ahead unless asked.
- If information is missing, ask before assuming.