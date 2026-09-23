# Peptide Ads | Consolidation | 23 Sep — render job 2 of 15

**Concept:** Consolidation | Static | One Desk Whole Stack | V1
**Method:** Route B single pass per `SHARED-PRODUCTION/S09`. Two takes per ratio,
`nano_banana_pro` at 4k.
**Reference:** packshot job `435b8aac-ca66-4af7-a265-05bfcd0fb75e` as
`image_references` on all four. The `~/Downloads/...` path is not reachable from
the container. Brief overrides the reference on cap colour (deep-black, not the
reference's royal blue) and on label text; both stated explicitly in the prompt.

## Delivered

| # | Ratio | job_id | master | delivered |
|---|---|---|---|---|
| 1 | 1:1  | `d9c4ce8c-e5e2-453b-b149-b58141a8d932` | 4096×4096 | 1080×1080 |
| 2 | 1:1  | `5d29d694-c706-480e-a3b7-2e5060573ab0` | 4096×4096 | 1080×1080 |
| 3 | 9:16 | `d8414632-19d7-4037-a3db-a5ff633cc89c` | 3072×5504 | 1080×1920 |
| 4 | 9:16 | `a36e70fe-594a-40f0-95bf-d222b39ddbb7` | 3072×5504 | 1080×1920 |

9:16 masters again came back 0.5581; centre-cropped to 3072×5461 then LANCZOS to
1080×1920 = 0.5625 exactly. 1:1 needed no crop.

## Model-id trap — cost 12 credits

`generate_image_batch` takes `{index, params:{...}}`, and **the accepted model id
is `nano_banana_pro`, which the server then stores as `nano_banana_2`.** Passing
the stored id `nano_banana_2` is not rejected — it is silently swapped for
`nano_banana_flash`. The first batch of four ran on flash before this was caught.
Always read the `model` field back from `jobs_wait` before spending on a full set.

## Letter-by-letter read-back — delivered files, RapidOCR at 2×

Ten of eleven strings correct in all four takes, no numerals anywhere, each of the
five card strings appearing exactly once per take, no unapproved strings.

**Drift: `For Peptide Brands Only` is absent from all four takes.** The vial label
carries only the white Peptide·Ads plate; the second line was not rendered.
Verified at 4× zoom on the 4K masters over a generous label region, so this is a
real omission, not an OCR floor artifact.

One low-confidence read to watch: take 1 of the 1:1 returned the sub-headline as
`BUILT ONLY FOR PEPTIdE BRANDS` at 0.85 confidence, a lowercase d. Take 2 read it
clean at 0.98. Treat take 2 as the safer square.

## Escalation ran and did not fix it — cost 11 credits

Per the brief's gate (same string failing twice), one 1:1 was re-rendered on
`gpt_image_2` at 4k high, job `5140efbf-6678-4826-a009-52f46fb6e5e3`, prompt
unchanged except for an added instruction spelling out that the label has two
parts and the second must not be omitted. **It omitted the same line.** Note it
returns 2880×2880 for "4k", not 4096.

Two different models dropping the same sub-line points at composition, not text
rendering: the vial is specified at 30% of frame height, which leaves the label
sub-line only about ten pixels tall at delivery size. Both models render the plate
and drop what will not resolve. The fix is to enlarge the vial or drop the sub-line
from the label for this concept, not to keep escalating.

## Safe zones — measured in delivery pixels

1:1 (no platform UI in feed): both pass. Headline 7.8–17.3% and 9.7–16.5%, footer
93.2–96.4% and 93.8–96.7%, all type inside the 6% side margins.

9:16: **both takes breach, top and bottom.**

| | brief | take 1 | take 2 |
|---|---|---|---|
| headline first line, top | ≥14% | 9.9% | 9.4% |
| `peptideads.com` | ~79% | 88.8–91.0% | 90.2–92.4% |

The footer sits inside Reels' bottom-35% and Stories' bottom-20% UI zones again.

This ran **with** the hardened instruction added after job 1: an explicit pixel row
(1480–1530 of 1920), "the entire bottom fifth is empty", and three negative-list
entries including `no text below pixel row 1536`. None of it bound. Absolute
vertical placement is not steerable by prompt on this model — naming pixels is no
better than naming percentages.

The workable fix is compositional: move the footer out of the bottom of the frame
entirely and set it directly under the blue sub-headline in the upper third, where
type reliably lands. Recorded in CLAUDE.md.

## Cost

Balance 15,475.96 → 15,436.96 = **39 credits**: 16 for the four delivered takes at
4 each, 12 wasted on the flash mis-route at 3 each, 11 on the gpt_image_2 probe.

## Recommendation

Do not ship as-is. The square pair is one missing label line away from usable and
the vertical pair needs the footer relocated. Both are prompt fixes for a V2, not
reroll luck: enlarge the vial so the label sub-line can resolve, and move the
footer into the upper third for 9:16.
