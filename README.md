# AI Sthlm News

AI Sthlm News is a lightweight news-browsing interface, initially focused on
[Hacker News](https://news.ycombinator.com/). It aims to make browsing stories,
discussion, and source links calmer and more convenient while keeping the
original publisher and Hacker News as the source of truth.

## Purpose

- Present Hacker News stories in an easy-to-scan, pleasant interface.
- Link readers back to the original article and its Hacker News discussion.
- Fetch public data from the original source rather than maintaining a copied
  news database.
- Carry forward the visual character of the AI Sthlm Events project: clean,
  editorial, compact, and welcoming.

## Technical constraints

- The UI is rendered with Vue loaded from a CDN; no Vue build step is required.
- Keep the project simple and deployable as static files wherever possible.
- Prefer official public Hacker News endpoints (for example, the Firebase API)
  and respect their availability, rate limits, and browser CORS behavior.
- Do not scrape, republish, or alter article content. Store only minimal UI
  state when necessary; articles remain hosted by their publishers.
- Build for modern desktop and mobile browsers, with accessible semantic HTML,
  keyboard-friendly controls, and readable contrast.
- Reuse shared branding assets from
  [ai-sthlm/assets](https://github.com/ai-sthlm/assets) via its GitHub Pages
  URLs; do not duplicate those assets in this repository.

## Deployment

The site is deployed as static files through GitHub Pages. The workflow in
`.github/workflows/pages.yml` publishes `index.html` and `style.css` from the
default branch. In repository settings, select **GitHub Actions** as the
GitHub Pages source before the first deployment.

## Design decisions

- **Keep the feed dense.** A story's title, linked domain, score, comment
  count, author, and compact relative time share one flowing line. The layout
  may wrap on small screens, but it should not become a card-heavy feed.
- **Separate the two destinations clearly.** A story title opens its Hacker
  News item and discussion; the linked domain opens the original article. This
  makes discussion the primary interaction without hiding the source.
- **Treat the comment count as the discussion control.** Clicking it loads the
  top-level comments under that story. There is no separate “open on HN” action
  in the current UI.
- **Reveal discussion progressively.** Comments are initially one ellipsized
  row. Clicking the row expands its full, sanitized body and loads its direct
  replies in one action. The same interaction works recursively for replies.
- **Show useful thread context while collapsed.** Every comment shows its
  author, compact time, direct reply count, and—once the background count
  completes—the total number of descendants in that thread. HN exposes only
  direct child IDs, so totals require recursive API reads; cache item requests
  to avoid fetching the same item twice.
- **Keep dividers quiet.** Comments use top borders only, so the last comment
  does not create a doubled rule with the next story. Comment time uses the
  same muted color as story points.
- **Optimize the small screen deliberately.** Comment previews ellipsize to
  the available width, touch targets remain usable, and expanded discussion
  text increases in size and line height for reading on mobile.

## Scope for the first version

The first version should support browsing a useful Hacker News feed, viewing
story metadata, and opening either the original article or its discussion.
Search, accounts, personalization, offline caching, and additional news
sources are intentionally out of scope until the basic experience is solid.
