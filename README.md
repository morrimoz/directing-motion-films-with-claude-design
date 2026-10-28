# Directing motion films with Claude Design

**Category: Creative AI workflows | Format: Agent skill and production templates**

A structured workflow for directing motion graphics with references, approved style frames, a timed brief and reviews of rendered frames. It can guide work in Claude Design or code-rendered animation tools.

This repository contains the production process and templates. It does not include a video renderer or a finished-film showcase.

## What is included

| Resource | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Nine stages from brief to export, with review gates |
| [Director brief](director-brief-template.md) | Audience, story, visual system, motion, sound, assets and delivery formats |
| [Critique checklist](critique-checklist.md) | Contact-sheet commands, vertical safe-zone checks and a review rubric |

## Workflow

Brief the film, inspect references, gather assets and approve still frames before animating. Build an animatic, finish motion and sound, then verify exports. Each review identifies three concrete problems to fix before the next pass.

The goal is to make creative decisions and acceptance checks explicit. The workflow does not guarantee a particular visual quality score.

## Install

For Cursor:

```bash
mkdir -p ~/.cursor/skills
git clone https://github.com/morrimoz/directing-motion-films-with-claude-design.git ~/.cursor/skills/directing-motion-films-with-claude-design
```

For Claude Code, use `~/.claude/skills/directing-motion-films-with-claude-design`. Start a new session after installation.

## Example request

```text
Use the directing-motion-films-with-claude-design skill for a product explainer.
Start with the brief and style frames. Use the supplied references and assets.
```

## Requirements and tradeoffs

A separate design or animation tool is required. Frame extraction and export inspection use FFmpeg and ffprobe. Human review is part of the workflow. References, licensed assets, rendering costs and final output verification remain the user's responsibility.

Native landscape and portrait compositions take more work than cropping a single export, but allow readable layouts in each format.

## Attribution

The workflow draws on the Movez course, "How to build motion design studio with Opus 5.5" by [0xmovez](https://x.com/0xmovez), published September 27, 2026.

## Related tool

[Plan to execution plan](https://github.com/morrimoz/plan-to-execution-plan) structures larger technical projects into bounded work and verification steps.

[MIT license](LICENSE)
