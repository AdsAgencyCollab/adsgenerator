# PeptideAds — video overlay (v3, real screenshot)

## The rule

**The Ads Manager table is the client's own screenshot, composited verbatim.
It is never redrawn.**

v1 and v2 rebuilt the table as type because the screenshot was only visible
to the assistant, not readable as a file. That was the wrong trade. A
redrawn UI always carries tells — in v2 the "Breakdown" button overlapped
the date range, the row separators were invented, the typeface was not
Meta's — and a results table that reads as generated destroys the one thing
the ad is selling. Accuracy of the digits does not rescue it.

The fix: the screenshot is uploaded into Higgsfield storage (upload widget),
which the render sandbox can read, and ffmpeg pastes those pixels.

## Composition

Three layers sandwich the untouched screenshot:

    video -> PA_shadow_layer.png -> screenshot (920x664 @ 80,356) -> PA_type_layer.png

- `PA_shadow_layer.png` — blurred drop shadow, its own footprint punched
  out so it only rims the screenshot and never tints it
- the screenshot — scaled 1124x812 -> 920x664 (lanczos, 0.8185x, aspect
  preserved), nothing else touched
- `PA_type_layer.png` — PeptideAds lockup + headline + ROAS line only. No
  table, no chrome, no separators.

Regenerate the two layers with `_build/overlay/overlay_v3.py <shot_w> <shot_h>`.

## Meta safe zones (1080x1920)

| Placement | Top | Bottom | Sides |
|---|---|---|---|
| Reels | 14% = 268 | 35% = 1248 | 6% = 64 |
| Stories | 14% | 20% | 6% |
| Feed | 0 | 0 | 0 |

Built result: ink bbox `x 80-1000, y 292-1237` inside a safe box of
`x 64-1016, y 268-1248`. Clears a 4:5 centre crop. Does **not** clear a 1:1
centre crop (needs y >= 420) — avoid that placement or build it separately.

## Verification

The paste is checked numerically, not by eye: the 920x664 region at (80,356)
of each output frame is diffed against the lanczos-scaled original.

    mean |paste - original| = 2.12/255 across all three clips, at 0.5s / 5s / 9.5s

That residual is H.264 quantisation on fine text edges, and it is identical
frame to frame — i.e. the region is a static paste, not a re-render.

## Open

The table header reads `Mar 1, 2026 - Apr 18, 2026` (48 days) while the
headline reads `in 18 days`. Both came from the client. Needs a decision.
