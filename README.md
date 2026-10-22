# WJCF — website design preview

A static preview of the WJCF website design, published here so it can be
opened and reviewed in a browser before the production build begins.

**This is a preview, not the product.** It is a single pre-rendered HTML page
with its images beside it. There is no build step, no framework and no
dependencies — the repository is exactly what the browser receives. The real
site will be rebuilt as a Vite project; this exists so the design can be
agreed first.

## Looking at it

Open the GitHub Pages URL on the repository's **About** panel, or run it
locally — any static server from the repository root will do:

```bash
python -m http.server 8000
# then open http://127.0.0.1:8000/
```

Opening `index.html` directly off the filesystem also works.

## What to look at

The site is **one page**. Everything is on the long scroll: About, Our Work,
Impact, Resources and Get Involved, each a part with its own chapters.

Two things behave differently depending on the width of your window:

- **Above 1040px** the five parts sit in the header as tabs.
- **Below 1040px** the tabs are replaced by a single gold control. Pressing it
  floods the screen with navy from under your finger, and the menu's
  destinations are revealed by the edge of that ink passing over them. The
  masthead is painted by the same circle, so the whole header and page flood
  as one sheet.

Narrow the window past 1040px, or open it on a phone, to see it.

## What is not finished

- **Two of the nine portraits are missing.** Dr. Aggarwal and Ms. Chakraborty
  show a square with their initials. That is deliberate: it says a photograph
  has not arrived, rather than showing someone else's face.
- **Copy is the client's current text**, not final editorial.

## Contents

```
index.html     the whole page: markup, styles and script in one file
_assets/       photographs, brand marks, the annual report PDF
.nojekyll      stops GitHub Pages hiding _assets (Jekyll drops _ folders)
```

---

Internal preview. Not for distribution.
