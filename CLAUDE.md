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
4. `nano_banana_pro` at 4K for finals. **4 credits per image at 4K.** An earlier
   version of this file said 24; that figure is wrong. Measured three times by
   balance delta — most recently 15,491.96 → 15,475.96 for a batch of four, i.e.
   16 credits for 4 images. Budget from 4, and confirm with `get_cost` preflight.
5. Budget 1.5–2× the file count in generations; rerolls are expected.
6. **Conform the ratio afterwards — nano_banana_pro does not honour it.** A
   "9:16" request returns 3072×5504 (0.5581, not 0.5625) and a "4:5" returns
   3712×4608 (0.8056, not 0.800). Centre-crop to the exact ratio, then LANCZOS
   down to the delivery size. 1:1 comes back square and needs no crop.
   **`gpt_image_2` is exact** — 2880×2880 and 2160×3840 (0.5625) — so a
   position-critical layout only needs a downscale. It costs 11 credits an image
   against nano_banana_pro's 4, and it is markedly better at dense typography:
   job 7 rendered a four-row three-column table with 19 strings, zero drift,
   across all four takes. Use it for tables and information artifacts; keep
   nano_banana_pro for photographic frames.
7. **Absolute vertical placement is not steerable by prompt. Compose around it.**
   Job 1 asked for a footer "at about 78% of the frame height" and got 86–91%.
   Job 2 hardened that to a named pixel row (1480–1530 of 1920), "the entire
   bottom fifth is empty", and `no text below pixel row 1536` in the negative
   list — and got 88–92%. Naming pixels is no better than naming percentages.
   On 9:16 the model pushes the lowest text toward the bottom edge, into Meta's
   Reels bottom-35% and Stories bottom-20% UI zones, every time. What does work
   is giving the composition a **physical object edge** to stop against — job 3's
   board ends at 88% with wall visible below it, and the footer moved to 74.8%.
   A cast shadow running to the frame edge is not an edge: job 6 tried exactly
   that and its CTA still landed at 85–89%. So either put a real object boundary
   across the lower frame with a different surface behind it, or set the footer
   directly under the headline block in the upper third. Job 7 confirms it: a
   card bottom edge at 78% plus a shelf at 80% put the footer at 66–70%.
   **The same trap exists at the top.** Job 7's card top edge sits at 10% and
   both verticals set the headline hard against the inside of it, at 11.2% and
   11.9%, inside Meta's Reels top-14% band, despite being told 15%. Fix it the
   same way: move the physical edge down to about 16% so type cannot start above
   it. Restating the percentage never works, at either end — job 8 added a deep
   bare-paper top margin plus `no text above 15 percent` in the negative list and
   still got 12.5%, so do not retry that.
   **Put every readable element ON the artifact, never on the ground beside it.**
   This is the sharpest form of the rule and it is four for four. Type printed on
   the object stays where it is put: job 3's board footer 74.8%, job 7's card
   footer 66–70%. Type placed on the floor or desk below the object migrates to
   the bottom edge: job 6's floor footer 91.8–94.1%, job 8's desk footer
   92.8–95.4%. Same model, same discipline, same briefed percentage — the only
   difference is whether the type had a surface to sit on.
   **A struck-through or rule-crossed line always fails a whole-page OCR pass.**
   Job 8's fifth row came back as `WANTS` + `LAIM IN THE AD`, and in one take not
   at all, because a red strike line cut the boxes. Band-crop the row and re-read
   at 3× before reporting: all four takes were in fact correct at 0.95–0.98. A row
   that reads as absent is not evidence it is absent when a rule crosses it. Then measure the OCR
   bounding boxes against the real safe-zone pixel lines before handing over.
8. **The model id you pass is `nano_banana_pro`; the id it stores is
   `nano_banana_2`.** Passing the stored id back is not rejected — it is silently
   swapped for `nano_banana_flash`, which is a different, cheaper model. Job 2
   lost 12 credits to this. `generate_image_batch` takes
   `{index, params:{model, prompt, aspect_ratio, resolution, input_images}}`;
   always read the `model` field back from `jobs_wait` on the first job before
   committing spend to a full set.
10. **Proof by the concatenated string, not the token list — and sort it first.**
   OCR breaks a line-wrapped phrase into one box per line, so `ONE PARTNER` comes
   back as `ONE` + `PARTNER` and reads as missing. Strip spaces and punctuation,
   join every token, then search. Sort the tokens into reading order (band the y
   centres, then order by x) *before* joining: unsorted, overlapping boxes and
   two-column layouts concatenate out of sequence and still read as missing. Jobs
   3, 5 and 6 threw six such false alarms between them.
10b. **Measure an ellipsis, never trust OCR on it.** At 1080 the reader merges the
   dots and returns `again..` for a correct `again...`. Segment the trailing blobs
   after the final letter and count equal-width runs instead. Job 6 read two dots
   on three of four takes; all four were right.
11. **A brief that bans product still carries the standing "attach the packshot"
   line.** It is boilerplate. Attaching a packshot to a no-product concept pushes
   the banned element into the frame. Read the HERO and NEGATIVE blocks before
   attaching anything, and say so when you drop it.
12. **What cannot be checked here must be said, every time.** Strings, spelling,
   counts, digits and y-positions are all machine-checkable through the sandbox.
   *No product in frame*, *no hands*, *no people* and anything else about what the
   picture looks like are not. Hand those to the user explicitly rather than
   letting a clean OCR report imply the whole ad was verified.

9. **A small hero drops its small type.** A vial at 30% of frame height leaves a
   label sub-line about ten pixels tall at 1080 delivery, and the model renders
   the plate and silently omits the line. `nano_banana_pro` and `gpt_image_2` at
   4k high both did it on job 2, so escalating models does not fix it. Either
   enlarge the hero until the sub-line can resolve, or take the sub-line off the
   label. Escalate only for a string that is *misspelled* twice; a string that is
   *missing* twice is a scale problem and escalation just spends credits.

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
| **empty glass — nothing inside** | Armin, 11 Sep: no powder, no liquid, nothing |
| small label on the **middle third only** | full-height label = cosmetics |

Bare glass must be visible **above and below** the label.

**The vial is empty.** Earlier renders put a lyophilized powder puck in the
bottom. Armin, 11 Sep 2026: *"without any powder inside, without anything
inside, just like the transparent file."* Clear empty glass, all the way
through. The grey stopper still shows in the neck — that is the closure, not
contents, and it is what sells the crimp as real. A sticker or label is fine;
nothing else is.

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
