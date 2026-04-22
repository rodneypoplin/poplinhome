# poplinhome

Public compliance pages for a personal SMS alert system.

Served at **https://poplinhome.com** via Cloudflare Pages. Purpose: provide
privacy policy, terms of service, and SMS opt-in disclosures required by
A2P 10DLC carrier review for a personal Twilio Sole Proprietor messaging
campaign.

This site is NOT a product. It is NOT offered to the public. It exists to
satisfy regulatory transparency requirements for a single-user alert system.

## Structure

- `index.html` — landing page
- `opt-in.html` — SMS consent disclosure
- `privacy.html` — privacy policy
- `terms.html` — terms of service
- `contact.html` — operator contact
- `style.css` — shared styles

All static HTML, no build step. Cloudflare Pages serves the directory as-is.

## Before going live

See `REVIEW.md` for the short checklist of placeholders that need your
confirmation before the first deploy.

## Deploy

Cloudflare Pages, GitHub-connected. Any push to `main` auto-deploys.

Or via wrangler:

```bash
wrangler pages deploy . --project-name poplinhome
```
