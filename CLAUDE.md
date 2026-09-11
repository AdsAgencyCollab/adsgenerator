# Agency Collective — ad production

## How ad imagery is made — not negotiable

**Every ad image is generated with Higgsfield.** Vials, bottles, product shots,
scenes, backgrounds, the finished frame — all of it. Armin, 10 Sep 2026:
*"Every time that we're going to be creating ads, they must be with Higgsfield.
They must use the skills that we have in here to create them."*

Do **not**:
- draw product with Pillow, SVG, CSS or any code path — a drawn vial reads as
  drawn, and it has been rejected twice
- recolour a packshot lit for a white background and expect it to sit on black —
  clear glass keeps its interior wall and its base refraction, and that is the
  single biggest tell
- composite type over a scene assembled by hand when Higgsfield can render the
  whole frame in one pass

Real client packshots are still the right hero **on their own ground** — that is
what the Scientipeptides D2C wave uses, and it works because the shot and the
canvas share a light. That is the exception, not the default.

## Skills to load before making anything

| Skill | When |
|---|---|
| `ruo-creative-design` | before any concepting, art direction or critique |
| `ruo-ad-creative-research` | before writing peptide or supplement ad copy |
| `peptide-ads-client-vault` | anything about a client's state or assets |

## Method — Route B, single pass

`SHARED-PRODUCTION/S09` and the design skill agree: one master prompt per
(concept × ratio) renders the finished frame, type included.

1. Give **every string verbatim** in the prompt, element by element, with
   "render EXACTLY as written, letter by letter, no other words in the frame".
2. Spell out label microtext and **name every digit** — a 50 MG comes back 60 MG
   otherwise.
3. Carry an explicit **negative list**. It is always
   `no syringes, no needles, no hands` — that part is compliance, never relax it.
   Everything else on the list is **per-lane**, and getting it wrong is what
   produced the shampoo bottles (see *Vials* below).
4. `nano_banana_pro` at 4K for finals. **24 credits per image at 4K** — twelve
   times the 2K price, so budget from the real number.
5. Budget 1.5–2× the file count in generations; rerolls are expected.

## Vials — Armin, 11 Sep 2026

> *"We need the vials to look like actual peptide vials, these look like
> shampoo bottles lol."*

An earlier version of this file banned *clear glass, visible liquid, metallic
caps, crimp seals and paper-label edges* as a blanket rule. Those five things
are exactly what makes a peptide vial read as a peptide vial, so the rule was
generating cosmetics packaging. It also contradicted our own client: the
Scientipeptides `BRAND_PROFILE.md` palette lists **Steel `#C9CBC8` — Crimp
cap**. Their real SKU has a crimp cap.

**A peptide vial is short.** Total glass height is roughly **twice the body
diameter**. Anything taller than about 2.5× reads as a bottle or a test tube.
This is the single biggest tell and it is a proportion, not a finish.

Always prompt the full anatomy, bottom to top:

| Part | Why it matters |
|---|---|
| flat base, straight cylindrical body | — |
| defined **shoulder** narrowing to a short **neck** | straight tube = test tube |
| outward-flared glass **lip** | the crimp needs something to grip |
| ribbed **aluminium crimp seal**, skirt visible | the #1 recognition cue |
| coloured **flip-off cap** centred in the crimp | the #2 recognition cue |
| grey butyl **stopper** faint through the glass | sells the crimp as real |
| **lyophilized powder puck**, lower fifth only | a full bottle reads as shampoo |
| small label on the **middle third only** | full-height label = cosmetics |

Bare glass must be visible **above and below** the label.

Negative list for a vial: *no tall bottle, no shampoo or body-wash bottle, no
cosmetics or serum bottle, no test tube, no screw cap, no pump, no dropper, no
full-height label, no syringes, no needles, no hands.*

**Four vials, not six.** Measured over eight renders: the model honours the
2:1 proportion for one vial (2.19–2.45) but *stretches* it when packing a row
of six (mean 2.74 and 2.96, 0/6 and 1/6 under the 2.5 line) — even with
"do not stretch" in the negative list. At four it holds: **2.19, 2.19, 2.19,
2.18 — 4/4 passing, and identical to each other.** Six is the bug, not the
prompt. If more than four services must appear, run two ads, don't add vials.

**Verify proportion by measuring, not by eye.** Segment the vial against the
dark ground, take the bounding-box height over the 80th-percentile body width
in the lower half, and check it lands near 2.0. That number is the whole of
Armin's note, made checkable.

**Label text runs horizontally.** Tall vials were being drawn only to fit
vertical service names — the tail wagging the dog. A real vial carries its drug
name horizontally on a small band, so `META ADS` sits where the compound name
goes. That is the whole joke in the B2B set, and it only lands if the vial is
convincingly real.

## The retrieval limit — say it, don't work around it

This environment's egress policy blocks `cloudfront.net`, so results cannot be
pulled back into the container: they cannot be inspected, composited or
letter-checked here. `scientipeptides.com` is blocked too, so live-page claim
verification cannot run.

The result URLs are plain public links. **Hand them to the user and say plainly
that the letter-by-letter proof was not run.** Never imply an unproofed legal
line was checked.

## Lanes

| Advertiser | Lane | Rules |
|---|---|---|
| A client brand selling to consumers | **D2C** | `D00`–`D04`. RUO disclaimer mandatory, both the canvas constant and the short form. |
| Agency Collective selling its own offer | **B2B** | peptideads.com, telehealthads.com, agencycollective.ai. No RUO disclaimer; the agency's own claims apply. |

## Never
Cloaking, or anything that sells evasion — a permanent Business Manager ban and
a hard fail on both lanes. Invented discount codes. A claim that was not
verified against the live page this run.
