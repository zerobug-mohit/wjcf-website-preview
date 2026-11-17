# WJCF website preview

The WJCF website as it stands, published here so it can be opened and reviewed
in a browser.

**This is the site's real build, but not the live site.** These files are what
the production project's Vite build produces, with links made relative so the
page works at this address. Nothing here is edited by hand. Each update
replaces the whole build.

## Looking at it

Open the GitHub Pages link on the repository's **About** panel. To run it
locally, serve the repository root with any static server:

```bash
python -m http.server 8000
# then open http://127.0.0.1:8000/
```

Opening `index.html` straight off the disk does not work, because browsers
block the page's script there.

## What to look at

The site is **one page**. Everything is on the long scroll: About, Our Work,
Impact, Resources and Get Involved, each a part with its own chapters.

Two things behave differently depending on the width of your window:

- **Above 1040px** the five parts sit in the header as tabs.
- **Below 1040px** the tabs are replaced by a single gold control. Pressing it
  floods the screen with navy from under your finger, and the menu's
  destinations are revealed by the edge of that ink passing over them.

Narrow the window past 1040px, or open it on a phone, to see it.

## What is not finished

- **Copy is the client's current text**, not final editorial.
- **Ms Chakraborty's photograph** was cropped tighter than the rest of the
  set, so her shoulders are continued past its edges to frame her like
  everyone else. An uncropped original would replace that.

## Contents

```
index.html       the page
assets/build/    its stylesheet, script and fonts, named by content
assets/          photographs, portraits, brand marks, the annual report
.nojekyll        serves the files exactly as they are
```

---

Internal preview. Not for distribution.
