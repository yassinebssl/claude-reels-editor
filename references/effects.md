# The six reel effects

All run over `./clip.mp4` in a Remotion project. Read numbers only from the data file named in each effect.

## over-the-shoulder

Two glass cards rise from behind the shoulders, each showing a real number; the person is cut out in front so the shoulders overlap the cards' bottom edges.

- Inputs: `numbers.yaml` with a before value and an after value (labels optional).
- Per-frame person matte; dark glass cards drawn BEHIND the matte.
- Card bottoms sit on the shoulder line (face box bottom + 0.55 × face height). Left card shows the before value. Right card counts from the before value to the after value over 24 frames with ease-out, then a green delta pill pops in.
- No card pixel ever over the face or hair.

## glass-graph

A frosted glass bar chart on the chest that climbs to a real number.

- Inputs: `chart.yaml` with title, period, total and 3-10 values.
- Detect the face every frame. Frosted card (backdrop blur ~22 px, white gradient 20% to 6%, 2 px white border) on the chest, its top at least 40 px below the chin on every frame.
- Inside: title "<title> · <period>", a big number counting 0 to the total with ease-out, bars that spring up one after another.
- Green only for positive changes.

## freeze-frame

Plays to the peak of a thumbs up, freezes, and pops the person forward as a sticker with a name tag.

- Inputs: a clip containing a thumbs up; name and role.
- Hand-pose detection finds the frame where the thumbs up peaks. Play to it, white flash, freeze.
- Grey and blur the background; pop the cut-out forward as a sticker: 14 px white outline from the matte, soft drop shadow, tilted -2.5°.
- Coral name tag under the chin with name and role, never over the face or the hand.
- Hold 1.3 s, fade the sticker, resume the clip.

## tier-list

Claude ranks a list for the user's audience, then animates the result S to D under the chin.

- Step 1: rank the items in tiers S to D with one line of reasoning each; save the answer to `tiers.md` exactly as written, and use it verbatim.
- Step 2: shift the footage up so the face sits in the top third. Dark glass panel below the chin with five coloured tier rows.
- Tiles fly in from the right one by one using real logo files from `logos/` (never draw a logo). The S tier lands last, with a glow.
- A pill above the panel reads "Ranking ..." then switches to "Ranked" with a check.

## text-behind

A huge word behind the head, with the head in front and every letter still readable.

- Inputs: a word of 2-5 characters.
- Per-frame matte. Set the word in a condensed weight-900 sans (the pack used Archivo) as large as fits 750 px wide.
- Place it so the head covers at most 20% of the letters' height on the worst frame; shift the footage down if needed.
- Draw order: clip, word, person cut-out. The word rises from behind the head over 13 frames, then stays still.
- Verify every letter is at least 70% visible on every frame; report any frame that fails.

## color-grade

A before/after wipe from flat footage to a cinematic grade.

- Bottom layer: `clip.mp4` (flat). Top layer: `clip.graded.mp4`; if missing, make a draft grade (saturation 1.18, contrast 1.1, brightness 0.98).
- The graded layer shows left of a vertical white divider that sweeps left to right over 32 frames, with a round handle at shoulder height.
- AFTER chip top left; BEFORE chip top right that fades out before the divider reaches it. Everything stays inside the frame.
