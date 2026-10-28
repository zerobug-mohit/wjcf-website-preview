# WJCF — the same design as a multi-page site

The approved direction is one long scroll. This is that same design as a
conventional website: a page per part, a navigation bar with menus, and a rail
at the foot of every page carrying the reader to the next one.

**Nothing about the design was redecided.** Every colour, type size, band,
photograph, motion rule and component here is the approved one, read straight
out of the production build at build time rather than copied. Rebuild this
after any change to the real site and it picks that change up.

Open `index.html`. No server is needed.

---

## The seventeen pages

| | |
|---|---|
| `index.html` | Home. The cover, who WJCF is in one paragraph and three figures, the eight portfolios, two proofs, the partners. Each band ends by pointing somewhere. |
| `about.html` | Our story, Why we exist, How we work, Our journey, Values. The five chapters that already sat under About. |
| `work.html` | The eight portfolios. |
| `work-*.html` | A page for each portfolio: the challenge, the approach in four moves, the results. Eight of them. |
| `impact.html` | Featured work, and the scale figures. |
| `resources.html` | Regulatory information and reports. |
| `partners.html` `team.html` `careers.html` `contact.html` | The four chapters of Get Involved, one page each. |

## Where the split came from

It was not invented. Every band in the approved page already carries a
`data-tab` saying which part of the site it belongs to, because the margin
index and the header both need to know. Those five groups are the five
destinations in the bar, so the scroll was cut where it already divides
itself.

The same is true of the navigation. `linkTo` already takes a flag for
"this is not the home page" and rewrites fragments accordingly. `frostNav`
already accepts a current tab and a set of menus. The stylesheet already
carries rules for `.nav-item--menu`, `.nav-menu`, `.nav-panel-sub` and
`a[aria-current]` that the single page never reaches. None of that was written
for this variation: it is what is left of the multi-page site this design
started as, before it was collapsed to one scroll on 22 October.

## What this variation adds, and it is deliberately little

Four things, all in `tools/multipage/site.mjs` in the production repository,
at the bottom, in one block:

1. **The dropdown's own surface.** `.nav-menu` was positioned, timed and
   reduced-motion aware, and empty: the one page it shipped on had nowhere to
   send anyone. It had no ground, no ink and no rules between its items. A
   flat plate, no radius and no shadow, because this world has no elevation
   system.
2. **A band that opens a page** takes the header's clearance, using the hero's
   own line rather than a new number.
3. **The onward rail.** The one thing this shape loses is that on a scroll the
   next part is simply the next thing down. At the foot of a page there is
   nothing below, so the next part is named, and the previous one with it.
4. **Four small corrections** where a component changes job: a card's name
   becomes the link to its page, the portfolio pages set their approach in one
   column rather than the drawer's two, a band that ends by sending the reader
   somewhere carries that link, and the tab you are on is drawn differently
   from the tab your pointer is over.

## What the checker proves

`node tools/multipage/check.mjs` in the production repository, on every build:

- 885 page links and 187 fragments all land, including every fragment landing
  on a page that actually has that id
- 77 asset references all resolve
- all 17 pages reachable from the home page
- every page marks exactly the tab it belongs to
- in a browser at 1440 and 393: nothing throws, no request fails, no page
  scrolls sideways, every image decodes, exactly one `h1` per page
- nothing is hidden at rest, in either motion state

## Three things worth knowing

**The home page belongs to no part.** It previews four and is inside none, so
its bands claim no part at all: the header underlines nothing while you are
there and the margin index stays out of the way. The first build got this
wrong and said OUR WORK in the margin of the home page.

**The portfolio pages name their own part.** A page about tuberculosis has a
band of results whose natural id is `impact`, which in the scroll's own maps
is the name of a different part of the site. Left alone, the margin index
announced Impact and the header underlined it.

**Every page carries the whole stylesheet and the whole behaviour inline**,
about 180 KB before compression, which is how the approved page is built and
why these open from the filesystem with no server. A production multi-page
build would serve both as cached files instead and each page would be about
70 KB.
