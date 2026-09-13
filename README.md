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

## Scope for the first version

The first version should support browsing a useful Hacker News feed, viewing
story metadata, and opening either the original article or its discussion.
Search, accounts, personalization, offline caching, and additional news
sources are intentionally out of scope until the basic experience is solid.
