# AI Music Prompt Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create the first working `SKILL.md` for the interactive AI music prompt skill, aligned with the approved design spec and existing music-library documents.

**Architecture:** The implementation will stay minimal. It will create one top-level `SKILL.md` that acts as a router and workflow controller, while keeping detailed knowledge in the existing library Markdown files. The document will encode six modes, a short interview flow, library-loading rules, language rules, safety rules, and output rules without duplicating full library content.

**Tech Stack:** Markdown, YAML frontmatter, existing project documentation

---

All paths below are relative to the skill root directory unless noted otherwise.
以下路径默认相对于 skill 根目录，除非另有说明。

## File Structure / 文件结构

### Files to create or modify
- Create: `SKILL.md`
- Reference: `docs/superpowers/specs/2026-06-06-ai-music-prompt-skill-design.md`
- Reference: `ai_music_customer_interaction_workflow_v0.1_bilingual.md`
- Reference: `ai_music_library_orchestration_rules_v0.1_bilingual.md`
- Reference: `ai_music_prompt_templates_v0.1_bilingual.md`

The plan is intentionally narrow: write only `SKILL.md` first. README, examples, and checklists can follow in later tasks.

### Task 1: Draft skill metadata and top-level contract

**Files:**
- Create: `SKILL.md`
- Reference: `docs/superpowers/specs/2026-06-06-ai-music-prompt-skill-design.md`

- [ ] **Step 1: Write the YAML frontmatter and top-level positioning**

Use this initial structure:

```md
---
name: interactive-ai-music-prompt-skill
description: Use this skill whenever the user wants to create a song prompt, BGM prompt, Suno prompt, Udio prompt, optimize existing music prompts or lyrics, compare multiple music directions, or generate a short-video hook. This skill acts like an AI music creation consultant: it asks a few high-value questions, builds a structured music brief, and outputs copy-ready prompt packages for AI music generation tools.
---

# Interactive AI Music Prompt Skill

## What this skill does

## Core identity

## What this skill is not
```

- [ ] **Step 2: Verify metadata matches the approved spec**

Check these items manually against `docs/superpowers/specs/2026-06-06-ai-music-prompt-skill-design.md`:
- six modes are in scope
- consultant framing is present
- no extra speculative features were added

Expected result: the top section states one skill, six modes, and a consultant-style workflow.

- [ ] **Step 3: Commit the initial draft skeleton**

```bash
git add SKILL.md
git commit -m "docs: add AI music skill skeleton"
```

If the repo is not ready for commits yet, skip the commit and note it explicitly in the execution log.

### Task 2: Add mode routing and questioning workflow

**Files:**
- Modify: `SKILL.md`
- Reference: `ai_music_customer_interaction_workflow_v0.1_bilingual.md`

- [ ] **Step 1: Write the mode-routing section**

Add a section that defines these modes exactly:

```md
## Mode routing

Route into one of these modes:
1. `create_vocal_song`
2. `create_instrumental_bgm`
3. `optimize_existing_prompt`
4. `optimize_existing_lyrics`
5. `generate_multi_versions`
6. `generate_short_video_hook`
```

Below that, add one short rule block per mode describing when it should trigger.

- [ ] **Step 2: Write the questioning strategy section**

Add a section like this:

```md
## Questioning strategy

Default to a short interview, not a long questionnaire.

- First, check whether the user already provided enough information.
- If not, ask up to 3 core questions.
- Only ask 2–3 follow-up questions when missing details would materially weaken the result.
- Stop asking and generate as soon as the brief is good enough.
```

Also include the three default first-round question targets:
- track type
- theme plus use case
- style plus mood

- [ ] **Step 3: Add expert-user fast path rules**

Add a short section stating:

```md
## Fast path for experienced users

If the user already specifies the key fields needed for generation, skip the interview and move directly to a brief summary plus output generation.
```

- [ ] **Step 4: Save and review for duplication**

Manual check:
- confirm the workflow references the customer interaction library instead of copying its full contents
- confirm the wording stays shorter than the underlying library file

Expected result: `SKILL.md` stays controller-like rather than becoming another giant reference file.

### Task 3: Add brief-building, library loading, and output rules

**Files:**
- Modify: `SKILL.md`
- Reference: `ai_music_library_orchestration_rules_v0.1_bilingual.md`
- Reference: `ai_music_prompt_templates_v0.1_bilingual.md`

- [ ] **Step 1: Add the internal `music_brief` section**

Add a concise section that lists the required internal fields:

```md
## Internal music brief

Build an internal `music_brief` before writing any final prompt.

Required fields:
- mode
- track_type
- theme
- use_case
- language
- genre
- mood
- tempo
- vocal
- instrumentation
- structure
- energy_curve
- hook_strategy
- avoid
- output_format
```

State that not every mode needs every field, but every final output must come from a structured brief.

- [ ] **Step 2: Add library-loading rules**

Add a section that explicitly says:
- always read the customer interaction workflow and orchestration rules first
- then load only the relevant deep library files as needed
- use one call chain for vocal songs and one for instrumental BGM

Include these exact chains:

```md
Vocal song:
Use Case Structure → Genre → Emotion → BPM/Rhythm → Vocal → Instrumentation/Arrangement → Prompt Templates

Instrumental BGM:
Use Case Structure → Genre → Emotion → BPM/Rhythm → Skip Vocal → Instrumentation/Arrangement → Prompt Templates
```

- [ ] **Step 3: Add output templates at controller level**

Add a high-level output-rules section that defines the required blocks for:
- `create_vocal_song`
- `create_instrumental_bgm`
- `optimize_existing_prompt`
- `optimize_existing_lyrics`
- `generate_multi_versions`
- `generate_short_video_hook`

Keep it structural. Do not paste full examples from the template library.

- [ ] **Step 4: Add language rules exactly as approved**

Include these rules:
- lyrics follow user request and default to Chinese when unspecified
- tool-ready prompt modules default to English
- human-facing explanation can follow the user language
- explanation text must not be mixed into prompt blocks

### Task 4: Add safety, quality checks, and final self-review

**Files:**
- Modify: `SKILL.md`
- Reference: `docs/superpowers/specs/2026-06-06-ai-music-prompt-skill-design.md`

- [ ] **Step 1: Add safety rules**

Add a section that states:
- do not directly imitate real artists or songs
- rewrite artist-comparison requests into abstract genre, era, texture, or mood language
- include commercial licensing reminder when the use case is commercial

- [ ] **Step 2: Add a short quality checklist**

Include checks for:
- clear track type
- use case reflected in structure
- mood translated into musical behavior
- prompt specificity
- correct lyric/prompt language split
- copy-ready iteration prompts

- [ ] **Step 3: Review against the spec for scope control**

Manual review checklist:
- no TODO or TBD markers
- no duplicated long-form library content
- all six modes present
- language rules present
- safety rules present
- output rules present
- wording stays within v1 scope

Expected result: `SKILL.md` is actionable, lean, and aligned with the spec.

- [ ] **Step 4: Commit the completed `SKILL.md`**

```bash
git add SKILL.md
git commit -m "docs: add first version of AI music prompt skill"
```

If commits are intentionally deferred, note that explicitly instead of inventing a commit.

