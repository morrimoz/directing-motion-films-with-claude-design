---
name: directing-motion-films-with-claude-design
description: Use when making a motion graphics video, launch film, product promo, explainer, animated ad or showreel with Claude Design (or any code-rendered animation - HTML/canvas, HyperFrames, Remotion), when reviewing or iterating on such a video, or when a generated video looks generic, cluttered, UI-heavy, mushy, slow, or "AI-made".
---

# Directing motion films with Claude Design

## Overview
The prompt is about 10% of the video. The other 90% is the harness: a reference, a locked look, a director's brief, gated stages, and a critique loop that measures real frames. Without them, Claude falls back to its default film: centred text on a dark gradient, everything fading in, a logo at the end.

You are the director. Claude Design is the crew. Your job is to hand it a brief and hold every gate.

## When to use
- Starting any motion video, launch film or animated promo.
- Reviewing an export, or writing the next revision prompt.
- Symptoms that mean a gate was skipped: interface screenshots as the content, several things on screen at once, one background colour for the whole film, fades and crossfades everywhere, a story strangers can't follow, the same bug coming back next round.

**Not for:** filming screen recordings with a presenter (that is a shot list plus a script), or pure AI-video generation with no code layer.

## The gates
Each gate produces the named artifact. **Do not start a gate until the previous artifact is approved by the human.** Gates 0-3 can go out in one message. **The stop before style frames is the one that is never skipped, even when the human says "fast".** Unknown facts go into the brief as `[BRACKETS]`. Never invent them, and never wait for them before drafting.

| # | Gate | Required artifact |
|---|---|---|
| 0 | **Route** | A one-line decision: Claude Design (visual canvas, human relays reviews) or a Claude Code harness (renders and critiques its own frames). Record it in the brief. |
| 1 | **Brief** | `director-brief.md`, filled from `director-brief-template.md`, including the logline, the stranger test and the locked copy table |
| 2 | **Reference** | 1-3 reference videos or frames, each with what to take and what not to take (in the Claude Design route this lives in the brief's reference section). The tool extracts the frames and describes the pacing shot by shot **before** designing. If it cannot read video, upload 6-10 stills from each reference. |
| 3 | **Assets** | Every image, logo, font file and screenshot **uploaded** to the tool. Never rely on local file paths. |
| 4 | **Style frames** | 4-6 **stills** that define the look. No motion. |
| 5 | **Animatic** | The full timeline on the beat grid, with the real story order, rough motion and placeholder slots |
| 6 | **Full pass** | Final motion to the spring spec, with native reframes: 16:9 and 9:16 composed separately, plus 4:5 when the Instagram feed matters |
| 7 | **Sound** | Scored to the beat grid (a licensed track, measured, or synthesised), plus a listening pass |
| 8 | **Ship** | Full-resolution exports with audio, a loop check, a poster frame or thumbnail, and a contact sheet |

## What a frame is
- **One hero element, filling 60-90% of the frame.** A word, a shape, a pattern, a product shot, or one simplified piece of interface with at most 3 lines.
- **Flat, full-bleed colour fields** that change on hard cuts. At most 3 colours per frame.
- **Type with extreme contrast:** a giant heavy display face for key words, a light secondary face, and tiny monospace chrome.
- **Editorial chrome on every frame**: a chapter label, a timecode, one brand element (the name or URL), and crop marks. A BPM readout is optional; drop it if it jars with a consumer brand. The chrome unifies scenes that otherwise look nothing alike, and in 9:16 it sits inside the safe zone.
- **Graphics and icons illustrate concepts. Interface appears only as proof.**
- **No** glow, glass, blur halos, vignettes or constant background texture. A signature motif (dots, particles) is a hero moment, not wallpaper.

## Motion spec
- **Hard cuts on the beat.** About one idea per 1-2 beats; 100-120 BPM suits launch films.
- **Closed-form springs**, profiled by element class. Default values:

  | Class | Used for | Damping ratio | Settles in |
  |---|---|---|---|
  | Snappy | Interface | 0.7 | about 0.25s |
  | Default | Cards, camera | 0.85 | about 0.4s |
  | Heavy | Big type, logos (no overshoot) | 1.0 | about 0.5s |
  | Playful | Mascots, icons (visible overshoot) | 0.5 | - |
- **Position and scale carry motion. Opacity-only transitions do not.** Add directional motion blur on fast moves.
- **Hook in the first 2 seconds, and a visual payoff every 3-5 seconds.**
- **Loop:** the call to action holds for at least 1.5s, then the final beat cuts back to frame 1.
- **Length is a whole number of bars** (at 120 BPM a bar is 2s, so 30s, 44s, 46s and 60s all fit).

## Every review round
**REQUIRED:** follow `critique-checklist.md`. It covers contact sheets at 2fps, transitions at 10fps, a safe-zone overlay for 9:16, frame-pair diffs for texture motion, and a 1-10 score per dimension. **Write the three worst problems and fix only those.** Repeat until every score is 8 or above. **Re-check the locked copy table every round**; tools silently rewrite copy.

## Red flags: stop and go back a gate
- Animating before the style frames are approved.
- There is no reference, or the reference was never described shot by shot.
- A stranger could not state what the product does after one silent viewing.
- The same defect appears in two consecutive rounds. Your brief is ambiguous, so rewrite that line as a measurable rule (pixels, seconds, percentage of the frame).
- An export is judged without its audio, or 9:16 is judged by cropping 16:9.
- "It just needs polish" after round 3. Polish never fixes a wrong visual language; return to gate 4.

## Tool gotchas (Claude Design)
- **Upload assets.** Local paths are read as filenames and render as placeholders.
- **Quick exports** are often 720p with no audio. Check with `ffprobe` before judging either.
- It reports "I haven't watched the result". **You** must look at the frames.
- **Review stills can carry the wrong timestamp.** Read the scrubber, not the filename.
- **Restyling:** a new page in the same project keeps the audio, timing and export scripts. A **new project** is right when the old look keeps leaking back in - seed it on the first message with the brief, the references, every asset, and any audio or timing files worth keeping.
- If Claude Design has an effort setting, use the highest one for a new film.

## Sources
- The Movez course, "How to build motion design studio with Opus 5.5" (x.com/0xmovez, 2026-09-27): harness over prompt, reference, spec, springs, sound, critique loop, gates.
