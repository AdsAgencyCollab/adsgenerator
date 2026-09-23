# Peptide Ads | Set 2 Learning Curve | 23 Sep — render job 6 of 15

**Concept:** Learning Curve | Static | The Claim Is Where It Breaks | V1
**Method:** as job 5. Model echo verified.

## Delivered

| # | Ratio | job_id | master | delivered |
|---|---|---|---|---|
| 1 | 1:1  | `9d2c4568-7f59-4b4b-b325-bc6956e91c80` | 4096×4096 | 1080×1080 |
| 2 | 1:1  | `8a58937a-7a17-4d1e-af36-59ab522daacd` | 4096×4096 | 1080×1080 |
| 3 | 9:16 | `b2408da8-d5ea-4bb2-89cd-c5bbab1cb3b6` | 3072×5504 | 1080×1920 |
| 4 | 9:16 | `cb79c4f7-4bbb-40a5-87fb-086aa3b4d52f` | 3072×5504 | 1080×1920 |

## Read-back

All nine strings present in all four takes. No numerals. No unapproved strings.

**The ellipsis is correct in all four.** OCR read `again..` at 1080 on three of
them, so it was measured directly: the trailing blob widths after the last letter
are 29/29/29, 27/27/27, 24/23/23 and 23/23/22 — three equal dots every time. A
two-dot reading at delivery size is an OCR merge, not a rendering fault. **Measure
an ellipsis, never trust OCR on it.**

**Drift, 9:16 take 2: the label reads `For Peptide Brands Only.` with an added
full stop.** Confirmed at 5× zoom on the 4K master at 0.99 confidence. Take 1's
label is clean, so no escalation is triggered — the rule is a string misspelled in
*both* takes.

**Defect, 9:16 take 1: both badge pills wrap onto two lines** (`WRITTEN AGAINST` /
`THE POLICY` and `NOT` / `GUESSED AT`), against the ARTIFACT rule of one line each,
no wrapping. The strings themselves are correct.

So each vertical take has one distinct fault and neither is clean.

## The bottom-edge fix does not transfer to this scene

Job 3 solved the vertical safe-zone problem by giving the board a visible bottom
edge to sit above. This brief tried the same idea with a cast shadow running to
the bottom edge, and it failed:

| | brief | take 1 | take 2 |
|---|---|---|---|
| `Learn More` | ~77% | 87.4–89.4% | 85.8–88.0% |
| `peptideads.com` | <80% | 91.8–94.1% | 90.5–92.4% |

A shadow is not an edge. What worked in job 3 was a **physical object boundary**
with a different surface behind it, which gives the composition somewhere to stop.
A floor that runs to the frame edge gives the model nowhere to put the CTA but the
bottom. Add this to the rule: the fix is an object edge, not dark space.

1:1, feed, no UI: both clean, footers at 93.6–96.6%, nothing to collide with.

## Cost, jobs 5 and 6 together

Balance 15,420.96 → 15,340.96 = **80 credits**. Job 5 16, job 6 16; the remaining
48 covers the four flash renders and the gpt_image_2 probe charged earlier in the
session against this balance window.

## Recommendation

Ship both squares from job 6. Neither vertical is shippable as-is: take 2 needs the
full stop off the label, take 1 needs the pills on one line, and both need the CTA
and footer lifted above 80%. For V2, give the scene a real object edge across the
lower frame, and shorten `WRITTEN AGAINST THE POLICY` so it cannot wrap.
