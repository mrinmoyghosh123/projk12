# projk12.org — Under Construction

Static "coming soon" landing page for [www.projk12.org](https://www.projk12.org).

## Files

- `index.html` — the live page
- `CNAME` — tells GitHub Pages to serve this on `www.projk12.org`
- `Landing Page v1.html` — earlier (more detailed) draft, kept for reference

## Deploy to GitHub Pages

### 1. Create the repo

```bash
# in this folder
git init
git add .
git commit -m "Initial commit: coming-soon landing"
git branch -M main
git remote add origin https://github.com/<your-username>/projk12.git
git push -u origin main
```

### 2. Enable Pages

On GitHub: **Settings → Pages**
- **Source:** Deploy from a branch
- **Branch:** `main` / `/ (root)`
- Save.

GitHub will detect the `CNAME` file and set the custom domain to `www.projk12.org` automatically. Tick **Enforce HTTPS** once the cert provisions (usually within ~15 min after DNS is correct).

### 3. Point DNS at GitHub

At your domain registrar (where projk12.org is registered), set these records:

**For the `www` subdomain (the one this site lives on):**
```
Type   Name   Value
CNAME  www    <your-username>.github.io.
```

**For the apex `projk12.org` (so it redirects to www):**
```
Type   Name   Value
A      @      185.199.108.153
A      @      185.199.109.153
A      @      185.199.110.153
A      @      185.199.111.153
```
(These are GitHub Pages' four anycast IPs.)

### 4. Wait for DNS

5 min – a few hours. Check progress with:
```bash
dig www.projk12.org +short
```
Once it returns GitHub's IPs (or `<your-username>.github.io`), the site is live.

---

To update the page later, edit `index.html`, then `git commit && git push`. GitHub Pages re-deploys in ~30 seconds.
