# How to make eyeclinicdelhi.com live with the new site

This is a step-by-step guide to publish the new website on **Vercel** (free) and re-point your **eyeclinicdelhi.com** domain from Weebly to the new site. Once it's live, you can cancel the Weebly subscription.

The whole process is three stages — each takes about 10 minutes.

---

## Stage 1 — Get the website files onto GitHub

Vercel deploys from a GitHub repository. We'll put the new website there first.

1. **Create a free GitHub account** at https://github.com/signup if you don't already have one. Use your usual email.
2. Once logged in, click the green **"New"** button on the left (or go to https://github.com/new).
3. Set:
   - **Repository name:** `vasundhara-eye-centre-site`
   - **Public** is fine (it's just a website).
   - Tick **"Add a README file"**.
   - Click **Create repository**.
4. On the new repository page, click **"Add file" → "Upload files"**.
5. Open the `vasundhara-website` folder I've put in your "Vasundhara important documents" folder. Select **all the contents** (the `index.html` file, the `about.html`, `contact.html`, etc., plus the `css`, `js` and `images` folders) and **drag them into the GitHub upload box**.
6. Scroll down, write `Initial site` in the commit box, click **Commit changes**.
7. Wait for the upload to finish — you should see your files listed.

Done. The site is now in GitHub.

---

## Stage 2 — Deploy it to Vercel

1. Go to https://vercel.com/signup and click **"Continue with GitHub"**. Use the same GitHub account you just made.
2. Once you're in the Vercel dashboard, click **"Add New… → Project"** at the top right.
3. You'll see a list of your GitHub repositories. Find **vasundhara-eye-centre-site** and click **Import**.
4. On the next screen, **don't change anything** — Vercel auto-detects this as a static site. Just click **Deploy**.
5. Wait about 30–60 seconds. Vercel will show "Congratulations" and give you a temporary URL like `vasundhara-eye-centre-site.vercel.app`.
6. Click that URL — your new site should open. Walk through the pages, click the call/email buttons, make sure everything works.

The site is live at the temporary URL. Now we just need to put it on **eyeclinicdelhi.com**.

---

## Stage 3 — Point eyeclinicdelhi.com to Vercel

This is exactly what we did last time with the other site. There are two halves: tell Vercel about the domain, and tell GoDaddy where to send it.

### 3A — In Vercel
1. Open your project's dashboard on Vercel.
2. Click the **Settings** tab → **Domains** in the left menu.
3. In the **"Add"** box, type `eyeclinicdelhi.com` and click **Add**.
4. Vercel will say *"Invalid configuration"* and show you two records you need to set in GoDaddy. Keep this Vercel tab open — we'll come back to it.
5. Click **Add** again and type `www.eyeclinicdelhi.com`. Add that too. Vercel will show another DNS record to set.

### 3B — In GoDaddy
1. Log into https://godaddy.com.
2. Click your name (top right) → **My Products** → find **eyeclinicdelhi.com** in the Domains list → click **DNS** next to it.
3. You'll see a list of existing DNS records (probably pointing to Weebly right now). We'll change two of them.

For the **root domain** (the row with name `@`):
- Find the existing `A` record with name `@`.
- Click the pencil icon to edit it.
- Change the **Value** to: `76.76.21.21` (this is Vercel's IP address — Vercel will show you the exact one in your dashboard, use that if it differs).
- Save.

For the **www subdomain** (the row with name `www`):
- Find the existing `CNAME` record with name `www`.
- Click the pencil icon to edit it.
- Change the **Value** to: `cname.vercel-dns.com.`
- Save.

If a record doesn't already exist, click **Add** at the top and create a new one with the values above.

> **Note:** GoDaddy may show a warning about Weebly hosting — it's fine to ignore. Once we change the DNS, Weebly hosting won't be in use any more.

### 3C — Wait for DNS to propagate
- Go back to the Vercel **Domains** page and refresh after a few minutes. The "Invalid configuration" warnings should turn green ✓ (sometimes takes 10 minutes; can take up to a few hours in rare cases).
- When both rows show green ticks, open https://eyeclinicdelhi.com in a new browser tab. The new site should appear.

That's it — eyeclinicdelhi.com now serves the new site, hosted free on Vercel.

---

## Stage 4 (optional but recommended) — Cancel Weebly

Once eyeclinicdelhi.com is loading the new site reliably (give it a day to be safe), you can cancel the Weebly subscription:

1. Log into https://weebly.com.
2. Go to **Account → Domains and Plans**.
3. Find the subscription tied to eyeclinicdelhi.com and click **Cancel**.

Your domain registration stays at GoDaddy (renew that yearly as usual). Vercel hosting is free for sites at this scale — there's no monthly bill.

---

## How to update the site later

When you want to change something on the website (add a doctor, update hours, swap a photo):

1. Open the file on GitHub directly (e.g. click `contact.html` → click the pencil icon at the top right of the file view).
2. Make the change.
3. Scroll down, click **Commit changes**.
4. Vercel automatically rebuilds and the change is live within ~30 seconds.

If you'd rather not edit raw HTML, just send me the change you want and I'll do it for you.

---

## Troubleshooting

**The site shows the wrong page or still shows Weebly**
The old DNS is cached on your computer. Try a different browser, your phone on mobile data, or open https://www.whatsmydns.net and search for `eyeclinicdelhi.com` — you'll see how the change is propagating across the world.

**A photo isn't showing up**
Filename mismatch — the `images/` folder names are case-sensitive. Make sure the GitHub upload preserved the exact names.

**Vercel says "Domain already in use"**
Means the domain is registered to a different Vercel account. Email Vercel support at support@vercel.com — usually resolved within a day.

**You see a "Set this domain as the primary" prompt**
Click that button, choose `www.eyeclinicdelhi.com` as the primary — Vercel will auto-redirect the bare domain to the www version (this is the standard setup).

---

## Cost summary

| Item | Cost |
|---|---|
| GitHub repository | Free |
| Vercel hosting | Free (forever, at this scale) |
| GoDaddy domain renewal | Whatever you already pay (~₹900/year) |
| Weebly subscription | **Cancel — saves whatever you were paying** |

Total ongoing cost after switching: just the GoDaddy domain renewal.
