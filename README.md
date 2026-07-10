# memer.shop

The Memer preorder site — a single self-contained `index.html` (all fonts, images, and the live Fourthwall storefront connection are baked in). No build step, no backend.

---

## Deploy to Cloudflare Pages (recommended)

You need a **free Cloudflare account** — sign up at https://dash.cloudflare.com (no payment info required). Cloudflare is what actually hosts and serves the site.

### 1. Put the code on GitHub
- Create a repo named `memer-shop`.
- Add `index.html` (drag-and-drop upload in the GitHub web UI is fine).

### 2. Create the Cloudflare Pages project
- Log in to https://dash.cloudflare.com
- Left sidebar → **Workers & Pages** → **Create** → **Pages** tab → **Connect to Git**
- Authorize GitHub and select the **memer-shop** repo
- Build settings:
  - **Framework preset:** None
  - **Build command:** (leave blank)
  - **Output directory:** `/`
- **Save and Deploy** → you get a live `*.pages.dev` URL in ~30s. Confirm it works.

### 3. Connect www.memer.shop
- In the Pages project → **Custom domains** → **Set up a domain** → enter `www.memer.shop`
- Cloudflare will ask you to manage the domain's DNS. Easiest: add `memer.shop` as a site in Cloudflare, let it auto-detect records, then paste the two Cloudflare nameservers it gives you into your **domain registrar** (where you bought memer.shop).
- Also add `memer.shop` (no www) and redirect it to `www`.
- SSL/HTTPS turns on automatically once DNS propagates (minutes to a few hours).

### 4. Lock it down (2 min)
Turn on **2-factor authentication** on: Cloudflare, GitHub, and your domain registrar. That's the real attack surface — the site itself is static and has nothing to hack.

---

## Updating the site
The site is exported from a design tool. To update: replace `index.html` in the repo and commit — Cloudflare auto-redeploys. No manual re-upload needed.

## Notes
- The Fourthwall token in the file is a **public storefront token** (`ptkn_…`) — read-only, safe to be in client code.
- Orders, payment, and shipping are handled by **Fourthwall**. This site links out to Fourthwall's hosted checkout.
- Alternative: you can skip separate hosting entirely and connect www.memer.shop **inside Fourthwall** — then Fourthwall serves the whole site. Use that only if you don't want this custom design as the front door.
