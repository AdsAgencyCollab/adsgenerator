# Wave 28 Sep — 15 statics, QA record

Rendered 1:1 at 4k. Six photographic on `nano_banana_pro` (4 cr), nine
typographic on `gpt_image_2` 4k high (11 cr). Four re-rolled after the first
proof pass. Masters are exact squares on both models, so no crop was needed.

## Result

**Fourteen clean. One needs a human glance.** Every approved string present, no
unapproved strings, no numerals outside the claim bank, no non-Latin characters
after the re-rolls.

| # | Format | job_id | verdict |
|---|---|---|---|
| 01 | breaking news | `e9428988-865a-47c3-82f8-22770d959788` | clean (re-roll) |
| 02 | side effect | `542e310f-ac36-454d-beb7-7a3e6341d1ae` | clean |
| 03 | warning | `79f561c3-1e2c-4a29-9eff-108e59892f46` | clean |
| 04 | emergency | `34182d53-d827-4421-9b99-c9e3e4f940e3` | clean |
| 05 | claymation | `ab0e1d77-0670-40a4-a503-0fa931690863` | clean (re-roll) |
| 06 | doodle | `4ec4145c-b79c-4c71-a0ba-b7ef23255a65` | clean |
| 07 | native billboard | `1e5bcaab-e5df-4c45-8a48-94834ee796f2` | clean |
| 08 | iphone notes | `d3286af0-8998-476b-af11-a6fe31010903` | clean |
| 09 | google search | `8a23c8ca-385e-4ba7-9d5a-718bc0b20f1b` | clean |
| 10 | reddit style | `97a096fc-b8b0-484f-9515-8311b0e1dcb0` | clean |
| 11 | text message | `2f3ac100-9f4e-41fd-9202-fe973b909d61` | clean |
| 12 | myth vs fact | `59beed7e-bdfe-4807-8262-f2b467087f5d` | clean |
| 13 | three signs | `de91efae-2ca7-48c3-a446-d92a03dd9d8f` | clean |
| 14 | stat headline | `7ce2f4c6-3d10-47c1-ae37-69595d1059f1` | figure needs an eye |
| 15 | venn diagram | `67fa4a5c-1350-40da-9b5b-2272260049d5` | clean (re-roll) |

## The four defects found and fixed

**01 breaking news — foreign characters and stray digits.** Asking for
"unreadable fine grey body text" as page texture produced real glyphs, including
Chinese characters and the strings `988` and `电：188`. Numerals on canvas that
are not in the claim bank, in an ad about compliance. Fixed by deleting the body
copy entirely: the lower two thirds of the page is now specified as blank
unprinted newsprint, plus an explicit ban on non-Latin characters.

**05 claymation — a whole line missing.** `META ADS. TIKTOK ADS. CREATIVE.
EMAIL. CRO.` did not render. Forty-three characters is too much to sculpt in
clay at legible size. Fixed by shortening it to `ONE TEAM. EVERY CHANNEL.`,
which rendered cleanly. **A hand-made lettering style has a character budget;
a long string silently disappears rather than rendering badly.**

**15 venn — corrupted glyphs and broken case.** The footer came back as
fullwidth CJK-style characters (`ｐeｐｔｉdｅａds.ｃom`) and the sub-line rendered
as `MOst aGenCies PiCK A SIde.` Fixed by moving all type onto a card rather than
bare dark ground, specifying FULL CAPITALS explicitly, and banning fullwidth and
non-Latin glyphs.

**14 stat headline — still unresolved, but probably fine.** `60+` reads as
missing on both the original and the re-roll. It is almost certainly present:
the briefed figure band is **46.9% bright pixels** with a peak row density of
0.71, and the `+` reads cleanly at 0.93 confidence. There is a very large white
figure there. RapidOCR cannot parse a glyph that fills most of its crop.

**This is the mirror of the job 2 finding.** There, a label sub-line at ten
pixels tall was too small to render at all. Here a display figure is too large
to read. **OCR fails at both ends of the size range and both failures look
identical in the report — a missing string.** Someone should open concept 14 and
confirm the figure reads `60+` and not `6O+` or `60`.

## New rule earned

Add to the negative list on every render from now on: *no Chinese characters, no
Japanese characters, no Cyrillic, no fullwidth glyphs, no characters outside the
basic English Latin alphabet.* Two of fifteen came back with CJK contamination,
both in places where the prompt asked for texture or small type. It is cheap to
prevent and expensive to miss on a compliance-sensitive account.

## Not machine-checkable

No image was looked at. Composition, whether the clay reads as clay, whether the
billboard reads as a real street, whether the vial overlaps any lettering, and
the shape of the `60+` figure all need a human eye.
