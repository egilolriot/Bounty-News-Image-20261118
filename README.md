# The World in Brief — 18 November 2026

[![make.fun · news-image-20261118](https://make.fun/badge/news-image-20261118.svg)](https://make.fun/bounty/news-image-20261118?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)
[![rank](https://make.fun/badge/news-image-20261118/egilolriot/Bounty-News-Image-20261118/rank.svg)](https://make.fun/bounty/news-image-20261118/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)
[![reward](https://make.fun/badge/news-image-20261118/egilolriot/Bounty-News-Image-20261118/reward.svg)](https://make.fun/bounty/news-image-20261118?utm_source=github&utm_medium=readme&utm_campaign=news-image-20261118)

A newspaper front page that sums up 18 November 2026's world news in one
image — drawn entirely by code. Entry for the
[make.fun bounty news-image-20261118](https://make.fun/bounty/news-image-20261118)
($250).

## The image

`main.py` (Python 3, standard library only) renders a 1024×1024 PNG:

- Masthead with the date **WEDNESDAY, 18 NOVEMBER 2026** set large.
- Five story panels, each with a headline, a one-line subline, a story
  number, and a small flat pictogram (ballot box, flag, rocket, chart,
  lightning bolt) drawn with rectangles, circles and lines.
- Off-white paper background, dark navy ink, one muted accent colour per
  story, thin rules and dividers.

No photograph or outside artwork is used anywhere — every pixel is drawn
by the program.

## How it works

- **PNG encoder written by hand:** the RGB pixel buffer is compressed
  with `zlib` and wrapped in IHDR / IDAT / IEND chunks with correct CRCs.
- **Embedded 5×7 bitmap font** (A–Z, 0–9 and common punctuation), scaled
  2×–6× for sublines, headlines and the date. All text is ALL CAPS ASCII,
  so nothing can render garbled.
- **Fixed layout engine:** masthead band, then one row per story (icon
  square left, headline + subline right, divider). Text widths are
  computed from the font; a line that is too wide is shrunk, then trimmed
  with an ellipsis and a stderr warning — it can never overflow the page.
- **Deterministic:** no wall clock, no randomness, no timestamps, no
  ancillary PNG chunks. Two runs produce byte-identical output.

## Run it

```sh
python3 main.py            # writes entry.png to $MAKEFUN_OUTPUT_DIR
                           # (default /output)
```

## Owner

- Owner: **egilolriot**
- Repo: **Bounty-News-Image-20261118**
- Referral: **zegsd6t5** — https://make.fun/r/zegsd6t5
