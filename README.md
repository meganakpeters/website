# meganakpeters.org

Personal website for Megan A. K. Peters. A single, self-contained `index.html` file — no build step, no dependencies, nothing to install. Fonts load from Google Fonts over the web; everything else is inline.

---

## Files in this folder

- `index.html` — the entire website
- `megan.jpg` — your photo (you still need to add this; see below)
- `CNAME` — tells GitHub which domain to serve (created for you during setup, step 6)
- `README.md` — this guide

---

## Adding your photo

1. Save a photo of yourself into this folder and name it exactly `megan.jpg` (a portrait/vertical crop looks best — roughly 4:5).
2. Open `index.html` in a text editor and find this block (around line 250):

   ```html
   <div class="ph">[ your photo here ]<br>...</div>
   <!-- <img src="megan.jpg" alt="Megan A. K. Peters"> -->
   ```

3. Delete the `<div class="ph">...</div>` line and remove the `<!--` and `-->` around the `<img>` line so it becomes:

   ```html
   <img src="megan.jpg" alt="Megan A. K. Peters">
   ```

4. Save. Double-click `index.html` to preview in your browser.

If you'd rather I do this once you've picked a photo, just drop it in the folder and ask.

---

## Publishing it for free with GitHub Pages

GitHub Pages hosts static sites at no cost and supports custom domains with free HTTPS. This is the whole path from empty account to `https://meganakpeters.org` serving your new page.

### 1. Create a GitHub account
Go to <https://github.com> and sign up (free) if you don't already have one.

### 2. Create a new repository
- Click the **+** in the top-right → **New repository**.
- **Repository name:** `meganakpeters` (any name works — the name doesn't affect the custom domain).
- Set it to **Public**.
- Do **not** add a README (you already have one).
- Click **Create repository**.

### 3. Upload your files
On the empty repository page:
- Click **uploading an existing file**.
- Drag in `index.html`, `README.md`, and `megan.jpg` (once you've added your photo).
- Click **Commit changes**.

> Prefer the command line? From inside this folder:
> ```bash
> git init
> git add .
> git commit -m "Initial site"
> git branch -M main
> git remote add origin https://github.com/YOUR-USERNAME/meganakpeters.git
> git push -u origin main
> ```

### 4. Turn on GitHub Pages
- In the repository, go to **Settings** → **Pages** (left sidebar).
- Under **Build and deployment → Source**, choose **Deploy from a branch**.
- Set **Branch** to `main` and folder to `/ (root)`. Click **Save**.
- Wait ~1 minute. A green banner will show your live URL, something like `https://YOUR-USERNAME.github.io/meganakpeters/`. Open it to confirm the site works.

At this point the site is live on the github.io address. The next steps point your own domain at it.

### 5. Point meganakpeters.org at GitHub Pages
Your domain currently sends visitors to Google Sites. You'll change that at whoever manages your domain's DNS (your **registrar** — e.g. Google Domains/Squarespace, Namecheap, GoDaddy, Cloudflare). Log in there and open the DNS settings for `meganakpeters.org`.

**First, remove the old records** that point the domain at Google Sites — typically a `CNAME` record on `www` pointing to `ghs.googlehosted.com`, and/or any `A`/forwarding records Google set up. Removing these is what disconnects the old Google site.

**Then add the GitHub Pages records.**

For the root domain (`meganakpeters.org`), add four **A** records — Host/Name `@`, each pointing to one of:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

(Optional but recommended) also add four **AAAA** records for `@`:

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

For the `www` version, add one **CNAME** record — Host/Name `www`, value `YOUR-USERNAME.github.io` (include the trailing dot if your registrar requires one).

> These four IP addresses are GitHub's official, published Pages addresses and are the same for everyone. DNS changes can take anywhere from a few minutes to a day (occasionally up to 48 hours) to propagate.

### 6. Tell GitHub about your domain
- Back in **Settings → Pages → Custom domain**, type `meganakpeters.org` and click **Save**.
- This automatically creates a file named `CNAME` in your repository containing your domain — keep it there.
- Leave **Enforce HTTPS** unchecked at first. Once GitHub finishes issuing the certificate (can take up to ~24 hours after DNS resolves), the checkbox becomes available — tick it so visitors always get `https://`.

### 7. Done
Visit `https://meganakpeters.org`. If it doesn't resolve immediately, give DNS time and check back. GitHub's **Settings → Pages** panel shows a green check when the domain and certificate are verified.

---

## Making changes later

Edit `index.html` (all the text and links live there), then either re-upload it through the GitHub website (**Add file → Upload files**, or click the file → pencil icon) or, if you used git:

```bash
git add .
git commit -m "Update content"
git push
```

Changes go live within a minute or so.

---

## Quick reference

| Thing | Where |
|---|---|
| All page content & links | `index.html` |
| Your photo | `megan.jpg` in this folder |
| GitHub Pages IPs (root domain) | `185.199.108.153` – `.111.153` |
| `www` CNAME target | `YOUR-USERNAME.github.io` |
| Live URL before custom domain | `https://YOUR-USERNAME.github.io/meganakpeters/` |

If you get stuck on any step — especially the DNS part, which varies by registrar — tell me who your domain registrar is and I'll give you the exact clicks.
