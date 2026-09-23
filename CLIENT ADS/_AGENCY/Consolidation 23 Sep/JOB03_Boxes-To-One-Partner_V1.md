# Peptide Ads | Consolidation | 23 Sep — render job 3 of 15

**Concept:** Consolidation | Static | Boxes To One Partner | V1
**Method:** Route B single pass per `SHARED-PRODUCTION/S09`. Two takes per ratio,
one batch, `nano_banana_pro` at 4k. Model echo checked on the first poll before
the spend landed — `nano_banana_2`, correct.

## The packshot reference was deliberately omitted

The job sheet carried the standing "attach the packshot as image_references" line,
but this concept's own HERO and NEGATIVE blocks forbid any product: *no vial, no
bottle, no jar, no packshot, no product of any kind appears anywhere in the frame*.
Attaching a four-vial packshot would have pushed the one element the brief bans
into the picture, and a dark studio product shot shares no light or palette with a
daylight whiteboard. Treated as boilerplate carried from jobs 1 and 2. Flagged to
the user rather than done silently.

## The 9:16 fix that finally worked

Jobs 1 and 2 both put the lowest text at 86–92% of the frame, inside Meta's UI
zones, and neither percentages nor a named pixel row nor negative-list entries
moved it. This job stopped instructing placement and changed the composition
instead: **the board's bottom edge is visible at about 88% of the frame with grey
wall below it.** The footer then has somewhere to sit that is not the frame edge.

| | job 1 | job 2 | job 3 take 1 | job 3 take 2 |
|---|---|---|---|---|
| lowest text | 86.3–88.5% | 88.8–91.0% | **81.7–83.7%** | **74.8–77.8%** |

Take 2 is the first vertical in this set fully inside the 14–80% band. Take 1 is
3.7 points over at the bottom. Giving the frame a physical object to end against
beats telling the model where pixels go.

## Delivered

| # | Ratio | job_id | master | delivered |
|---|---|---|---|---|
| 1 | 1:1  | `b1050c90-f9b4-41e8-a650-ad49f99e959a` | 4096×4096 | 1080×1080 |
| 2 | 1:1  | `73432433-45c9-408f-859e-014404d492e7` | 4096×4096 | 1080×1080 |
| 3 | 9:16 | `3f639c0f-27fc-48c4-a740-3bd4d7b33887` | 3072×5504 | 1080×1920 |
| 4 | 9:16 | `590f2ad0-858e-4c18-bddd-813732a233d2` | 3072×5504 | 1080×1920 |

9:16 masters 0.5581 again, centre-cropped and resampled to 0.5625 exactly.

## Letter-by-letter read-back — delivered files, RapidOCR at 2×

**All nine strings correct in all four takes. Zero drift.** No numerals anywhere.
No unapproved strings. Each of the five box strings appears exactly once per take,
so no sixth rectangle and no repeated box string.

Two line-break false alarms worth recording, because the naive check flags them:
in both 1:1 takes `ONE PARTNER` comes back as separate `ONE` and `PARTNER` boxes,
stacked inside the blue rectangle, and `BUILT ONLY FOR PEPTIDE BRANDS` splits
across two boxes in 1:1 take 2 and 9:16 take 1. Both are line breaks inside the
right strings, not missing or misspelled text. **Match on the concatenated,
punctuation-stripped string, never on the token list.**

Hand-lettering held up: confidences 0.91–0.99 across every marker word, no
gibberish, no handwriting-shaped marks that are not letters.

## Positions

1:1, feed, no platform UI: both pass, all type inside the 6% side margins.
Take 1 headline 13.5–17.2%, footer 85.8–89.3%. Take 2 headline 14.6–18.0%,
footer 82.9–87.0%.

9:16 take 1: headline 14.1–18.4%, boxes 23.5–52.5%, `ONE PARTNER` 61.1–65.0%,
turn line 69.8–76.8%, footer 81.7–83.7%. Every element but the footer inside band.

9:16 take 2: headline 18.5–20.8%, boxes 23.6–49.1%, `ONE PARTNER` 57.6–61.2%,
turn line 65.5–69.2%, footer 74.8–77.8%. **Everything inside 14–80%.**

## Not verified — needs a human eye

`cloudfront.net` is blocked from this container, so the images cannot be looked at
here. Strings, spelling, counts, digits and positions are all machine-checked. The
brief's *no product, no hands, no people* requirement is **not** machine-checkable
and has not been confirmed. The reference was omitted and the negative list carries
it, so the risk is low, but someone should open the four files and confirm.

## Cost

Balance 15,436.96 → 15,420.96 = **16 credits**, 4 per image. No escalation: nothing
misspelled once, let alone twice.

## Recommendation

Ship 9:16 take 2 as the vertical. It is the cleanest file this set has produced.
For the square, take 2 sits slightly better on the page. Carry the visible-bottom-
edge trick into every remaining vertical in the set.
