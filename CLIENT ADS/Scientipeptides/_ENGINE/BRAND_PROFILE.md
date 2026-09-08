# BRAND_PROFILE — Scientipeptides

*Lane: D2C — client brand · Vertical: RUO peptides · Created 2026-09-08*

## Identity
| Field | Value |
|---|---|
| Brand | Scientipeptides |
| Wordmark | `Scientipeptides` — "Scienti" regular, "peptides" bold, one word |
| Descriptor | `An American peptides company.` (verbatim, with the full stop) |
| Domain | scientipeptides.com |
| Market / Disclaimer variant | **US (FDA)** |
| KPI | Purchase / ROAS |
| Optimisation event | ⚠ **UNSET — must be recorded before launch.** D01 §1.9: a health-classified domain often has Purchase/AddToCart blocked. Site categories are indication-shaped, so assume classified until Events Manager says otherwise. |

## Voice card
Plain, declarative, specification-grade. States what was measured and by whom.
Never persuades about an outcome. Short sentences. No exclamation, no hype
adjectives, no superlatives. The register of a lab report that happens to be
well designed.

## Palette (sampled off the real packshots + site)
| Role | Hex | Use |
|---|---|---|
| Signal orange | `#E8532B` | Brand accent, CTA chips, wordmark dot |
| Terracotta | `#C0472A` | BPC-157 / TB-500 label ground |
| Camel | `#B79372` | GHKCu label ground |
| Deep brown | `#4A2E15` | GHKCu label type |
| Warm off-white | `#F5F3EF` | Light world ground |
| Near-black | `#131211` | Dark world ground |
| Steel | `#C9CBC8` | Crimp cap |

Type: geometric grotesque, tight caps for headlines; the label's own face is a
humanist sans. No serif anywhere.

## SKU table — character-verified off the flat die-lines (Product visual C)
| SKU on canvas | Label ground | Strength chip | Packshot | COA | Lot |
|---|---|---|---|---|---|
| `BPC-157` | terracotta | `10 MG` | Pain and Inflammation/Product visual A - BPC 157.jpg | 2602180085 | 1000001 |
| `TB-500` | terracotta | `10 MG` | Pain and Inflammation/Product visual A - TB-500.jpg | 2602180083 | 600001 |
| `GHKCu` | camel | `50 MG` | Skin Health/Product visual A - GHKCu 50mg.jpg | — | — |
| `GHKCu` | camel | `100 MG` | Skin Health/Product visual A - GHKCu 100mg.jpg | 2604200589 | GHK100-042026-2 |

**Label string, exact, every SKU** (top to bottom on the wrap):
`.ᖭ.Scientipeptides` (logo mark + wordmark) · `<COMPOUND>` · `<NN> MG` in a
rounded outline chip · a horizontal rule · `RUO` in a rounded outline chip +
`Research use only.` · a dark rounded square holding a flask glyph, butted to a
white pill reading `99%` + `PURITY` in a rounded outline chip. Right-hand white
panel: `COA` in a circle, a `CE` mark, and rotated 90°:
`Scientipeptides™` / `An American peptides company.` / `scientipeptides.com`
(the URL in signal orange).

⚠ The vial reads **`GHKCu`** — one word, no hyphen, capital C, lowercase u.
The COA writes it `GHK-Cu`. **Canvas follows the vial.**

## Restricted SKUs — never build creative around
Tirzepatide (GLP-2), Retatrutide (GLP-3), HCG, SLU-PP-322/332, 5-Amino-1MQ,
Glow, Klow, Wolverine Stack, Melanotan, PT-141. D01 §1.3 sensitive list plus
everything in the Weight Loss folder. **This wave uses none of them.**

## Compound naming — profile override, this wave only
D01 §1.3 sets compound names **off by default** and calls naming any compound a
soft flag. The client has explicitly commissioned 10 named-vial creatives on
BPC-157, TB-500 and GHKCu (2026-09-08). None is on the sensitive list, so this
is a **profile-level allowance, not a gate breach** — recorded here so the
judge does not read it as drift. The other 10 carry no compound name at all.

## Ban list (this brand)
Everything in D01 §6, plus: `GOLD standard`, `5 Star Rated By Scientists`,
`Made in the USA` (of the product — unresolved, D00 §7), any discount code
(none issued), any purity figure drawn onto an illustrative trace.

## Live offer
| Field | Value |
|---|---|
| Offer | 25% off |
| Code | **NONE ISSUED** — client decision 2026-09-08: run code-free |
| On-canvas treatment | `25% OFF` + `APPLIED AT CHECKOUT`. No code string anywhere. |
| Runs until | ⚠ unset — no end date on canvas, per D01 §1.5 (no fabricated deadline) |
| Destination | ⚠ **unset — see blockers** |

## Open blockers — a human must clear these before launch
1. **Live-page verification never ran.** `scientipeptides.com` is blocked by
   this environment's egress proxy (403 on CONNECT). D01 §1.8 / D04 §1 make
   this a ⛔ gate. Rows S16–S18 in `SUBSTANTIATION.md` are screenshot-grade,
   not live-grade.
2. **Destination URL unassigned.** D00 §4 forbids a PDP and forbids any page
   naming a flagged SKU. The site's `/shop?cat=weight-loss` and
   `/shop?cat=sexual-health-tanning` categories name Tirzepatide and
   Retatrutide, so most of the shop tree is disqualified. A COA-library or
   `/science` destination is needed.
3. **Lander is indication-shaped.** Categories read Pain/Inflammation, Weight
   Loss, Sexual Health/Tanning, Anti-aging, Brain Health, Immune System — the
   precise trigger set in D01 §1.9 for Meta's health auto-classifier. This is a
   delivery-note item, not a creative fix.
4. **Age gate unconfirmed** (D01 §1.8 requires one before browsing).
5. **Optimisation event unrecorded.**
6. **NAD+ has no packshot** — dropped from this wave by client decision.

## Run config
`offer_led_concepts: 10 of 20` (client instruction — half) ·
`unanimity: yes` (first set for this brand, D04 §0) ·
`cadence: unset`
