# Wave 28 Sep — Video 2, "Ask What Else They Run"

**Delivered:** 1080×1920, 15.5 s, 24 fps, AAC, burned captions.
`https://d2ol7oe51mr4n9.cloudfront.net/user_33uTwjMVb5NBs9hREmEUJfVFSFg/1c234932-1284-4907-9b52-a6b88823d91a.mp4`

Armin, 28 Sep: *"we need other scenes that don't necessarily have the plain vial
bottle… allusive motion graphics."* So six of the seven beats carry **no product
at all**. The vial appears once, in the last 1.37 seconds, as the payoff.

## Structure

| # | Beat | In | Out | Line |
|---|---|---|---|---|
| 1 | a vast grid of blank grey plaques, rows flipping like a departure board | 0.00 | 1.85 | *Ask the agency what else they run.* |
| 2 | three plaques ignite — a leaf, a chair, a tooth | 1.85 | 4.10 | *A supplement brand. A furniture store…* |
| 3 | conveyor of identical grey boxes, one shunted off the line | 4.10 | 6.30 | *…A dental clinic.* |
| 4 | a column of blue light eroding into ash and blowing away | 6.30 | 10.20 | *Your account is where they learn your category. You pay for the lessons.* |
| 5 | black; one shaft of light, one plaque ignites blue | 10.20 | 12.10 | *We run peptide brands.* |
| 6 | radar sweep locks onto one blue cluster | 12.10 | 14.05 | *Sixty plus. Nothing else.* |
| 7 | hero vial rises into the beam | 14.05 | 15.42 | *Book the call.* |

Mean shot length 2.20 s. The icons are pure line shapes, never words — the
categories have to read without type, because a named brand on screen is a
claim we cannot make and a logo we do not own.

## A finding: on a dark film, only a white flash reads as a cut

Every beat here is blue-on-black, so **the cuts do not register at all** to
ffmpeg scene detection — the frames either side of a cut are equally dark and
equally sparse. First assembly, threshold 0.30: four detections, and all four
were the white flashes already inserted. The four real content cuts at 4.10,
6.30, 10.20 and 14.05 were invisible.

Black blink frames were tried next and made no difference: **a 2-frame black on
near-black footage is a no-op.** Only after each content cut got a 2-frame WHITE
flash did the cut register — ten detections, five of the six transitions.

The one that still does not register is the 3-frame black at 10.20, the PAS
turn. It is kept anyway because it lands inside the voiceover's own 0.34 s pause
between *lessons* and *We*, so the turn is carried by the silence rather than by
the picture. **It is not claimed as a visible cut.**

What a detector cannot see, an eye may still catch — but the reverse is the risk
worth designing against, and the flashes remove it.

## Voice

Generated separately this time: `seed_audio`, preset voice Reid, **0.1 credits**.
It came back at 21.9 s for 40 words — 110 wpm, far slower than the approved cut.
Trimmed of head and tail silence and paced up by `atempo=1.4144` to 15.42 s,
which is 156 wpm, **the same pace as video 1**. Pitch is preserved by atempo.

Decoupling the voice from the picture is the real win here: the VO costs a tenth
of a credit, so the script can be re-cut and re-timed freely without touching a
single 48-credit beat.

## QA

- **31 picture frames sampled at 2 fps.** `PeptideAds` reads on 3 of them — and
  it should read on exactly 3, because the vial is only on screen for the last
  1.37 s. Every other frame is product-free, as briefed.
- **No non-Latin glyphs.** No fullwidth, no CJK, no Cyrillic.
- **One stray `S` at 4.5 s, disproved.** A 327 × 320 px box at 0.61 confidence in
  the conveyor beat. Band-cropped and re-read at 2×, 3× and 4×: `NO TEXT` at all
  three. It is an S-shaped piece of belt geometry, not baked type. A letter that
  tall in a 1080-wide frame would be unmissable.
- **All 40 voiceover words transcribe back against the script.**
  `[QA] ok — every caption word is in the script`. 26 caption groups.
- **Captions clear every Meta safe zone**, measured by burning the subtitle track
  over black: y 1163–1213, x 361–720. Clear of Reels top-14 % (269), Reels
  bottom-35 % (1248), Stories bottom-20 % (1536), 6 % gutters (65–1015).
- **`Sixty` stayed a word.** The transcriber wrote `60` again; patched before
  grouping, per rule 16.
- **Storyboards carried no stray text**: seven of eight panels OCR'd completely
  clean, and the eighth — the hero — read `PeptideAds` 0.95 and
  `For Peptide Brands Only` 1.00.

## Not machine-checkable

Whether the leaf, chair and tooth icons read as *supplement, furniture, dentist*
without a word of type; whether the flashes feel like punctuation or like
strobing; whether the eroding column reads as budget burning or as decoration;
and whether anything banned leaked into a frame between the sampled half-seconds.
**Eyes on the file.**

## Spend

| Item | Credits |
|---|---|
| Boards ×2, `gpt_image_2` 21:9 2k high | ~22 |
| Beats ×7, `seedance_2_5` 1080p 4 s, audio off | 336 |
| Voice, `seed_audio` | 0.1 |

**The account is losing credits to something outside this session.** Balance fell
964.92 → 814.92 while no job of ours was running, and twenty Nano Banana Pro
charges appeared during the video 1 rebuild that this session never submitted.
Video 3 on this pipeline is roughly another 360.
