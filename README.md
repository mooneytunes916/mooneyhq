# mooneyhq.com

The personal site of Jonathon Mooney. I go by Mooney.

A single-file static site, no build step. Just `index.html`, deployed to Vercel, pointed at the `mooneyhq.com` domain bought from Namecheap.

---

## How to get this live (step by step)

You've done this twice before — once for Mooney Tunes, once for the Hano-Mooneys beach trip. Same playbook. Should take about 30 minutes if DNS behaves.

### Step 1 — Buy the domain (5 min)

1. Go to **namecheap.com** and log in (same account you used for `mooneytunes.app`).
2. Search for **mooneyhq.com** and add to cart.
3. At checkout, **decline the upsells**: you don't need their email hosting, Premium DNS, or SSL. Vercel handles SSL for free.
4. **Turn on Auto-Renew** so you don't lose the domain in a year.
5. **Turn on WhoisGuard** (free) — keeps your personal info out of public WHOIS lookups.
6. Complete checkout.

### Step 2 — Create the GitHub repo (5 min)

1. Go to **github.com** and sign in (mooneyjonathon@gmail.com, account `mooneytunes916` — or rename to `mooneyhq` first under Settings → Account → Change username if you want a cleaner URL).
2. Click the **+** icon top right → **New repository**.
3. Repository name: `mooneyhq`
4. Set to **Public**.
5. Leave everything else default. Click **Create repository**.
6. On the next screen, click the link that says **"uploading an existing file"**.
7. Drag your `index.html` and `README.md` files onto the upload area.
8. Scroll down. Click **Commit changes**.

That's it. Your code is on GitHub.

### Step 3 — Deploy to Vercel (5 min)

1. Go to **vercel.com** and sign in with GitHub (same account as Mooney Tunes).
2. Click **Add New...** → **Project**.
3. Find **mooneyhq** in your repo list. Click **Import**.
4. **Framework Preset**: leave on "Other" (it's just static HTML, no framework needed).
5. **Root Directory**: leave as `./` (the index.html is at the root).
6. Click **Deploy**.

About 30 seconds later you'll get a live URL like `mooneyhq.vercel.app`. Click it. The site should load.

### Step 4 — Connect mooneyhq.com to the Vercel deployment (10 min, plus DNS wait)

1. In Vercel, open the **mooneyhq** project → **Settings** → **Domains**.
2. In the input box, type `mooneyhq.com` and click **Add**.
3. Vercel will give you two DNS records to add at Namecheap. Usually:
   - An **A record** for `@` pointing to `76.76.21.21` (or similar Vercel IP)
   - A **CNAME record** for `www` pointing to `cname.vercel-dns.com`
   - Copy the exact values Vercel shows you — they sometimes change.
4. In a new tab, go to **namecheap.com** → Dashboard → **mooneyhq.com** → **Manage** → **Advanced DNS**.
5. Delete the default Namecheap "URL Redirect" / "Parking Page" records that come with new domains.
6. Click **Add New Record** and add the **A record** Vercel gave you.
7. Add the **CNAME record** Vercel gave you.
8. Save changes.
9. Wait. DNS propagation can take 5 to 30 minutes (occasionally longer).
10. Refresh the Vercel Domains page. Once it shows "Valid Configuration" with a green check, you're done. Vercel auto-provisions an SSL cert at that point too.

### Step 5 — Test (2 min)

1. Open **mooneyhq.com** in a fresh browser window (or incognito to bypass cache).
2. Check the site loads.
3. Click the email link — should open your mail app addressed to mooneyjonathon@gmail.com.
4. Click LinkedIn — should land on your profile.
5. Click GitHub — should land on your GitHub.

If anything's off, holler.

---

## How to make changes after it's live

Any edit you make to `index.html` in GitHub auto-deploys to Vercel in about 30 seconds. To edit:

1. Go to **github.com/mooneytunes916/mooneyhq** (or whichever username you end up with).
2. Click `index.html` → click the pencil icon to edit.
3. Make your change. Scroll down. Click **Commit changes**.
4. Vercel sees the commit and redeploys automatically.

For bigger edits, ask Claude to make the change and you can copy/paste the new file back to GitHub. Or use Claude Code locally if you want the full dev loop.

---

## What's still TODO

- [ ] Swap the placeholder gray "M" avatar circle for a real photo. In `index.html`, find the line that starts `<div class="avatar" aria-hidden="true">M</div>` and replace it with `<img src="your-photo.jpg" class="avatar" alt="Mooney">`. Upload the photo to the repo first.
- [ ] Replace the gradient project thumbnails with real images when you have them.
- [ ] Build the `/about/` page (the "More about me ›" link currently goes to a 404).
- [ ] Write the "What I learned rolling out AI to 244 people" post (the homepage promises it).
- [ ] When you leave Lyft: add ABC Rideshare Inspections back to the About bullets and Projects list.
