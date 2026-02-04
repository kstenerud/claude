Agent operating principles:
- If an approach isn't working or feels overcomplicated, stop and rethink rather than immediately switching tactics.
- When uncertain about requirements or viability, ask. Correctness over speed.
- Always formulate a minimal plan and get confirmation before proceeding. Propose extras separately.
- If there's uncommitted work in the project, ask before proceeding.
- Maintain a CLAUDE.md file in every project root. Create one if it doesn't exist.
- When reworking tests due to changed functionality, first check if the test still adds value.

Token efficiency:
- Keep responses concise. Don't echo back file contents or restate what was just read.
- Use targeted file reads (specify line ranges) for large files instead of reading the whole file.
- Use the Explore subagent for broad codebase searches instead of multiple sequential Grep/Glob calls.
- Prefer Edit over Write — rewriting whole files costs more tokens.
- Don't re-read files already in the conversation context.
- Batch independent tool calls in parallel.
- Don't over-explain changes unless asked. A brief summary is sufficient.
- Avoid speculative exploration. Don't read files "just in case" — only read what's needed for the current step.
- When a project CLAUDE.md exists, trust it for project structure rather than re-exploring from scratch.
- Don't duplicate global CLAUDE.md content in project CLAUDE.md files. The global file is always loaded; repeating it doubles the cost.

Delegation:
- After planning, delegate each implementation step to a Task subagent using model "sonnet" (or "haiku" for trivial steps like running builds/tests).
- Plans passed to subagents must be self-contained: include exact file paths, what to change, and acceptance criteria.
- Keep architectural decisions and complex debugging in the main agent.
- For single small edits, just do it directly — don't spawn a subagent for trivial work.

Good code:
- Comprehensible to someone unfamiliar with the codebase (principle of least astonishment).
- Follow language/technology best practices and idioms.
- Focus on algorithm and architecture over localized optimizations unless asked.
- Keep project CLAUDE.md files up to date as the project evolves.
- YAGNI: Only build what's needed now. Ask if unsure about the YAGNI/flexibility tradeoff.
- All functionality requires tests. Architect for testability without overcomplicating.
- Simpler solutions are better.

CLAUDE.md in a project:
- Describe: architecture and rationale, idiosyncrasies, how components fit together, each component's purpose/mechanics/responsibilities.
- Avoid code examples unless essential for understanding.
- Update with new insights gained while working.

Naming:
- Names should enhance readability and describe "what", not "how" (exception: specializations where "how" distinguishes them).
- Classes/structs: describe purpose. Functions/methods: describe action or question answered.
- Members: fit purpose in containing type. Instances: describe purpose in algorithm.
- Iterators: prefix with "i" + what's iterated (camelCase or snake_case per convention).

Comments:
- Reserve for non-obvious implementations. Focus on "why" over "how" (except for complex algorithms).
- No code examples in comments. No history (use VCS). Keep comments current.
- Don't remove existing comments without approval. If unclear why one exists, ask.
- Every source file needs a purpose comment near the top, each line prefixed "ABOUTME: " (keep within 80 chars).
