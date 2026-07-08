# Bitcoin Mining Dashboard

Single-file dashboard (`index.html`) — all HTML, CSS, and JavaScript embedded, no build step
and no dependencies. Open the file in a browser to run it. Market data (CoinGecko,
Blockchain.info, mempool.space) is fetched client-side at runtime.

## Git & PR workflow

- **Before pushing to any branch that has an associated PR, check that the PR is still open**
  (via the GitHub API). If it has been merged or closed, do NOT push to that branch — cut a
  fresh branch from the latest `main`, apply the changes there, and open a new PR.
- Never stack new commits onto an already-merged branch.
- One concern per PR; the owner merges quickly, so keep PRs small and focused.

## Privacy rules (public repo)

- User-specific values (wallet addresses, contract parameter overrides) live in browser
  localStorage only. Never hardcode personal financial data, addresses, or xpubs into the
  repo — shipped defaults must stay safe to publish.

## Verifying changes

- Test by driving the real page in headless Chromium (Playwright), mocking the external APIs
  with `page.route(...)` — the sandbox may block outbound network. Screenshot light and dark
  modes (`colorScheme` context option) and check math against the yield formula:
  `dailyBtc = fleetTH × 1e12 × 86400 × blockReward / (difficulty × 2^32) × (1 − poolFee)`.
