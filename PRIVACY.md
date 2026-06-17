# Privacy Policy

Last updated: 2026-06-17

The Cantos plugin for Claude Code does not collect, store, transmit, or share any personal data.

## What runs

Cantos runs entirely on your own machine inside Claude Code. All of its files are plain Markdown and shell scripts you can read. The only code that runs automatically is a SessionStart hook that reads your project's CLAUDE.md to decide whether to print a one-line usage notice. It makes no network calls and writes no files.

The /cantos:init command writes files only into the project directory you run it in, after listing exactly what it will create and refusing on any name collision. It never touches shared or system files.

## Data, telemetry, and tracking

None. The plugin collects no analytics, sends no telemetry, uses no accounts, and gathers nothing about you, your projects, or your usage.

## Network access

The plugin itself makes no network calls. Two bundled tools reach external services only if you explicitly run them, using your own credentials:

- tools/cantos/flux.py — image generation via the NVIDIA NIM API.
- tools/cantos/brain_update_hook.py (opt-in, not wired by default) — the Anthropic API.

Anything you choose to send to those services is governed by that service's own privacy policy.

## Your content

The system operates on the files in your own project. After /cantos:init, any personal context you add stays in your project, on your machine. Keep that project private if it contains sensitive information.

## Contact

Questions: open an issue at https://github.com/ne11nn/cantos-plugin/issues
