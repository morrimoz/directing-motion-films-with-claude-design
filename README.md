# Directing motion films with Claude Design

An [agent skill](https://cursor.com/docs/context/skills) for making motion graphics that do not look like the default AI film: centred text on a dark gradient, everything fading in, a logo at the end.

The prompt is about 10% of the video. The other 90% is the harness: a reference, a locked look, a director's brief, gated stages, and a critique loop that measures real frames.

## What it does

The skill walks an agent through nine gates. Style frames are approved before any motion. Each review round scores real frames and fixes only the three worst problems.

It also includes:

- `director-brief-template.md` - the brief pasted into the first message
- `critique-checklist.md` - ffmpeg contact sheets, a 9:16 safe-zone overlay, and a 1-10 rubric

Works with Claude Design, and with any code-rendered animation (HTML/canvas, HyperFrames, Remotion).

## Install

**Cursor** (all projects):

```bash
git clone https://github.com/morrimoz/directing-motion-films-with-claude-design.git ~/.cursor/skills/directing-motion-films-with-claude-design
```

**Claude Code:**

```bash
git clone https://github.com/morrimoz/directing-motion-films-with-claude-design.git ~/.claude/skills/directing-motion-films-with-claude-design
```

Restart the session so the skill is picked up. The folder must contain `SKILL.md`.

## Usage

Ask for a motion video, launch film, product promo, explainer, or animated ad. The skill also applies when a generated video looks generic, cluttered, UI-heavy, mushy, slow, or AI-made.

## Source

The process follows the Movez course, "How to build motion design studio with Opus 5.5" (x.com/0xmovez, 2026-09-27): harness over prompt, reference, spec, springs, sound, critique loop, gates.

## License

MIT
