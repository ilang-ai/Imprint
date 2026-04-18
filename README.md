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
[![Version](https://img.shields.io/badge/version-2.0-d4a858?style=for-the-badge)](#changelog)
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
taste, your git habits. Portable across any SKILL.md-compatible agent.

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

### VS Code / VS Code forks

Search "Imprint" in the Extensions panel, or:

- [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ILang.imprint)
- [Open VSX](https://open-vsx.org/extension/ILang/imprint)

### Manual test

```bash
git clone https://github.com/ilang-ai/Imprint.git
claude --plugin-dir ./Imprint
```

### Any SKILL.md-compatible agent

Copy `skills/imprint/SKILL.md` into your agent's skills directory.

---

## What It Overlaps With

Imprint covers ground that these skills address individually. Not a drop-in replacement for all of them, but a single file that handles the common cases.

| Instead of installing...      | Imprint covers this by                                                       |
| :--------------------------- | :--------------------------------------------------------------------------- |
| `claude-mem` (memory)        | Stores **how you work**, not what happened. ~90% smaller.                    |
| `Caveman` (compression)      | Structured format is the default, not a mode.                                |
| `onboard`                    | Project context extraction on first run.                                     |
| Code-review skills           | Review against **your** standards, not universal rules.                      |
| `systematic-debugging`       | Architecture first, then binary search. Lessons become immunity.             |
| `superpowers` (planning)     | Your rhythm, not a fixed methodology.                                        |
| Progress-tracking skills     | Auto-checkpoint on meaningful state changes.                                 |
| TDD skills                   | Resources decide strategy, multi-model or single, auto-adapts.               |
| Git-workflow skills          | Searchable commits, README as landing page when discoverability is on.       |
| `seo-audit`                  | Structured output is more parseable by AI search engines.                    |
| Copywriting skills           | Tone, terminology, and rhythm derived from your imprint.                     |

**One file. Eleven capability areas. Depth varies by area.**

---

## Compatibility

<div align="center">

| Agent           | Support    | Install                    |
| :-------------- | :--------: | :------------------------- |
| **Claude Code** | native     | `/plugin marketplace add`  |
| **Codex CLI**   | native     | `npx skills add`           |
| **Cursor**      | native     | `/add-plugin` or skills dir|
| **Gemini CLI**  | native     | `gemini extensions install`|
| **VS Code**     | extension  | VS Code Marketplace        |
| **Copilot**     | SKILL.md   | drop in skills dir         |
| **Windsurf**    | SKILL.md   | drop in skills dir         |
| **Trae**        | SKILL.md   | drop in skills dir         |
| **Cline**       | SKILL.md   | drop in skills dir         |
| **Roo**         | SKILL.md   | drop in skills dir         |

</div>

**native** = dedicated plugin/extension manifest. **SKILL.md** = compatible via the open Agent Skills standard. Any agent that reads SKILL.md files can load Imprint.

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
META        schema version, timestamps, session count
CORE        global behavioral genes with confidence and scope
  GENE      traits (T:) and anti-patterns (A:), conditional via when:
FACT        verifiable environment data (stack, deploy target, model access)
PROJECT     repo-specific overrides, stack, constraints, mismatches
LESSONS     cross-project traps, accumulated from real experience
PROGRESS    milestone-only checkpoints, auto-summarized every 10 entries
RUNTIME     current mode settings (transparency, speed, compression)
DECAY       lifecycle rules for tentative genes and inactive projects
```

Core imprint stays under 500 tokens. Project and progress layers can grow.

---

## Example: real .dna.md

This is what an actual profile looks like after a few sessions:

```
::DNA{user}
::META{schema:2.0|updated:2026-04-18|sessions:5}

::CORE{
  ::CONTEXT{role:fullstack_dev|experience:4yr|model_access:2|discoverability:yes}

  ::GENE{style|conf:confirmed|scope:global}
    T:conclusions_first
    T:minimal_output|when:task_simple
    T:full_detail|when:task_complex
    A:verbose_without_signal⇒waste

  ::GENE{planning|conf:confirmed|scope:global}
    T:build_first_plan_later
    A:monolithic_spec⇒reject

  ::GENE{debug|conf:4/5|scope:global}
    T:check_architecture_before_code
    A:guess_from_error_message⇒wrong_direction
}

::FACT{
  ::ITEM{key:preferred_stack|value:react,node|conf:confirmed}
  ::ITEM{key:models_used|value:claude,gpt|conf:confirmed}
}

::PROJECT{repo:my-saas}
  ::STACK{frontend:next.js|backend:node|db:postgres}
  ::CONSTRAINT{auth:clerk|deploy:vercel}
}

::LESSONS{
  ::LESSON{id:middleware_order_matters|type:debug|scope:project|conf:confirmed}
  ::LESSON{id:always_check_env_vars_first|type:deploy|scope:cross_project|conf:3/5}
}

::PROGRESS{
  ::ITEM{date:2026-04-18|done:auth_flow|learned:clerk_webhook_needs_raw_body|next:stripe_integration}
}

::RUNTIME{transparency:quiet|speed:balanced|compression:structured_default}
::DECAY{tentative_unseen_30d=>remove|repeated_3x=>confirm|progress_10_items=>summarize}
::END{DNA}
```

312 tokens. Carries code style, debugging approach, project context, lessons, and progress across every session and every agent.

---

## Changelog

### v2.0 (2026-04-18)
- **Schema 2.0**: CORE/PROJECT layered separation. Global genes no longer mix with project overrides.
- **Conditional genes**: `T:minimal|when:simple` + `T:full_detail|when:complex`. Context-dependent behavior.
- **Five conflict types**: user vs history, global vs project, two confirmed contradicting, multi-agent disagreement, lesson vs task. Each with explicit resolution.
- **Progress compression**: auto-summarize every 10 entries, keep file lean.
- **User transparency**: quiet/explain/audit three modes, natural switching.
- **Reflexion reframed**: part of the thinking process, not an extra API call. Zero visible latency.
- **Context drift protection**: re-read profile before major decisions in long sessions.
- **Team override**: project linter and team style rules always override personal genes.
- **Speed mode**: `RUNTIME{speed:fast}` skips reflexion for latency-sensitive work.
- **Version sync**: all manifests aligned to 2.0.0.

### v1.5 (2026-04-18)
- **Add** reflexion loop for single-model code review: AI self-critiques and fixes its own output before presenting to user
- **Improve** code review no longer uses a static checklist, now runs an active self-correction cycle checking against user's profile and lessons

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
- [skills.sh](https://skills.sh/ilang-ai/Imprint/imprint)
- [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ILang.imprint)
- [Open VSX](https://open-vsx.org/extension/ILang/imprint)
- [Hugging Face](https://huggingface.co/i-Lang/Imprint)
- [SKILL.md spec](https://github.com/ilang-ai/ilang-spec)

---

## License

MIT License. 2026 Eastsoft Inc. / Palm Media Technology / Canada.

---

<div align="center">

**Powered by the [I-Lang Protocol](https://ilang.ai)**, an open standard for human-AI communication.

*Published by Claude (automated)*

</div>
