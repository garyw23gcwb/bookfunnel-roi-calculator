# Book Funnel ROI Calculator

Interactive calculator for bookfunnels.io. A prospect enters their own numbers
and sees how ad spend turns into book sales, recurring revenue, and high ticket
clients. Every dashed number is editable and everything else recalculates.

## Files

| File | What it is |
| --- | --- |
| `build/index.html` | Deployable page. Fonts load from Google Fonts, logos inlined. 82 KB. |
| `bookfunnel-roi-calculator.html` | Fully self-contained copy (fonts inlined). 241 KB. For the Claude artifact and offline use. |
| `template-no-fonts.html` | Source template with `__G4_B64__` style placeholders. **Edit this one.** |
| `assets/` | Logo PNGs and the original `.ai` source. |

## Editing

Make changes in `template-no-fonts.html`, then rebuild both outputs. The
placeholders are replaced with base64 of the font and logo files; `build/index.html`
additionally strips the three `@font-face` blocks and swaps in a Google Fonts link,
which is what takes it from 241 KB down to 82 KB.

## Deploying to bookfunnels.io/roi

The domain lives in HighLevel, so the page is hosted separately and embedded.

1. Push this repo to GitHub (public: GitHub Pages needs it on the free plan).
2. Settings, Pages, deploy from `main` branch, `/build` folder. The page lands at
   `https://<user>.github.io/bookfunnel-roi-calculator/`.
3. In HighLevel, build a page at `/roi` with a single full-width Custom Code element
   holding a responsive iframe pointing at the Pages URL.

The calculator sizes itself to the viewport, so give the iframe a generous fixed
height (around 1100px desktop) or post the document height up to the parent.

## The model

Ad spend is the anchor. Clicks are ad spend divided by cost per click, book sales
are a percentage of clicks, and every downstream figure follows. Editing any
derived number back-solves ad spend, so the calculator works in both directions.

Person counts round to whole numbers and revenue is derived from the rounded
counts, so it never shows a fractional client.

Defaults: $5,000 ad spend, $4.00 CPC, 10% book conversion, $21 book, 30% bump
upgrade at $37, 10% one-click offer at $97, 10% join MRR at $97, 10% apply,
33% close, $5,000 high ticket price.
