# Sites Navigator

Personal links/bookmark homepage — terminal/retro styled, single `index.html`, no build step.

## Deploy to GitHub Pages

1. Create a new repo on GitHub (e.g. `sites-navigator`, or `<your-username>.github.io` if you want it at the root of your GitHub domain).
2. Add `index.html` to the repo root and push to `main`.
3. In the repo: **Settings → Pages → Build and deployment → Source** = `Deploy from a branch`, branch = `main`, folder = `/ (root)`. Save.
4. Your page goes live at `https://<username>.github.io/<repo-name>/` (or `https://<username>.github.io/` if you used the `.github.io` repo name).
5. Optional: add a `CNAME` file with a custom domain if you want it at your own domain instead.

## Making Press & Mentions self-updating

Right now that section is a static, hand-written list. To make it sync automatically from your Raindrop "Mentions" collection:

1. In Raindrop, open the **Mentions** collection → **Share** → copy the RSS feed link (looks like `https://rss.raindrop.io/<id>/<token>`).
2. Open `index.html`, find `var RAINDROP_RSS_URL = '';` near the bottom, and paste the link between the quotes.
3. Push. On page load the script fetches the feed (via the free [rss2json.com](https://rss2json.com) proxy, since browsers can't fetch raw RSS cross-origin) and swaps in the live list, marked with a small "● live" badge in the section header.

If you leave the URL blank, or the fetch ever fails (rss2json's free tier is rate-limited), the page just quietly keeps showing the static list that's already baked into the HTML — nothing breaks either way. Worth checking back periodically that the live badge is still showing; if you outgrow the free proxy tier, rss2json.com offers a free API key for higher limits (add it as `&api_key=...` to the `api` URL in the script).
