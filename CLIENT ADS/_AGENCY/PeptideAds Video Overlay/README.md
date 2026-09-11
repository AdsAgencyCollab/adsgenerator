# PeptideAds — video overlay (Ads Manager table)

Transparent 1080×1920 PNG burned over the three live-action background
clips (boat / car / cycling). One overlay, three videos.

## What changed in v2

The v1 overlay ran from y=236 to y=1635. On Reels and Stories the bottom
35% of the frame is caption, CTA button and icon rail — so the last rows
of the table and the ROAS line were sitting underneath platform UI. That
is the clipping visible in the live ad.

v2 fixes three things:

1. **Safe zones.** Every readable element is inside the Meta Reels
   reserve — the strictest placement these run in, and a superset of
   Stories. Measured on the built file: ink bbox `x 80–1000, y 292–1228`
   against a safe box of `x 64–1016, y 268–1248`. Also clears a 4:5
   centre crop. It does *not* clear a 1:1 centre crop (that would need
   y ≥ 420), which is the one placement to avoid.

2. **Branding.** A PeptideAds lockup on a white pill, centred, overlapping
   the table's top edge — brand in the first frame, and the single element
   allowed to break the grid.

3. **The footage reads.** Opaque coverage is down from 45.7% of the frame
   to 31.4%: table narrowed 1012 → 920, chrome collapsed to one row,
   row height 96 → 72, and a clear band top and bottom.

| | v1 | v2 |
|---|---|---|
| opaque coverage | 45.65% | 31.40% |
| ink bbox (y) | 236 – 1635 | 292 – 1228 |
| inside Reels safe | no | yes |
| inside 4:5 crop | no | yes |
| PeptideAds lockup | — | yes |

## Meta safe zones used (1080×1920)

| Placement | Top | Bottom | Sides |
|---|---|---|---|
| Reels | 14% = 268 | 35% = 1248 | 6% = 64 |
| Stories | 14% | 20% | 6% |
| Feed | 0 | 0 | 0 |

## The data

Every figure is transcribed from the client's own Ads Manager screenshot
and lives in one place (`table.py`), imported by the overlay builder so
the two cannot drift. Nothing in the table is generated — a generated
table invents digits.

## Open

The table header reads `Mar 1, 2026 – Apr 18, 2026` (48 days) while the
headline reads `in 18 days`. Both strings came off the client screenshot;
neither has been changed. Needs a decision before this scales.
