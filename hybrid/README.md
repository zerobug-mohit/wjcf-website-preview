# WJCF — the long scroll, with portfolio pages

The approved site is one page, and here it stays one page: the same cover, the
same twelve bands, the same order, the same navigation of five anchors.

**One thing is different.** Each portfolio card's control was a button that
opened a drawer under its row. It is now a link that says **Explore
portfolio** and goes to a page about that portfolio.

Open `index.html`. No server is needed.

---

## The nine pages

| | |
|---|---|
| `index.html` | The approved long scroll, unchanged except for the eight card controls. |
| `work-*.html` | A page for each portfolio: the challenge, the approach in four named moves, the results. |

## Why this shape

The drawer has to hold a whole portfolio inside a grid of eight. It gets the
challenge in one column, the approach in another and the results in a strip,
and it has no room for anything that arrives later: no results table, no state
list, no publications, no photographs of the work.

A page has room for all of it. The scroll keeps what it is good at, which is
being read start to finish in one movement, and stops being the only place the
detail can live.

## What was proved, not assumed

The claim that the scroll is unchanged is checked on every build rather than
hoped. The generated page is compared against the frozen approved page line by
line:

```
32 differing runs; 32 inside the portfolio card grid
Nothing outside the grid differs. The scroll is the approved page.
8 cards say "Explore portfolio"
0 drawers left
```

Thirty-two is exactly four per portfolio: the card's name becomes a link, the
button becomes an anchor, the label changes, and the ten-line drawer panel
goes. Nothing above or below the grid moves.

`node tools/multipage/check.mjs hybrid` in the production repository adds the
rest: 161 links and 109 fragments all landing, every fragment on a page that
has that id, 50 assets resolving, all nine pages reachable, and a browser at
1440 and 393 confirming that nothing throws, no request fails, no page scrolls
sideways and every image decodes.

## The portfolio pages needed no new navigation

That is the part worth noticing. `navBar()` already takes the page it is on,
and `linkTo` already rewrites a fragment for a page that is not the home page:
ask for the bar with anything other than `'Home'` and every tab becomes
`index.html#about` and the rest. So the header on a portfolio page is the
approved header, doing exactly what it was built to do, on the pages it was
built for.

At the foot of each page a rail names the previous and next portfolio. The
first one's previous and the last one's next are both the areas section of the
scroll, so the series closes rather than dead-ends.

There is no closing band below that rail, and there was one. It said "The rest
of our work", repeated the standfirst the scroll already carries, and linked
back to the grid. That made three routes to the same place: the sticky
header's Our Work anchor, which never leaves the screen, the rail, and a band
of borrowed copy between them. Two of those are the design's. The third was
padding, so it went.

## How this relates to the other two

| Folder | Shape |
|---|---|
| `v7-poster` | The approved long scroll. One page. |
| `v7-hybrid` | This. The long scroll, with eight portfolio pages behind it. |
| `v7-multipage` | A full multi-page site: seventeen pages, a navigation bar of pages with menus. |

The hybrid and the multi-page variation **share their portfolio pages**, from
`tools/multipage/parts.mjs`, so the eight detail pages are literally the same
code in both. The client is comparing shapes, not portfolio pages; if those
differed between the variations the comparison would be measuring the wrong
thing.
