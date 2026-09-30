# Flagship 45-second video — build log, 30 Sep 2026

**Delivered:** 1080×1920, 45.21 s, 24 fps, 38 MB, 6.9 Mbps, AAC, hard cuts only.
`https://d2ol7oe51mr4n9.cloudfront.net/user_33uTwjMVb5NBs9hREmEUJfVFSFg/21731a6f-ea71-4780-a797-4a4209ba6f88.mp4`

Built to the 9-scene brief and to `V01 — Hook and message doctrine for long-form
video`. Nine separately generated Seedance clips, stitched, graded once, typed.

## READ THIS FIRST — the numbers do not match the claim bank

`CLIENT ADS/_AGENCY/CLAIM_BANK.md`, approved by Armin 2 Sep and **re-supplied
23 Sep after a render went out with an unapproved label**, says:

> Nothing numeric may appear in a Peptide Ads creative unless it is on this page.
> An ad carries numbers from this page or it carries none.

Four of the brief's five on-screen numbers are not on that page:

| On screen in this cut | Nearest approved | Match |
|---|---|---|
| `$30M+ scaled` | L1 `$40M+ MANAGED` | ✗ different figure and different verb |
| `3 to 5X average ROAS` | L2 `4.2x ROAS`, L3 `3.8x ROAS` | ✗ range, not a point figure |
| `60% lower CAC` | L7 `31% LOWER CPA` | ✗ different figure, CAC not CPA |
| `40% average profit margin` | — | ✗ no comparable entry |
| `60+ peptide brands` (VO only, not on screen) | C2 | ✓ |

The brief states these are real, sourced and gate-verified, and explicitly
forbids substitution, so they were used as given. But **no gate was run here and
none could be**: `peptideads.com` is refused by the organisation's egress proxy
(HTTP 403 on CONNECT), so the live-page check that `CLAUDE.md`'s *Never* section
requires did not happen, and the `flib.py` format-library gate the doctrine's §4
describes does not exist anywhere in this repository. **Nothing in this build
verified those four numbers. Armin or the claim bank has to.**

One thing the brief worried about that is *not* a problem: the `$12,000 / 3
months / 10% + 10%` pricing never reaches the screen or the voiceover in the
9-scene script, so C9 (*pricing or fees — DO NOT USE*) is not triggered by this
deliverable.

If the bank wins, the swap is cheap: the picture carries **no numbers at all** —
every figure is burned type over black, and the voice is 0.1 credits. Changing
all four costs one TTS regeneration and one type burn. No clip is re-rendered.

## Three corrections to the brief's technical spec

1. **There is no 5-second generation cap.** `seedance_2_5` takes 4–30 s. Each
   scene was generated at roughly 1.4× the length it needed so the cut could land
   inside the first 70% of motion.
2. **The cap is black, not blue.** The brief says to name a cap colour, with the
   stated reason being that omni_reference drifts warm. The real packshot
   (`PeptideAds Iterations/PA_00_control_1x1.png`) has a **glossy deep-black**
   flip-off cap; the blue is the `Ads` highlight and the accent palette. Every
   prompt names *glossy deep-black cap, cool blue-steel palette, no warm/amber/
   golden/orange tones*, which serves the anti-drift intent without repainting
   the product.
3. **The real packshot file could not be attached.** `upload.higgsfield.ai` is
   refused by the same egress policy, so the on-disk PNG could not reach
   Higgsfield storage. Instead a canonical packshot was rendered on `gpt_image_2`
   to match the control exactly and OCR-verified before anything was built on it,
   then used as the `image_references` anchor on all five product scenes.
   Same for the logo: rather than attach `logo.png`, the wordmark is **typeset in
   the burn**, so the model never gets the chance to invent the mark at all.

## The packshot anchor, and a measurement trap

First render measured **2.75** on height ÷ body width — past Armin's 2.5 fail
line. It was shot on a glossy reflective floor, and **the reflection joins the
silhouette**, inflating the height. Re-rendered on matte ground with an explicit
"two of its own widths stacked" instruction:

| Take | Ratio | Verdict |
|---|---|---|
| glossy floor | 2.75 | FAIL |
| matte, take A | 1.96 | PASS |
| matte, take B | 1.94 | PASS — used |

**Measure vial proportion on matte ground only.** A reflective surface makes a
correct vial measure as a bottle.

Take B's label reads `Peptide` 1.00, `Ads` 1.00, `META` 0.99, `ADS` 0.98,
`For Peptide Brands Only` 1.00. No digits, no non-Latin glyphs.

## Structure

| # | Beat | Screen | Picture | Product |
|---|---|---|---|---|
| 1 | Hook | 0.00–6.35 | vial in a hard top shaft, slow push-in | yes |
| 2 | Diagnosis | 6.35–10.20 | three blank grey plaques land one by one | no |
| 3 | Diagnosis | 10.20–14.50 | carousel of blank panels, never revealing | no |
| 4 | Turn | 14.50–20.20 | a column of dots ignites blue and climbs | no |
| 5 | Sunk cost | 20.20–24.35 | a column of light eroding into ash | no |
| 6 | **Reveal** | 24.35–28.74 | out of black, the vial slams into one beam | yes |
| 7 | Proof | 28.74–33.50 | the vial rotating, forensic, razor sharp | yes |
| 8 | Offer | 33.50–38.90 | three identical vials, three pools of light | yes |
| 9 | CTA | 38.90–45.21 | locked centre, unbroken push-in | yes |

Four of nine beats carry **no product at all**. Scenes 2–5 were given no
image reference on purpose — attaching a vial to a no-product scene is how the
banned element gets into frame (rule 11).

Scene 8 uses **three** vials, not four or more: the bank's own finding is that
the model holds the 2:1 proportion at four and stretches it at six.

## The 60–70% cut rule — first real data point

The doctrine flags this as untested. It held: every one of the nine clips was
usable inside its first 70% of motion, and none of the nine needed its in-point
moved off zero.

| Scene | Generated | Used | % of clip |
|---|---|---|---|
| 1 | 9.04 s | 6.35 s | 70.2 |
| 2 | 6.04 s | 3.85 s | 63.7 |
| 3 | 6.04 s | 4.30 s | 71.2 |
| 4 | 8.04 s | 5.70 s | 70.9 |
| 5 | 6.04 s | 4.15 s | 68.7 |
| 6 | 6.04 s | 4.39 s | 72.7 |
| 7 | 7.04 s | 4.76 s | 67.6 |
| 8 | 8.04 s | 5.40 s | 67.1 |
| 9 | 9.04 s | 6.11 s | 67.6 |

Generating ~1.4× and discarding the tail costs about 40% more credits and buys
a settle-free out point on every cut. On this evidence it is worth it.

## Cuts: seven of eight register, one does not

Hard cuts only, no dissolves and no flash frames — the brief excludes them and
this film's register is restrained, not disruptive. Measured on the delivered
file with `-loglevel info` (rule 14):

| Threshold | Cuts found |
|---|---|
| 0.30 | 6.38, 39.08 |
| 0.20 | 6.38, 28.88, 33.67, 39.08 |
| 0.15 | 6.38, 10.25, 14.58, 24.46, 28.88, 33.67, 39.08 |

Seven of the eight boundaries register by 0.15. **The one that never registers
is 20.20, scene 4 → scene 5** — the climbing dot column into the eroding light
column. Both are cool-blue geometry on black and they read as one continuous
shot to the detector. If it reads that way to the eye too, the fix is to
re-render scene 5 with a different form or a different value, not to add a flash.

## Voice and captions

`seed_audio`, preset voice Reid, **0.1 credits**. Came back at 51.78 s for 118
words (133 wpm); trimmed and paced with `atempo=1.1507` to **45.006 s**, which is
153 wpm — the pace of the approved cuts. The picture is cut to the resulting
word timings, not the other way round.

**Captions are phrase-synced, not strictly word-by-word, and that is deliberate.**
The brief asks for karaoke captions on scenes 1 and 9; the doctrine's §4.2 asks
that an approved number keep its qualifying phrase as a **contiguous** string.
Strict word-by-word would show `40%` / `average` / `profit` / `margin` as four
separate cards and break exactly the adjacency the gate exists to protect. So
scene 1 holds `40% average profit margin` whole on one card and runs the rest of
the line as timed cards. Scenes 2–8 are static supers, unanimated, as briefed.

## QA on the delivered file

- **Every on-screen string reads, 14 of 14.** Frames sampled inside each super's
  window and OCR'd. `40% average profit margin`, `$30M+ scaled`,
  `3 to 5X average ROAS`, `60% lower CAC`, `The Q4 Growth Team` all read as
  contiguous strings.
- **`peptideads.com` first read as missing and is not.** The whole-frame pass at
  44.40 s could not see it against the volumetric rays behind it. Band-cropped
  and re-read at 2×, 3× and 4×: `peptideads.com` at **1.00** every time.
- **Captions clear all four Meta lines**, measured per rule 15 by burning the
  subtitle track over black: y 518–1217, x 201–878. Against Reels top-14 % (269),
  Reels bottom-35 % (1248), Stories bottom-20 % (1536), 6 % gutters (65–1015).
  A whole-frame measure had said y up to 1434 and x to 1017 — **that was the
  vial's own label, not a caption.** Rule 15 caught it.
- **No non-Latin glyphs anywhere.**
- **One grade pass after stitching**, not per clip: `eq=saturation=1.08:contrast=1.05`
  plus light grain, applied to the 45 s stitch before any type was burned, so the
  supers stay clean.

## Two things the brief asked for that this cut does not fully hit

1. **The CTA is held 1.4× the average beat, not 2–3×.** With 9 scenes at ~5 s
   inside a 45 s total, there is no room for a 9–13 s CTA without rushing the
   reveal, which the brief separately says to give room. It is the longest beat
   in the film by a clear margin. To get a true 2–3× the film has to run to about
   52 s, which both Reels and TikTok allow.
2. **Hook and reveal both open with "Here's".** The doctrine says to grep the
   hook for anything the reveal reuses. Numbers: no overlap, correct —
   `40% average profit margin` against `$30M+ scaled`. But *"Here's how they get
   there"* and *"Here's the number they're not showing you"* share the opener.
   The script is locked and substitution is forbidden, so it stands — flagging it
   because the doctrine's own rule finds it.

## Known gap — sound

There is still **no sound-design tooling in this pipeline**: no foley, no music
bed, no sidechain ducking under the voiceover, no J-cuts or L-cuts across the
scene boundaries. The delivered file is voiceover only over picture. Per the
doctrine's §3 this is flagged rather than papered over with a flat music bed.

## Not machine-checkable

Whether the vial is recognisably the same vial across five separately generated
clips; whether the three vials in scene 8 are truly identical; whether the
scene 4 → 5 boundary reads as a cut to a human eye; whether the grade sits right;
and whether anything banned leaked into a frame between the sampled points.
**Eyes on the file before it goes to Ad Central.**

## Spend

| Item | Credits |
|---|---|
| Voice, `seed_audio` | 0.1 |
| Packshot stills ×3 (1 + 2 re-rolls), `gpt_image_2` 4k high | ~33 |
| 9 scenes, `seedance_2_5` 1080p, 65 s generated at 12 cr/s | 780 |
