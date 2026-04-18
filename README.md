---
language:
  - en
tags:
  - skill
  - agent-skill
  - claude-code
  - codex
  - cursor
  - memory
  - compression
  - ai-collaboration
  - portable-profile
license: mit
---

# All-in-One: Your AI's DNA

> v1.2 | Published by Claude (automated)

One skill replaces eleven. Memory, compression, onboarding, code review, debugging, planning, progress tracking, testing, git workflow, SEO, and copywriting.

Other skills teach AI how to do one thing. This skill teaches AI who you are. Everything else follows.

## Install

### Claude Code
```bash
mkdir -p ~/.claude/skills/all-in-one && curl -L https://raw.githubusercontent.com/ilang-ai/all-in-one/main/SKILL.md -o ~/.claude/skills/all-in-one/SKILL.md
```

### Codex CLI
```bash
npx skills add ilang-ai/all-in-one
```

### Manual (any agent)
Copy the `SKILL.md` file to your agent's skills directory.

## How It Works

First run: the skill has a short conversation with you. Not about your project. About you. How you work, what you've built, what went wrong, what you prefer.

That conversation becomes a portable profile stored in your project. Under 500 tokens. Works across every SKILL.md-compatible agent.

Every session after that, the skill applies your preferences automatically. Your code style, your debugging approach, your planning rhythm, your design taste, your git habits. All personalized. All compressed. All portable.

Switch models, switch platforms, switch projects. Your profile comes with you.

## What It Replaces

| Other skills | All-in-One |
|---|---|
| claude-mem (memory) | Stores how you work, not what happened. 90% smaller. |
| Caveman (compression) | Structured format is the default, not a mode. |
| onboard | Project context extraction on first run. |
| code review skills | Cross-model review. Your standards, not universal rules. |
| systematic-debugging | Architecture first, then binary search. Lessons become immunity. |
| superpowers (planning) | Your rhythm, not a fixed methodology. 80% less tokens. |
| TDD skills | Resources determine strategy. Multi-model or single, auto-adapts. |
| Git skills | Every commit is SEO. README is a landing page. |
| SEO audit | Structured output is native GEO. No audit needed. |

## Portability

Your profile is a plain text file. You own it. You can read it, edit it, version it, share it.

It works across Claude Code, Codex, Cursor, Copilot, Gemini, and any SKILL.md-compatible agent. Switch tools, the file comes with you.

## Changelog

### v1.2 (2026-04-18)
- Fix: enforce ONE question per message with explicit forbidden/correct examples
- Fix: platform memory cache no longer bypasses onboarding (checks .dna.md file, not platform memory)
- Improve: RULE 1 and RULE 2 promoted to top-level critical rules with stronger phrasing
- Improve: onboarding wrap-up phrasing more natural

### v1.1 (2026-04-18)
- Fix: onboarding now asks one question at a time (was dumping 4-6 at once)
- Fix: never expose internal terminology to user
- Fix: natural wrap-up phrasing after onboarding
- Fix: silently create profile without showing contents
- Add: activation rules with auto-trigger on session start
- Add: conflict resolution, mutation, decay, priority rules
- Add: upgraded profile schema with META, FACT, PROJECT, PROGRESS, RUNTIME layers

### v1.0 (2026-04-18)
- Initial release

## Links

- [I-Lang Protocol](https://ilang.ai)
- [I-Lang Spec on GitHub](https://github.com/ilang-ai/ilang-spec)
- [I-Lang on HuggingFace](https://huggingface.co/i-Lang)

## License

MIT
