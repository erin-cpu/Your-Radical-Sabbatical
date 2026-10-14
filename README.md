# Your Radical Sabbatical

The landing page for Your Radical Sabbatical — five days at Endicott College, Beverly, Massachusetts, Summer 2027.

Live at **https://yourradicalsabbatical.com**

A single static page. No build step, no dependencies, no framework. Open `index.html` in a browser and it works.

---

## Files

```
index.html          the entire page — structure, styles and behaviour
CNAME               tells GitHub Pages to serve the custom domain
robots.txt          search engine permissions
sitemap.xml         one URL, for indexing
.nojekyll           stops GitHub running Jekyll over the files
images/
  arts-center.jpg     Manninen Center for the Arts (cover)
  quad-dusk.jpg       the quad at golden hour (filmstrip + social card)
  beach.jpg           the shoreline
  garden-lodge.webp   workshop and salon spaces
  lodge-patio.jpg     the patio
  campus-aerial.jpg   behind the permission slip
  erin.jpg            host photo
  social-card.jpg     1200×630 link preview
  favicon.png         browser tab icon
```

Fonts load from Google Fonts at runtime: Bricolage Grotesque, Courier Prime, Archivo. Everything else is in the file.

---

## Publishing to GitHub Pages

**1. Create the repository** on GitHub, then from this folder:

```bash
git init
git add .
git commit -m "Your Radical Sabbatical landing page"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

**2. Turn on Pages.** Repository → Settings → Pages → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.

**3. Point the domain.** At your domain registrar, create these DNS records:

| Type | Name | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `YOUR-USERNAME.github.io` |

**4. Back in Settings → Pages**, enter `yourradicalsabbatical.com` as the custom domain, then tick **Enforce HTTPS** once the certificate is issued. DNS can take anywhere from ten minutes to a day to propagate; the certificate follows shortly after.

The `CNAME` file in this repo already contains the domain, so GitHub will pick it up on the first deploy.

---

## Making changes

Edit `index.html` and push. The page redeploys in about a minute.

Things you are most likely to want to change:

| What | Where to look |
|---|---|
| The interest form link | search for `typeform.com` — it appears in four places |
| The domain | search for `yourradicalsabbatical` — masthead, spine, permission slip, footer |
| Host bio and credits | search for `class="pass"` |
| Colours | the `:root` block at the top of the `<style>` — every colour is a token |
| Fonts | the two `<link>` tags in `<head>`, plus the font tokens in `:root` |
| Dates and pricing | deliberately absent. The page says these go out with the application. |

The countdown on the permission slip and in the masthead computes itself from the visitor's date against 21 June 2027 — search for `new Date(2027, 5, 21)` to change the target.

---

## What the page does

Beyond scrolling:

- The cover and the permission slip can be **stamped** — click anywhere on them
- The **"Your"** in the title is editable; a visitor's name propagates to the masthead and the permission slip, and persists in their browser
- The **hundred squares** are clickable; claiming all seventy triggers confetti
- The **three-question quiz** picks a track and stamps the matching card
- The **slot machine** generates a creative prompt from three word lists
- The **five day tabs** recolour the section
- The **filmstrip** drags sideways
- The **packing list** remembers ticks per visitor, in their own browser
- The **permission slip** tears off
- The page progressively goes **out of register** as you scroll, and a Usefulness meter drains to zero

Visitor state (packing ticks, the name on the cover) lives in that visitor's own browser via `localStorage`. Nothing is sent anywhere. The only data collection is the Typeform.

---

Page and code by Claude, for Erin Neuhardt. Photographs of Endicott College supplied by Erin Neuhardt.
