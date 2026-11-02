---
name: claude-reels-editor
description: Edit talking-head reels with Remotion in Claude Code using six data-driven overlay effects: over-the-shoulder proof cards, a frosted glass chart on the chest, a freeze-frame cut-out sticker on a gesture, an animated S to D tier list, a huge word behind the head, and a before/after colour-grade wipe. Every number comes from a file the user provides, never invented. Use when the user wants one of these reel effects, wants to show real stats or rankings over their talking clip, or says "edit my reel" with a Remotion project and a clip.mp4.
---

# Claude reels editor

Six overlay effects for a vertical talking-head clip, each built as one Remotion component. Credit: effects adapted from the "6 Claude prompts that edit my reels" pack by @brodyautomates. The specs below are rewritten summaries.

## Workflow

1. **Project:** a Remotion project (`npx create-video@latest`) with the clip saved as `clip.mp4` in the project. Claude Code runs in that folder.
2. **Inputs:** collect the effect's inputs (listed per effect). Anything in braces in a request is the user's own words or numbers.
3. **The numbers rule:** only use numbers the user can screenshot. Put them in a data file (`numbers.yaml`, `chart.yaml`, `tiers.md`) and read every value from it. Never make one up; if a value is missing, ask.
4. **Build** the component, preview with `npx remotion studio`, render, and report the output path.
5. **Check** the effect's own rule (face never covered, letters visible, everything in frame) on every frame and tell the user if it fails.

## Shared building blocks

- **Person matte:** per-frame person segmentation (MediaPipe selfie segmentation or rembg on Linux/Windows, Apple Vision on macOS). Draw order for "behind me" graphics: clip, graphic, cut-out person.
- **Face box:** per-frame face detection; shoulder line ≈ face box bottom + 0.55 × face height. Smooth over time.
- **Pose:** hand landmarks for gesture timing (freeze-frame).
- **Counting numbers:** ease-out count, tabular figures.

## The six effects

Full specs: [references/effects.md](references/effects.md).

| Command | Component | What it does | Inputs |
|---|---|---|---|
| over-the-shoulder | OverShoulder | Two real numbers on glass cards rising from behind the shoulders, person cut out in front | `numbers.yaml` with before and after |
| glass-graph | GlassChart | Frosted glass bar chart on the chest that climbs to a real total | `chart.yaml` with 3-10 values, total, title, period |
| freeze-frame | (FreezeFrame) | Freeze on a thumbs up, cut-out sticker with white outline, name tag | a clip with a thumbs up, name and role |
| tier-list | TierList | Claude ranks a list S to D, then it animates under the chin | the items, real logo files in `logos/` |
| text-behind | TextBehind | Huge 2-5 letter word behind the head, every letter readable | the word |
| color-grade | GradeWipe | Wipe from flat footage to a cinematic grade with BEFORE/AFTER chips | `clip.graded.mp4` or a draft grade |

## Related

For a larger library of 20 premium edits (reel wall, orbit, billboard, Kallaway layout and more), a house style, and an `/edit` command, use the `claude-code-edits` skill. The `remotion` plugin covers Remotion APIs and rendering.
