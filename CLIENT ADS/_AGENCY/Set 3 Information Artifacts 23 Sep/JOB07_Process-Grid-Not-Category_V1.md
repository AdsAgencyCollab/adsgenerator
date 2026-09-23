# Peptide Ads | Set 3 Information Artifacts | 23 Sep — render job 7 of 15

**Concept:** Us vs Them | Static | Process Grid Not Category | V1
**Model:** `gpt_image_2` at 4k quality high, chosen in the brief for dense
typography. Two takes per ratio, one batch. Packshot attached with the standard
override paragraph.

## gpt_image_2 is the right model for a table, and the numbers say so

Nineteen approved strings, a four-row three-column table, and **zero drift across
all four takes.** No missing strings, no misspellings, no numerals, no invented
rows, no extra columns, no stray text. Confidences 0.85–1.00.

Every cell landed: `THE CATEGORY`/`ONE OF MANY`/`ONLY THIS ONE`,
`THE POLICY`/`READ AFTER`/`READ FIRST`, `THE CREATIVE`/`OUTSOURCED`/`IN HOUSE`,
`THE STACK`/`ADS ONLY`/`ALL OF IT`, under headers `A GENERALIST` and `PEPTIDE ADS`.

**It also honours the aspect ratio exactly.** Masters came back 2880×2880
(1.0000) and 2160×3840 (0.5625 precisely), so the conform step was a clean
downscale with no crop at all. nano_banana_pro returns 0.5581 for the same
request and always needs 43 rows of height cut. Worth remembering when a layout
is position-critical.

Cost is the trade: **11 credits per image against nano_banana_pro's 4.** This
batch was 44. Balance 15,340.96 → 15,296.96.

## Delivered

| # | Ratio | job_id | master | delivered |
|---|---|---|---|---|
| 1 | 1:1  | `2e818581-bbb4-48e8-a381-669a4f80dcf5` | 2880×2880 | 1080×1080 |
| 2 | 1:1  | `5e5d2045-322a-4c1c-9df6-d06e685b1602` | 2880×2880 | 1080×1080 |
| 3 | 9:16 | `d5d64a9a-12e8-46cc-a705-f29d8b248224` | 2160×3840 | 1080×1920 |
| 4 | 9:16 | `7e3546b8-09b3-4670-b7d6-67ae3c00c625` | 2160×3840 | 1080×1920 |

## The bottom of the vertical frame is solved

The card's bottom edge at 78% plus the shelf at 80% gave the composition a real
physical boundary, which is exactly what job 3 established and job 6 failed to
provide. Result:

| | job 6 (shadow to edge) | job 7 take 1 | job 7 take 2 |
|---|---|---|---|
| footer | 91.8–94.1% | **68.0–69.9%** | **66.5–68.3%** |
| lowest element | 94.1% | 80.6% | 76.3% |

Nothing sits in the bottom fifth of either vertical. The rule holds: an object
edge with a different surface behind it works, dark space does not.

## New failure mode — the top line, not the bottom

Both verticals put the headline **above** the 14% top-safe line:

| | brief | take 1 | take 2 |
|---|---|---|---|
| headline first line | 15% | **11.2%** | **11.9%** |

That is 41 to 54 pixels inside Meta's Reels top-14% UI band. Cause is the same
class of problem as the footer: the card's top edge is specified at 10% and the
model sets the headline hard against the inside of that edge rather than at the
15% it was told. **The fix is the same shape as the bottom fix — move the card's
top edge down to about 16% so the headline physically cannot start above 18%.**
Do not just restate the percentage.

1:1 takes are clean on position; feed carries no UI overlay and both footers sit
at 90.4–93.1% with nothing to collide with.

## Two notes for the record

The middle column's grey cross renders as a glyph OCR reads as the letter `X`,
which is why cells come back as `X READ AFTER`. That is the artifact working, not
stray text. Four crosses read cleanly in takes 2, 3 and 4; in 1:1 take 1 only
three were picked out separately, most likely an OCR merge rather than a missing
mark, but it is the one thing in this job worth a human glance.

**The brief contradicts itself on the label's case.** The proof list writes
`For Peptide Brands Only` in title case; the HERO block says set it "in small
white capitals". All four takes rendered capitals, following the HERO block. Not
counted as drift, but the two should be reconciled before this concept is reused.

## Not machine-checkable

No visual inspection is possible here. Strings, spelling, counts, digits and
positions are proofed. Whether the vial overlaps a rule or a word, whether the
four body rows are truly equal height, and whether the checks and crosses are
crisp rather than blobby all need a human eye.

## Recommendation

Ship both squares. The verticals are one prompt change from clean: drop the card's
top edge to 16% and they pass on every axis. Given the table came back perfect on
all four takes, keep `gpt_image_2` for every Information Artifact concept and keep
nano_banana_pro for the photographic ones.
