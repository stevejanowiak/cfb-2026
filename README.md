# 2026 Win Totals Dashboard

A single-file dashboard tracking a 10-bet college football win-total slate,
Michigan's week-by-week win probabilities, and SP+ trends for 10 teams.

Everything lives in `index.html`. No build step, no server, no dependencies to install.

---

## First-time setup (about 10 minutes)

1. **Create a GitHub account** at github.com if you don't have one.

2. **Create a repository.** Click the `+` in the top right, then *New repository*.
   - Name it something like `cfb-2026`
   - Set it to **Public** — GitHub Pages is only free on public repos
   - Check *Add a README file*
   - Click *Create repository*

3. **Upload the dashboard.** In the repo, click *Add file* → *Upload files*,
   drag in `index.html`, then click *Commit changes*.
   The filename must be exactly `index.html` — that's what Pages serves by default.

4. **Turn on Pages.** Go to *Settings* → *Pages* (left sidebar).
   Under *Source*, choose **Deploy from a branch**. Set branch to `main` and
   folder to `/ (root)`. Click *Save*.

5. **Wait about a minute**, then reload the Settings → Pages screen. Your URL appears at
   the top, in the form:

   ```
   https://YOURNAME.github.io/cfb-2026/
   ```

   Send that link to the other two. It works on phones.

---

## Weekly update

Each week you'll get a new `index.html`. To publish it:

1. Open your repo and click on `index.html`
2. Click the pencil icon (*Edit this file*), select all, and paste in the new contents
   — or use *Add file* → *Upload files* and drop the new one in to overwrite
3. Click *Commit changes*
4. The live site updates in under a minute

Every commit is saved, so you can see any prior week's version under the *History*
tab, or roll back if something looks wrong.

---

## What changes each week

All the data sits in one JavaScript object near the top of the `<script>` block:

```js
const DATA = { ... };
```

Nothing else in the file changes week to week. The markup, styling, and chart
configuration stay fixed. That object holds:

| Key | What it is |
|---|---|
| `week`, `date` | Header label |
| `bets` | One entry per bet: kickoff, opponent, probabilities, value, status |
| `michOpp`, `grid` | Michigan's 12 opponents, and one row per week of win probabilities |
| `sp26` | SP+ rating by week for the 10 tracked teams |
| `michHist` | Michigan SP+ by week for 2023, 2024, 2025, 2026 |
| `ev` | Total expected value by week, 2023–2026 |

Bet rows use `status` of `live`, `won`, or `lost` — that's what drives the green
and red row shading.

---

## Notes

- The page pulls Chart.js and fonts from a CDN, so it needs an internet connection.
  It will not render charts offline.
- The URL is public. Anyone with the link can see it. There's nothing sensitive here,
  but worth knowing before you share it around.
- Naming the repo `YOURNAME.github.io` instead would serve it at the root URL
  (`https://YOURNAME.github.io/`) with no subfolder. Only works for one repo per account.
