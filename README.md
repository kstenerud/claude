Claude Optimization Strategies
==============================

* Put a [`CLAUDE.md`](CLAUDE.md) in your `$HOME/.claude` dir
* Start new conversations for unrelated tasks. Context accumulates and the entire history gets processed on every turn. A 50-turn conversation about feature A is wasted context when you pivot to feature B.
* Use `/compact` when a conversation gets long but you still need continuity. It summarizes the context, freeing up tokens.
* Use Sonnet as your default model, switch to Opus only for complex architecture/debugging. Most routine coding doesn't need Opus.
* Be specific in requests. "Fix the null check in src/auth/login.ts:47" costs far less than "fix the login bug" because the agent doesn't have to search.
* Use `.claudeignore` (hard block) or `.gitignore` (soft block) to exclude directories the agent should not search (build output, node_modules, vendored deps, large data files). Every broad search scans these otherwise.
* Make sure the CLAUDE.md in your project directory has all the info that would be expensive to re-learn. In particular, it should list out the major directories and what they are for. This helps cut down on how much Claude will scan, because it'll know which directories contain info that's unrelated to its task.
* Provide file paths when you know them. Saves entire exploration rounds.

## Issues with latest version

Currently, the latest Claude is borked and consumes too many tokens. Install 2.0.76 and tell it not to update:

```bash
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code@2.0.76
```

Edit `$HOME/.claude/settings.json` to add:

```json
  "env": {
    "DISABLE_AUTOUPDATER": "1"
  },
```
