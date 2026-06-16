# cantos (plugin)

**The entire [Cantos](https://github.com/ne11nn/cantos) system as a one-command Claude Code plugin.** Cantos is a self-improving, multi-agent personal-assistant operating system: an orchestrator that delegates each request to a specialist assistant, backed by a library of skills and sub-agents. Everything is plain, editable markdown. Nothing is a black box.

This is the *installable* form of Cantos. (You can also clone the full template at [ne11nn/cantos](https://github.com/ne11nn/cantos).)

## Install

```
/plugin marketplace add ne11nn/cantos-plugin
/plugin install cantos@cantos-plugin
```

That's it. The plugin's skills and the `browser-agent` are now available in every session, and a SessionStart notice tells you how to bring up the full system.

## Two ways to run the system

| Command | What it does | When |
| --- | --- | --- |
| `/cantos:init` | Scaffolds the **entire writable system** into your current project as real, git-tracked files (CLAUDE.md, the assistants, workflows, references, the self-improvement spine), then runs a short setup interview to personalize it. | The real install. Run once per project. This is the only mode where the system **persists and evolves** — `/wrap` and brain-file updates stick on disk, and every future session in that directory starts as Cantos automatically. |
| `/cantos:start` | Adopts the Cantos orchestrator for the **current session only**, reading the bundled system in place. Writes nothing. | A quick try, or a one-off you don't want to scaffold. |

## What "self-improving" means

Cantos is built to sharpen over time instead of decaying. Every session can fold what it learned back into its own instructions: `/wrap` reviews the conversation and updates the relevant brain file, workflow, or the registry, routed through a three-question test that keeps the instructions short instead of letting rules pile up. That loop only persists when the files are real on disk, which is why `/cantos:init` (not the ephemeral `/cantos:start`) is the way to actually live in the system.

## What's bundled

- **The orchestrator + specialist assistants** (research and writing, admin via MCP, engineering) and their sub-agents, under `system/`.
- **Skills**, surfaced in every session: design and UI, motion, frontend engineering, codebase architecture, research, and writing-craft. A few system-coupled skills (`wrap`, `name-session`, `write-like-me`, `ai-detect`, `impeccable`) are not exposed as standalone plugin skills because they need the scaffolded system to work; they ship inside `system/` and activate after `/cantos:init`.
- **The `browser-agent`** for general browser automation (pair with the `playwright-cli` skill).

## Privacy

After `/cantos:init`, the scaffolded system holds your personal context (`context/me.md`, `context/work.md`) and, if you use the voice features, your writing samples. Keep that project in a **private** repo. The plugin itself ships no personal data.

## License

MIT for the original work. Several bundled skills are vendored from third parties and retain their own licenses; some have unverified provenance and are **not** covered by this repo's MIT grant. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and verify before redistribution or commercial reuse.
