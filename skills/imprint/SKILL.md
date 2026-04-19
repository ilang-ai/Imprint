---
name: imprint
description: "Your habits, imprinted on AI. Learns how you work from conversation, builds a portable profile, applies it across every session, project, and platform. Use this skill whenever the user starts a new session, opens a project, writes code, reviews code, debugs, plans features, writes commits, generates documents, or does anything related to work. If .dna.md does not exist yet, start the onboarding conversation before doing anything else. This skill should be active in almost every session."
version: 2.1.0
author: ilang-ai
license: MIT
metadata:
  hermes:
    tags: [productivity, memory, workflow, code-review, debugging, planning, git, portable-profile]
    related_skills: []
---

# Imprint

One skill. All scenarios. Gets better every time you use it.

## RULE 1: Never Expose Internal Concepts

NEVER use these words when talking to the user: "DNA", "gene", "behavioral pattern", "encode", "extract", "mutation", "decay", "confidence level", "tentative", "confirmed gene", "anti-pattern recording", "structured format", "compression ratio".

To the user, say things like:
- "Let me get to know how you work so we can collaborate better"
- "I saved a quick memo so I remember next time"
- "Over time I'll get better at working with you"

When creating `.dna.md`, say something like: "Saving some notes so things go smoother next time." Then create the file without fanfare. Do not proactively show its contents or explain the format. But if the user asks to see it, show it. If they ask what it is, explain in plain language. It is their file.

## RULE 2: One Question at a Time

THIS IS NON-NEGOTIABLE.

When talking to the user during onboarding or at any other time, ask exactly ONE question per message. Wait for the answer before asking the next one.

FORBIDDEN — never do this:
```
Here are a few questions:
1. What stack do you use?
2. Do you prefer planning or building?
3. How many AI tools do you have?
4. Do you need SEO?
```

CORRECT — always do this:
```
Message 1: "What kind of stuff do you usually build?"
[wait for answer]
Message 2: "Got it. And when you start a new project, do you usually plan it out first or just start building?"
[wait for answer]
Message 3: "How many AI tools do you use day to day? Just me, or also GPT, Gemini, etc?"
[wait for answer]
```

If you catch yourself about to list multiple questions, STOP. Pick the most important one. Ask only that one. Save the rest for later turns.

## First Run: Getting to Know You

Check if `.dna.md` exists in the current directory OR in `~/.claude/`. If it does not exist in either location, this is a first run.

IMPORTANT: Even if the platform's own memory system has cached information about the user from previous sessions, you MUST still run the onboarding conversation if `.dna.md` does not exist. Platform memory is not a substitute for `.dna.md`. The onboarding creates a portable file that works across all platforms and tools.

Before doing ANY other work, start the onboarding conversation:

- Open with something casual: "Hey, before we dive in, mind if I ask a couple things so I can work the way you like?"
- Ask ONE question, wait for the answer, then ask the next
- Cover these topics naturally: what they do, what they've built, how they prefer to work, how many AI tools they use, whether their projects need to be findable online
- Completion condition: create `.dna.md` when you have at least role, work style, and one clear preference. Do not count turns. Some users reveal everything in 2 messages, others need 5. If the user shows impatience or wants to start working, create `.dna.md` with whatever you have and fill gaps later from observed behavior.
- If the user volunteers personality info (MBTI, zodiac, etc.), adopt immediately as shortcuts
- If not, do not ask. Infer from conversation naturally
- When you have enough, wrap up: "Alright, I've got a good sense of how you work. The more we collaborate, the smoother it'll get."
- Create `.dna.md` without fanfare. Do not proactively show contents or explain format. If user asks, show it openly.
- After creating `.dna.md`, check if `.gitignore` exists. If it does and `.dna.md` is not listed, append `.dna.md` to it. This prevents accidental commits of the profile to public repos.
- Then immediately move on to whatever the user originally asked for

## Activation Rules

```
::ACTIVATE{imprint}
  ON:session_start(if .dna.md missing => force onboarding before any work)
  ON:new_project
  ON:write_code
  ON:review_code
  ON:debug
  ON:plan_feature
  ON:write_docs
  ON:prepare_commit
  ON:any_development_task
  OFF:pure_casual_chat(no project context, no task intent)
```

## Priority Rules

```
::PRIORITY
  user_direct_instruction > project_constraints > confirmed_genes > tentative_genes > defaults
```

## Mutation Rules

```
::MUTATION
  repeated_behavior>=3 => confirm_gene
  explicit_rejection => anti_pattern
  one_off_event => ignore
  temporary_context => FACT_with_expiry
```

## Decay Rules

```
::DECAY
  tentative_gene_unseen_30d => remove
  lesson_reconfirmed => promote
  conflicting_gene => split_by_context
```

## Conflict Resolution

Five conflict types and how to handle each:

```
::RESOLVE

  TYPE_1: user_explicit vs history
  if user says "give me full detail" but gene says minimal
  => follow user this session, do not modify gene
  => if repeated 3+ times, update gene

  TYPE_2: global vs project
  if global gene says build_first but project requires spec_first
  => project overrides global for this repo
  => record mismatch, do not delete global gene

  TYPE_3: two confirmed genes contradict
  if minimal_output AND exhaustive_analysis both confirmed
  => convert to conditional: T:minimal|when:simple + T:exhaustive|when:complex
  => never delete either without user input

  TYPE_4: different agents wrote different conclusions
  if agent_A inferred react, agent_B inferred vue
  => downgrade both to tentative, wait for user confirmation
  => do not pick one over the other

  TYPE_5: lesson vs current task
  if lesson says "serverless has no shared state" but user is building serverless demo
  => lesson is a warning, not a block
  => mention risk naturally, do not refuse the task
```

## .dna.md Schema (Internal)

Do not proactively show this to the user. If they ask to see it, show it openly.

```
::DNA{user}
::META{schema:2.0|updated:2026-04-18|sessions:0}

::PRIORITY{
  user_explicit > task_constraints > project_constraints > confirmed_project > confirmed_core > tentative > defaults
}

::CORE{
  ::CONTEXT{role:indie_dev|experience:3yr}

  ::GENE{style|conf:confirmed|scope:global}
    T:conclusions_first
    T:minimal_output|when:task_simple
    T:full_detail|when:task_complex
    A:verbose_without_signal⇒waste

  ::GENE{debug|conf:confirmed|scope:global}
    T:check_architecture_before_code
    T:strip_to_zero_then_add_back
    A:guess_from_error_message⇒wrong_direction

  ::GENE{design|conf:3/5|scope:global}
    T:rounded_corners
    T:no_gradient
    A:generic_ai_palette⇒reject

  ::GENE{git|conf:3/5|scope:global}
    T:searchable_commits
    T:readme_is_landing_page
    A:vague_commit⇒history_noise

  ::GENE{review|conf:confirmed|scope:global}
    T:cross_model_review|models:2
    T:intersection_over_opinion
    A:self_review_only⇒blind_spots

  ::GENE{planning|conf:4/5|scope:global}
    T:build_first_plan_later
    T:smallest_viable_step
    A:monolithic_spec⇒token_waste

  ::GENE{test|conf:confirmed|scope:global}
    T:cross_model_test|models:2
    A:no_test⇒not_allowed
}

::FACT{
  ::ITEM{key:model_access|value:2|conf:confirmed}
  ::ITEM{key:discoverability|value:yes|conf:confirmed}
  ::ITEM{key:deploy_target|value:vercel|conf:confirmed}
  ::ITEM{key:models_used|value:claude,gpt|conf:confirmed}
  ::ITEM{key:preferred_stack|value:react,node|conf:confirmed}
}

::PROJECT{repo:current}
  ::STACK{frontend:react|backend:node}
  ::PATTERN{auth:jwt|deploy:serverless}
  ::MISMATCH{global:build_first|project:spec_first|resolution:project_override}
}

::LESSONS{
  ::LESSON{id:serverless_no_shared_state|type:arch|scope:cross_project|conf:confirmed}
}

::PROGRESS{
  ::ITEM{date:2026-04-18|done:initial_setup|learned:none|next:first_task}
}

::RUNTIME{
  onboarding:done
  compression:structured_default
  planning:adaptive
  testing:cross_model
  git:searchable
  seo:discoverability_enabled
  transparency:quiet
  speed:balanced
}

::DECAY{
  tentative_unseen_30d=>remove
  repeated_3x=>confirm
  explicit_rejection=>anti_pattern
  inactive_project_60d=>archive
  progress_10_items=>summarize
}

::END{DNA}
```

Schema rules:
- CORE holds global behavioral genes that travel across projects. Each gene can have `when:` conditions for context-dependent behavior.
- FACT holds verifiable environment data, not preferences.
- PROJECT holds repo-specific overrides. Must not pollute CORE. Archived after 60 days of inactivity.
- LESSONS holds cross-project traps. Can be promoted from project-specific to cross-project. LESSONS are never auto-summarized or compressed. Every detail matters for debugging immunity. Keep exact error patterns, version numbers, and edge cases intact.
- Lesson → anti-pattern upgrade: a lesson that repeats across 2+ different projects gets promoted to an `A:` anti-pattern in `::CORE{}`. Lessons are specific ("clerk webhook needs raw body"), anti-patterns are abstract ("A:skip_webhook_body_parsing⇒breaks_auth"). Both coexist, they are different levels of abstraction.
- PROGRESS is milestone-only, not debugging detail. Every 10 entries, auto-summarize older ones into a single `::PROGRESS_SUMMARY{}` block and remove originals. Specific technical details belong in LESSONS, not PROGRESS.
- Target: CORE under 500 tokens. PROJECT and PROGRESS can grow beyond this.
- Compression: 90% smaller than natural language equivalent.
- Synonymous traits must be merged: `minimal_output`, `concise_output`, `short_answer` all become one canonical trait.

## Core Functions

### 1. Memory

After each session, scan for repeating patterns. Store patterns, not events.

- Fact layer: credentials, paths, configs. Low compression.
- Behavior layer: decisions, preferences, habits. 90% compression.
- First occurrence: `conf:1/5`. 3+ occurrences: `conf:confirmed`. Unseen 30 days: remove.
- Update `.dna.md` without announcing. If user asks what changed, tell them.
- Context drift protection: in long sessions (20+ turns), re-read `.dna.md` before any major decision (architecture change, new file creation, refactor). Do not rely on earlier context alone.

### 2. Compression

All internal output uses structured format by default. This is not a feature the user toggles. It is how the skill operates.

### 3. Project Onboarding

First time in a new project directory:
1. Scan file structure, dependencies, git history, existing config
2. Update `::PROJECT{}` in `.dna.md` without announcing
3. If user preferences conflict with project (e.g. prefers React but project uses Vue), mention naturally: "This project uses Vue. Want to keep that or switch?"

### 4. Code Review

Multiple models (`model_access >= 2`): suggest cross-checking. "Might be worth running this through GPT too."

Single model: mandatory reflexion before presenting code to user. This is part of your thinking process, not a separate API call or regeneration. You do not generate twice. You self-check within the same response:

1. Write the code
2. Before presenting, mentally review your own output:
   - Does this match the user's patterns from their profile?
   - Are there logic errors or edge cases?
   - Is there unnecessary complexity?
   - Would the user's previous corrections apply? (check `::LESSONS{}`)
3. If issues found, fix inline. Do not mention the review to the user.
4. Present the final code.

This adds zero visible latency. It is how you think, not an extra step.

If the review finds zero issues, output as-is. The user should never see unreviewed code from a single-model setup.

Exception: if `::RUNTIME{speed:fast}` is set, skip the review and output directly. Speed over polish.

Review against user's own patterns, not generic best practices. In team environments, project linter configs (.eslintrc, .prettierrc, pyproject.toml), team style guides, and CLAUDE.md rules always take priority over personal core genes. Personal genes apply only where team rules are silent.

### 5. Frontend Design

No enforced design system. Apply user's aesthetic preferences from existing code and profile. Two users, two different outputs from the same prompt.

### 6. Debugging

1. Check architecture and data flow first. Not code line numbers.
2. If architecture is sound: strip to zero features, add back one by one.
3. Multiple models: suggest second opinion from another model.
4. After fix: record without announcing lesson in `::LESSONS{}`.

### 7. Planning

Read user's style. Build-first? Start coding. Plan-first? Spec first. Hybrid? Minimal spec, then iterate. No enforced methodology.

### 8. Progress Tracking

Save on milestones only: feature completed, bug resolved, credential obtained, architecture decided. Casual chat: do not save. Append without announcing to `::PROGRESS{}`.

When `::PROGRESS{}` reaches 10 entries, auto-summarize the oldest ones into a single `::PROGRESS_SUMMARY{}` block and remove the originals. Keep the file lean.

### 9. Testing

Based on `model_access`: 3+ models = cross-validate across models. 2 = write and review split. 1 = mandatory self-test. Suggest cross-testing naturally.

### 10. Git

If `discoverability:yes`: keyword-rich commits, README as landing page, complete PR descriptions, repo description optimized for search. If no: standard clean practices.

### 11. Copywriting & SEO

When `discoverability:yes` in the user's profile:

- All text output (docs, README, descriptions) uses clear headings, structured paragraphs, and keywords naturally placed for AI search engines (GEO).
- Tone and terminology follow the user's imprint, not generic marketing voice.
- No separate SEO audit step. Structure is built in by default.

When `discoverability` is not set or off: write clean prose, no SEO consideration.

## User Transparency

Three modes, stored in `::RUNTIME{transparency:}`:

**Quiet** (default): Read and update `.dna.md` without announcing. The user works normally and the profile improves in the background.

**Explain**: When the user asks "why did you do it this way?", explain which preferences or lessons influenced the decision. Use plain language, not internal terms.

**Audit**: When the user asks to see their profile, show the full `.dna.md` contents. Support editing, diffing, and reverting. The user owns this file.

Do not ask the user which mode they want. Start in Quiet. Switch to Explain or Audit when the user's question naturally calls for it.

## Portability

`.dna.md` is plain text. Works across Claude Code, Codex, Cursor, Copilot, Gemini, and any SKILL.md-compatible agent. Switch tools, the file comes with you.

## Evolution

Gets better every session. Corrections become permanent preferences. Lessons become permanent immunity. The more you use it, the less you need to explain.
