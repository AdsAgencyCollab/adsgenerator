# Peptide Ads | Consolidation | 23 Sep — render job 1 of 5

**Concept:** Consolidation | Static | One Partner Every Channel | V1
**Method:** Route B single pass per `SHARED-PRODUCTION/S09`. Two takes per ratio,
same prompt, one batch. `nano_banana_pro` (nano_banana_2) at 4k.
**Reference:** packshot job `435b8aac-ca66-4af7-a265-05bfcd0fb75e` attached as
`image_references` on all four. The local `~/Downloads/...` path was not reachable
from the container; this is the identical render already in Higgsfield storage.

Two points where the brief overrides the reference, stated explicitly in each
prompt: the reference has a **royal blue cap** (brief requires glossy deep-black)
and its labels read `META ADS / GOOGLE ADS / EMAIL / CREATIVE` (brief requires the
Peptide·Ads plate plus `For Peptide Brands Only`).

## Jobs

| # | Ratio | job_id | master |
|---|---|---|---|
| 1 | 1:1  | `f87c19bf-9b38-44ce-b168-e5650666e6db` | 4096×4096 |
| 2 | 1:1  | `265d1fa1-3dac-4fdd-8d8d-901bb27161c7` | 4096×4096 |
| 3 | 9:16 | `00364277-a285-4178-bc34-f2205069210a` | 3072×5504 |
| 4 | 9:16 | `4f36b8c0-3af0-45d3-952a-09ad102918dd` | 3072×5504 |

**Cost:** 16 credits for the batch, 4 per image at 4k. Balance 15,491.96 → 15,475.96.
No `gpt_image_2` escalation — no string misspelled in both takes of either ratio.

## Conform

1:1 masters are exactly 1.0000 and were resampled to 1080×1080.
9:16 masters came back 0.5581, not 0.5625. Centre-cropped 3072×5504 → 3072×5461
(0.562534, 43px of height removed, 21 top / 22 bottom, 0.78% of the frame, no type
near either edge) then LANCZOS to 1080×1920 = 0.5625 exactly.

## Letter-by-letter read-back — delivered 1080 files, RapidOCR at 2×

All eleven approved strings present and correct in all four takes. Zero drift.

`ONE PARTNER.` · `EVERY CHANNEL YOU RUN.` · `META ADS` · `TIKTOK ADS` ·
`CREATIVE` · `EMAIL` · `CRO` · `Peptide` · `Ads` · `For Peptide Brands Only` ·
`peptideads.com`

No unapproved strings. **No numerals anywhere in any take** — the digit scan
returns empty for all four. No duplicated callouts. Strongly-blue pixels in the
cap region 0.00% in all four, so the glossy deep-black cap held against a blue-cap
reference.

## Defects found — 9:16 only

Both vertical takes place the footer far lower than the brief's 78%:

| | brief | take 1 | take 2 |
|---|---|---|---|
| `peptideads.com` | ~78% | **86.3–88.5%** | **88.9–91.1%** |

That is inside Meta's Reels bottom-35% zone (from y 1248) and inside the Stories
bottom-20% zone (from y 1536). The footer will sit under platform UI in both
placements. Take 1 also breaks the headline onto three lines rather than two, and
its first line starts at 10.05% — above the 14% top-safe line.

Take 2 is the better vertical: headline on two lines starting at 14.84%, callouts
41–62%. Only its footer is out of zone.

Both 1:1 takes pass — no UI overlay in feed, type inside 6% side margins, footer
at 93.5–96.8% with nothing to collide with.

## Recommendation

Ship the 1:1 pair. Re-render the 9:16 pair with the footer pinned hard — name the
pixel row, not a percentage, and add `no text below 74% of the frame height` to
the negative list. The type-position failure is a placement bug, not a spelling
one, so an instruction edit on take 2 would be cheaper than a fresh pass.
