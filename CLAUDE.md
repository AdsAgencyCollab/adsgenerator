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
3. Carry an explicit **negative list**. For product bottles that means: no clear
   glass, no visible liquid, no silver or metallic cap, no crimp seal, no paper
   label or label edge, no syringes, no needles, no hands.
4. `nano_banana_pro` at 4K for finals. **24 credits per image at 4K** — twelve
   times the 2K price, so budget from the real number.
5. Budget 1.5–2× the file count in generations; rerolls are expected.

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
