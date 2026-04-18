---
language:
  - en
tags:
  - skill
  - agent-skill
  - imprint
  - claude-code
  - codex
  - cursor
  - copilot
  - gemini
  - windsurf
  - memory
  - compression
  - ai-collaboration
  - portable-profile
license: mit
---

<div align="center">

<img src="https://raw.githubusercontent.com/ilang-ai/Imprint/main/imprint-banner.png" alt="Imprint, your working imprint, portable across every agent." width="100%"/>

# Imprint

### *Your working imprint, portable across every agent.*

[![License](https://img.shields.io/badge/License-MIT-1e3a8a?style=for-the-badge)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.4-d4a858?style=for-the-badge)](#changelog)
[![Skill Standard](https://img.shields.io/badge/SKILL.md-compatible-0b0f1a?style=for-the-badge&labelColor=d4a858)](https://github.com/ilang-ai/Imprint)
[![Agents](https://img.shields.io/badge/19%20agents-supported-0b0f1a?style=for-the-badge)](https://github.com/ilang-ai/Imprint#compatibility)

</div>

---

> **Imprint**, *verb.* To stamp a mark that cannot be erased.
> *noun.* The mark itself, permanent, portable, unmistakably yours.
>
> In ethology, *imprinting* is the moment a young animal learns, once and
> forever, who it belongs to. In printing, an *imprint* is the publisher's
> signature pressed into every page. In both meanings, something is **marked
> at its core**, and that mark travels with it.
>
> This project is that mark, for human-AI work.

---

## What this is

**Imprint** is a single plugin that captures **how *you* work** and
carries it across every AI agent you use.

On first run, the skill has a short conversation with you. **Not about your
project, about you.** How you debug, how you plan, how you write commits,
what you've shipped, what went wrong, what you prefer.

That conversation becomes a **portable profile**, a working imprint, stored
alongside your code. Under 500 tokens. Structured. Readable. Yours.

Every session after that, the skill applies your imprint automatically:
your code style, your review standards, your planning rhythm, your design
taste, your git habits. Across 19 agents. Across every project.

**Switch models. Switch platforms. Switch teams. Your imprint comes with you.**

---

## Install

### Claude Code (recommended)

```
/plugin marketplace add ilang-ai/Imprint
/plugin install imprint@ilang-plugins
```

### Codex CLI

```bash
npx skills add ilang-ai/Imprint
```

### Cursor

```
/add-plugin ilang-ai/Imprint
```

### Gemini CLI

```bash
gemini extensions install https://github.com/ilang-ai/Imprint
```

### Manual test

```bash
git clone https://github.com/ilang-ai/Imprint.git
claude --plugin-dir ./Imprint
```

### Any SKILL.md-compatible agent

Copy `skills/imprint/SKILL.md` into your agent's skills directory.

---

## What It Replaces

One file. Eleven capabilities. Zero dependencies.

| You used to install...        | Imprint does it by                                                            |
| :--------------------------- | :--------------------------------------------------------------------------- |
| `claude-mem` (memory)        | Stores **how you work**, not what happened. ~90% smaller.                    |
| `Caveman` (compression)      | Structured format is the default, not a mode.                                |
| `onboard`                    | Project context extraction on first run.                                     |
| Code-review skills           | Review against **your** standards, not universal rules.                      |
| `systematic-debugging`       | Architecture first, then binary search. Lessons become immunity.             |
| `superpowers` (planning)     | Your rhythm, not a fixed methodology. ~80% fewer tokens.                     |
| Progress-tracking skills     | Auto-checkpoint on meaningful state changes.                                 |
| TDD skills                   | Resources decide strategy, multi-model or single, auto-adapts.               |
| Git-workflow skills          | Every commit is SEO. README is a landing page.                               |
| `seo-audit`                  | Structured output is native GEO. No audit needed.                            |
| Copywriting skills           | Tone, terminology, and rhythm derived from your imprint.                     |

**11 skills → 1 imprint → every agent.**

---

## Compatibility

<div align="center">

| Agent           | Status | Install                    |
| :-------------- | :----: | :------------------------- |
| **Claude Code** | ✅     | `/plugin marketplace add`  |
| **Codex CLI**   | ✅     | `npx skills add`           |
| **Cursor**      | ✅     | `/add-plugin` or skills dir|
| **Copilot**     | ✅     | drop in skills dir         |
| **Gemini**      | ✅     | drop in skills dir         |
| **Windsurf**    | ✅     | drop in skills dir         |
| **Trae**        | ✅     | drop in skills dir         |
| **Cline**       | ✅     | drop in skills dir         |
| **Roo**         | ✅     | drop in skills dir         |
| *+ 10 more*     | ✅     | SKILL.md standard          |

</div>

Any agent that speaks the SKILL.md standard works. **19 agents** today,
more as the standard spreads.

---

## Your imprint is yours

The imprint is a **plain text file** sitting next to your code. You own it.

- **Read** it, no black box, no vendor cache
- **Edit** it, nudge a preference, commit the change
- **Version** it, it's just git
- **Share** it, hand it to a teammate, they inherit your working style
- **Port** it, every SKILL.md agent speaks the same file

Switch tools, the imprint comes with you. No lock-in. Ever.

---

## Schema at a glance

```text
META        imprint version, identity hash, last-updated
FACT        immutable preferences (code style, license, naming)
PROJECT     current project shape, stack, constraints
PROGRESS    checkpoints, decisions, lessons
RUNTIME     per-session volatile state
```

Five layers. One file. Under 500 tokens.

---

## Changelog

### v1.4 (2026-04-18)
- **Rebrand** from all-in-one to Imprint
- **Add** Imprint design assets: banner, logo, social preview
- **Add** `.cursor-plugin/` for Cursor Marketplace compatibility
- **Add** `.claude-plugin/marketplace.json` for self-distribution
- **Submit** to Claude Code official marketplace and Cursor Marketplace

### v1.3 (2026-04-18)
- **Add** plugin manifest (`.claude-plugin/plugin.json`) for official marketplace
- **Move** SKILL.md to `skills/imprint/SKILL.md` per plugin spec
- **Update** install instructions for plugin format

### v1.2 (2026-04-18)
- **Fix** enforce *one question per message* with explicit forbidden/correct examples
- **Fix** platform memory cache no longer bypasses onboarding
- **Improve** Rule 1 and Rule 2 promoted to top-level critical rules
- **Improve** onboarding wrap-up phrasing more natural

### v1.1 (2026-04-18)
- **Fix** onboarding now asks one question at a time (was dumping 4-6 at once)
- **Fix** never expose internal terminology to user
- **Add** activation rules with auto-trigger on session start
- **Add** conflict resolution, mutation, decay, priority rules
- **Add** upgraded schema with META / FACT / PROJECT / PROGRESS / RUNTIME layers

### v1.0 (2026-04-18)
- Initial release

---

## Contributing

Issues and PRs welcome. Keep the imprint under 500 tokens and the file
human-readable, those are the two hard constraints.

---

## Links

- [ilang.ai](https://ilang.ai)
- [GitHub](https://github.com/ilang-ai/Imprint)
- [Hugging Face](https://huggingface.co/i-Lang)
- [SKILL.md spec](https://github.com/ilang-ai/ilang-spec)

---

## License

MIT License. 2026 Eastsoft Inc. / Palm Media Technology / Canada.

---

<div align="center">

**Powered by the [I-Lang Protocol](https://ilang.ai)**, an open standard for human-AI communication.

*Published by Claude (automated) / Free forever*

</div>
