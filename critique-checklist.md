# Critique checklist: every review round

Look at real frames, not descriptions. Tools often report "I haven't watched the result".

## 1. Inspect the file first
```bash
ffprobe -v error -show_entries format=duration:stream=codec_type,width,height,r_frame_rate -of compact "$V"
```
Note the resolution and whether there is an audio stream. **Never judge sound from a file that has
no audio stream.**

## 2. Contact sheets
```bash
mkdir -p frames
ffmpeg -v error -i "$V" -vf "fps=2,scale=480:-1" -q:v 4 frames/f_%03d.jpg
for s in 0 1 2 3 4 5; do
  ffmpeg -v error -start_number $((s*20+1)) -i frames/f_%03d.jpg -frames:v 1 -vf "tile=5x4" sheet_$s.jpg -y
done
```
Each sheet covers 10 seconds. For transitions and collisions, sample the moment at 10fps:
```bash
ffmpeg -v error -ss 14.2 -t 1.4 -i "$V" -vf "fps=10,scale=260:-1" t_%02d.jpg
```

## 3. The 9:16 safe-zone overlay
The red bands are the platform's top and bottom interface; the orange strip is its action buttons.
```bash
ffmpeg -v error -ss $T -i "$V" -frames:v 1 -vf "drawbox=x=0:y=0:w=iw:h=ih*0.14:color=red@0.28:t=fill,drawbox=x=0:y=ih*0.80:w=iw:h=ih*0.20:color=red@0.28:t=fill,drawbox=x=iw*0.88:y=ih*0.45:w=iw*0.12:h=ih*0.35:color=orange@0.25:t=fill" sz.jpg
```

## 4. Is the background texture actually moving?
Take two frames about 0.5s apart and compare them. If they look identical, the "animated" texture is
too small or too dim to read.

## 5. Score each dimension 1-10

| Dimension | 8+ means |
| --- | --- |
| Stranger clarity | Watching muted, the stranger test sentence is obvious |
| Hook | Something striking happens in the first 2s |
| One hero per frame | Every paused frame has one obvious focal point at 60-90% of the frame |
| Colour rhythm | Fields change with the chapters; never one colour for the whole film |
| Type | Key words are huge; nothing important is small |
| Motion feel | Springs with overshoot, hard cuts on the beat, no mushy fades |
| Craft | No overlaps, no clipped text, no placeholders left, no stray artefacts |
| Safe zones | Nothing important under the platform's interface (9:16) |
| Copy fidelity | Every line matches the locked copy table exactly |
| Truth | Every claim is true, and nothing invented |
| Sound | It lands on the cuts, and the key moments hit (once audio exists) |

## 6. Write the fix list
Write **the three worst problems**, each with a timecode, a cause and a measurable fix (pixels,
seconds, percentage of the frame, hex values). Send only those.

**If a problem already appeared last round, the brief is ambiguous.** Rewrite that brief line as a
rule, not a wish.

## 7. Before shipping
- The loop seam: the last frame flows into the first.
- The poster frame.
- Both aspects reviewed.
- One full listen with sound.
- A final full-resolution export.
