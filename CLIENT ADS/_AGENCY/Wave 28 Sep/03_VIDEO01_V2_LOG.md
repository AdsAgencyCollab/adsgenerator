# Wave 28 Sep — Video 1 v2, "The Learning Curve" (rebuild)

V1 was rejected as too boring. This log records what was actually wrong, a
measurement mistake made while diagnosing it, and the pipeline that replaced it.

**Delivered:** 1080×1920, 15.21 s, 24 fps, AAC, burned captions.
`https://d2ol7oe51mr4n9.cloudfront.net/user_33uTwjMVb5NBs9hREmEUJfVFSFg/36cb7b43-631a-485c-8bd4-884648f16d5d.mp4`

## A measurement trap worth writing down

`showinfo` logs at ffmpeg's **info** level, so a scene-detection command written
as `ffmpeg -v error -i f.mp4 -vf "select='gt(scene,0.3)',showinfo" -f null -`
prints **nothing at all** and reads as *zero cuts* no matter what the file
contains. Measured that way, v2's first attempt appeared to have zero cuts at
every threshold down to 0.05, and the conclusion drawn — that Seedance will not
cut at all — was wrong.

Re-run with `-loglevel info`, the same file has five scene changes at threshold
0.30: **4.12, 4.96, 5.00, 5.92, 12.54**.

So the model does cut. What it will not do is cut *where it is told*. Eight cuts
were briefed, timed to the frame and named (WHIP-PAN, IMPACT, GLITCH, CUT TO
BLACK); five arrived, four of them bunched between 4.1 s and 5.9 s, and then the
picture sat still from **5.92 to 12.54 — a 6.6-second hold in the middle of a
fifteen-second ad.** That hold is what read as boring, and no amount of prompt
language moved it.

**Always pass `-loglevel info` when reading `showinfo`.** A silent scene-detect
command is the failure mode that looks most like a finding.

## What replaced it

Cut placement is not steerable inside a single generation, so it was taken out
of the model's hands: **each beat is its own generation, and the cuts are made in
ffmpeg**, where they are guaranteed rather than requested.

| Step | What ran | Credits |
|---|---|---|
| Boards ×2 | `gpt_image_2` 21:9 2k high, branded label | ~22 |
| Beats ×7 | `seedance_2_5` `omni_reference` 9:16 1080p 4 s, audio OFF | 336 |
| Voice | lifted from the rejected 15 s render — same script, already paid | 0 |
| Edit | ffmpeg: 7 hard cuts, 2-frame white flashes, 3-frame black at the turn | 0 |
| Captions | `transcribe_words` → `group_captions` → `make_captions` → burn | 0 |

Seven beats over 15.21 s is a mean shot length of **2.17 s**, against a 6.6 s
dead hold in v1. Cuts verified on the delivered file at threshold 0.30:
**1.92, 2.00, 2.75, 5.17, 9.33, 9.42, 12.42**.

The cut at 9.30 did not register on its own — beats 5 and 6 are both *vial in a
beam on black* and the detector read them as one shot. A 2-frame white flash was
added on that cut so it reads as a cut to the eye as well as to the meter. The
3-frame hard black at 7.20 is the PAS turn: problem stops, fix begins.

## Structure

| # | Beat | In | Out | Line |
|---|---|---|---|---|
| 1 | vial slams down, shockwave | 0.00 | 1.90 | *Your ad account got killed.* |
| 2 | four vials topple like dominoes | 1.90 | 2.70 | *Again.* |
| 3 | blizzard of blank paper buries it | 2.70 | 5.10 | *…still learning your category.* |
| 4 | vial falls through darkness | 5.10 | 7.20 | *On your budget. On your calendar.* |
| 5 | slams down into one hard beam | 7.20 | 9.30 | *Here's the fix. One team.* |
| 6 | rises into warm light | 9.30 | 12.30 | *One category. Nothing else.* |
| 7 | hero push-in | 12.30 | 15.21 | *Sixty plus peptide brands. Book the call.* |

## The label

Armin, 28 Sep: the vial must carry the real mark — `PeptideAds` with *Peptide*
black and *Ads* blue, `For Peptide Brands Only` beneath. The first pair of boards
had been rendered with a deliberately **blank** label, because a blank surface is
the standing defence against the CJK contamination in rule 10c. They were
re-rendered with the wordmark spelled letter by letter and the ban on non-Latin
glyphs kept.

OCR over all eight board panels, each cropped and re-read at 3×:

| Board | Panel | `PeptideAds` | `For Peptide Brands Only` |
|---|---|---|---|
| C | 1 | 0.98 | 0.99 |
| C | 2 | 0.97 | **dropped** |
| C | 3 | 0.98 | 0.99 |
| C | 4 | 0.98 | 0.98 |
| D | 1 | 0.99 | 0.99 |
| D | 2 | 0.99 | 0.99 |
| D | 3 | 0.99 | 1.00 |
| D | 4 | 0.98 | 0.99 |

Eight of eight carry the wordmark, seven of eight the sub-line. The one that
drops it is C2, four vials in one panel — each vial is small, and **rule 9
predicts exactly this**. It is a 0.8-second chaos beat, so it was left rather
than re-rendered; escalating the model does not fix a scale problem.

## QA on the delivered file

- **30 frames sampled at 2 fps.** `PeptideAds` reads on **26 of 30**. The four
  misses are the inserted flash/black frames and the fastest motion frames.
- **No non-Latin glyphs anywhere.** No fullwidth, no CJK, no Cyrillic.
- **No text on screen that is not the label or a caption.** Every other string
  OCR returned (`PeptideA`, `PeptideAd`, `Aas`, `de Brandh`) is a partial read of
  the same wordmark mid-motion, confirmed by re-reading the band.
- **Voiceover transcribes word for word against the authored script.** All 39
  words, `[QA] ok — every caption word is in the script`. 27 caption groups.
- **Captions clear every Meta safe zone**, measured by burning the subtitle track
  over black and OCR-ing the result: y 1163–1213, x 377–705. Clear of Reels
  top-14 % (269), Reels bottom-35 % (1248), Stories bottom-20 % (1536) and the
  6 % side gutters (65–1015). marginV had to go to 700; the 430 first tried sat
  at y 1432–1484, inside the Reels bottom band.

**Numbers stay words.** The voiceover says *sixty plus peptide brands*; the
transcriber normalises it to `60`, which is patched back to the word form before
grouping — otherwise `group_captions.py` exits 3 and a numeral lands on canvas.

## Not machine-checkable

Whether the vial is one consistent vial across seven separately generated clips,
whether the label survives the fast beats to a human eye, whether the cuts land
on the beat, and whether anything banned leaked into a frame between the sampled
half-seconds. **Eyes on the file before this runs anywhere.**

## Spend note

Balance fell 1,642.92 → 964.92 across this rebuild, 678 credits. This session
accounts for roughly 560 of that (180 + ~22 + 336, plus preflights). The
remainder is **Nano Banana Pro charges this session never made** — twenty of
them at 4 credits each, timestamped 19:03, 19:06 and 19:15 while this work was
uploading. Something else on the account is generating. Worth checking alongside
the earlier unexplained drop.
