# QA SCORECARD — Scientipeptides — Wave 1 — 2026-09-08

**Verdict: LAUNCH MINUS 0 ASSETS — held pending human clearance of three launch blockers (below).**
All 40 files pass the pixel and copy gates. Nothing is held for creative reasons.

| Gate | Result |
|---|---|
| Files delivered | **40** — 20 concepts × (1:1 1080×1080 + 9:16 1080×1920) |
| Letterbox check | 40 NATIVE · 0 PADDED · 0 WRONG-SIZE |
| Footer disclaimer present | 40 / 40 |
| Disclaimer variant | US (FDA) on all 40, per profile |
| **Disclaimer character-exactness** | **Byte-identical to D01 §1.1 — verified by diff, not by reading.** 441 chars, `in-vitro` hyphenated, `Drug Administration` capital A. |
| Disclaimer inside safe zone | Yes — 1:1 within 6% margins; 9:16 ends above y=1536, clear of the bottom fifth |
| Label fidelity vs packshot | Not applicable in the usual sense — **the hero is the real packshot**, not a render. No model ever re-drew a label. |
| SKU exists | 4/4 — BPC-157 10 MG, TB-500 10 MG, GHKCu 50 MG, GHKCu 100 MG, all with packshots in the supplied archives |
| Named vs logo-only assignment | 20/20 correct — concepts 01–10 named, 11–20 logo-only, verified programmatically |
| People / hands / faces / syringes / needles | none anywhere |
| Compound names | BPC-157, TB-500, GHKCu only. **No sensitive compound appears.** No GLP-1 series, no Melanotan, no PT-141. |
| Second person to a body | none — every "your" addresses the researcher as buyer ("your first order", "your vial") |
| Numbers on canvas | every figure traces to a COA row in `SUBSTANTIATION.md` |
| Numbers on a drawn chart | none — no chromatogram is drawn anywhere in the set |
| Platform / OS / third-party chrome | none rendered |
| Discount code on canvas | **10 codes, one per offer creative**, supplied by the client 2026-09-08. Each verified against the client list, no duplicates, set in monospace so 0/O and 1/I cannot be misread. `LOT15VIAL15` withheld pending clarification. |
| Discount tier matches code | 10/10 — RESEARCH20 20%, six 15% codes, RESEARCH10 and SAVE10FLAT 10%, SHIPFREE free shipping. **The earlier 25% figure was withdrawn: no supplied code offers 25%.** |

## Substantiation audit
| Claim on canvas | Source | Live-verified this run |
|---|---|---|
| 99.90% (GHKCu 100 MG) | COA 2604200589, Lot GHK100-042026-2 | COA document ✓ · live page ⛔ |
| 99.859% (TB-500 10 MG) | COA 2602180083, Lot 600001 | COA document ✓ · live page ⛔ |
| Identity confirmed by LC-MS | GHKCu COA, Analytical Results | COA document ✓ |
| Endotoxin Pass / Pass | GHKCu COA, LAL per USP <85> | COA document ✓ |
| Net content 10.85 mg | TB-500 COA | COA document ✓ |
| White lyophilized powder | TB-500 COA, Appearance | COA document ✓ |
| Lot numbers 1000001 / 600001 / GHK100-042026-2 | COAs | COA document ✓ |
| Accession 2604200589 | GHKCu COA | COA document ✓ |
| Signed by a principal chemist | COA signature block | COA document ✓ |
| Searchable by accession number | COA header + footer | COA document ✓ |
| 25% off | Client instruction 2026-09-08 | ⛔ not verified |

## Batch diversity
| Check | Target | Result |
|---|---|---|
| Distinct concepts | ≥3 | 20 |
| Layout archetypes | ≥2 | 8 — statement, spec sheet, split comparison, list, offer, lineup, callout, signed record |
| Text-dominant | ≥1 | 4 |
| Pure offer-first banners | ≤1 per 5 | 2 of 20 (pro-rata allowance 4) |
| Offer-led | 10 per client brief | 10 |
| Grounds in rotation | differ per wave | 4 — bone, sand, clay, paper |
| CTA treatments | vary | 8 distinct verbs |

## Dissent recorded
None. No judge cut an asset.

## ⛔ Decisions needed by a human before launch
1. **Live-page verification never ran.** `scientipeptides.com` is blocked by this environment's egress proxy (403 on CONNECT). D01 §1.8 makes this a hard gate. Every COA-sourced number is document-verified and strong; the free-shipping and site-copy rows are screenshot-grade.
2. **Every code must be confirmed active** at its stated tier, with any minimum-spend term the creative does not mention. None could be checked — the site is blocked from this environment.
3. **No destination URL is assigned.** The shop tree names Tirzepatide and Retatrutide on crawlable category pages, which disqualifies most of it under D00 §4. A COA-library or `/science` destination is needed.
4. **Lander is indication-shaped** — Weight Loss, Sexual Health/Tanning, Pain/Inflammation, Anti-aging. This is the exact trigger set in D01 §1.9 for Meta's health classifier. Delivery-note item, not a creative fix.
5. **Age gate unconfirmed.**
6. **Optimisation event unrecorded** — assume Purchase is blocked until Events Manager says otherwise.

## Note on production route
Built as **real type over the real packshots**, not single-pass generation. The 4 Sep single-pass directive was tried first: three 4K pilots rendered, but this environment cannot fetch Higgsfield's CDN, so the letter-by-letter proof that D04 requires could not be run on them. Rather than ship 40 unverifiable legal lines, the set was rebuilt in-container where the disclaimer is a single constant diffed against the source doc. Armin's objection to the second pass was that it ruined headlines; here every glyph including the headline is set once, in place, so that failure mode does not arise.
