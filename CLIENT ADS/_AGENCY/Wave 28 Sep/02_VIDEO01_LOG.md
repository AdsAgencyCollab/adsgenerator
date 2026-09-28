# Wave 28 Sep — Video 1 of 3, "The Learning Curve"

**Delivered:** 1080×1920, 15.04 s, AAC audio, burned captions.
**Cost: 180 credits**, preflighted with `get_cost` before submission and
confirmed on the bill. Three videos would have been 540.

## Pipeline

Adapted from the `ugc-product-video` workflow, which is the only bundled flow
that is multi-scene, product-hero and has no creator on camera. Structure kept:
a 21:9 storyboard of four 9:16 beats becomes ONE Seedance clip carrying three
internal hard cuts, then captions are burned from the finished audio.

| Step | What ran |
|---|---|
| Board | `gpt_image_2` 21:9 2k high, job `a69be232-cafb-4f95-bbe3-471c86836010` |
| Clip | `seedance_2_5`, `omni_reference`, 9:16, 1080p, 15 s, audio on, job `8c8b49b9-298a-484d-86c7-e2c168c2d158` |
| Captions | `transcribe_words` → `group_captions` → `make_captions`, burned with ffmpeg |
| Final | media `bb99a70c-b6a6-4968-b33d-7ea9019543de` |

## Two deliberate deviations from the workflow, both stated

**The de-slop pass was skipped.** The flow calls it mandatory, but its prompt
forces *"flat authentic iPhone photo, deep focus, AVOID cinematic / DSLR look"*
and spends most of its words on pore-level skin, vellus hair and preserving face
proportions. **There is no skin and no face in any frame of this ad** — the
compliance rules forbid both. Running it would have cost a generation and
actively fought the dark cinematic grade the brand uses. Skipped on purpose.

**A preset recommendation was declined.** The submission came back suggesting the
"IN THE DARK" preset. Declined with `declined_preset_id` — the storyboard is
driving composition here, and a look preset would have overridden it.

## QA

**The voiceover transcribes back word for word against the authored script.**
All 36 words, `[QA] ok — every caption word is in the script`, so no mis-heard
text could reach the burn. 23 caption groups, one to two words each, blanking in
the pauses, anchored in the bottom 15% safe band.

**`four months` stayed a word, never a digit.** The caption reference advises
writing numbers as digits for alignment, but the claim bank forbids on-canvas
numerals outside L1–L12, and a burned subtitle is on-canvas text. The word form
satisfies both and the alignment held anyway.

**No baked text anywhere.** Fifteen frames sampled at 1 fps and OCR'd: zero text
found in the source render, so every word on screen is a caption we control.

## Not machine-checkable

Whether the vial stays one vial across all four beats, whether the label reads
correctly through the motion, whether the cuts land where intended, and whether
any hand or person leaked into a frame between the sampled seconds. **All of it
needs eyes on the file before this goes anywhere near an ad account.**

## Videos 2 and 3

Boards are rendered and held: `b2adbc78-6114-414b-8e9d-5e437b93eaa8` (Ask What
Else They Run) and `a7f02d9b-235c-48ae-84a4-05c5d8d267a9` (This Isn't For
Everyone). Each is 180 credits to finish, same pipeline.
