# Publishing INTL 503 as a subpage of your GitHub Pages site

Your personal site lives in `USERNAME.github.io` with a custom domain
(call it `YOURDOMAIN.com`). Because of that custom domain, **any project
repo you own is automatically served at `YOURDOMAIN.com/<repo-name>/`** —
so the course site becomes a true subpage with no extra DNS work.

Pick the repo name to match the URL you want:
- repo `intl503`  ->  `https://YOURDOMAIN.com/intl503/`
- repo `ipe`      ->  `https://YOURDOMAIN.com/ipe/`

The steps below use `intl503` — substitute your choice.

---

## One-time setup

### 1. Create an empty repo on GitHub
On github.com: **New repository** -> name it `intl503` -> Public ->
do NOT add a README/.gitignore/license -> **Create repository**.

(Public is simplest; the site is your own CC-licensed materials. The
`.gitignore` already keeps readings, test bank, notes, and exams OUT of
the repo, so nothing copyrighted or private gets pushed.)

### 2. Turn this project into a git repo and push it
In a terminal (or RStudio's Terminal pane), from the project folder:

```bash
cd "/Users/sarahbauerledanzman/Library/CloudStorage/OneDrive-IndianaUniversity/Teaching/IU Courses/503 - IPE"
git init
git add .
git commit -m "Initial commit: INTL 503 course site"
git branch -M main
git remote add origin https://github.com/USERNAME/intl503.git
git push -u origin main
```

### 3. Publish the rendered site
```bash
quarto publish gh-pages
```
This renders the site, creates a `gh-pages` branch, pushes the HTML there,
adds the `.nojekyll` file GitHub needs, and turns on Pages. Say "yes" when
it asks to confirm. (Re-run this one command anytime you want to push an
update — e.g. after the weekend build.)

### 4. Check the Pages settings (usually already correct)
On GitHub: repo **Settings -> Pages**. Source should be **Deploy from a
branch -> `gh-pages` / (root)**. Leave the **custom domain field BLANK** —
blank is what makes it inherit `YOURDOMAIN.com/intl503/`. (Adding a domain
here would move it off the subpath.)

### 5. Visit it
After a minute or two: `https://YOURDOMAIN.com/intl503/`
The slides now load correctly because they're served over HTTPS (the blank
"open in new tab" problem only happens when opening files from disk).

### 6. Link it from your personal site
Add a menu/nav item on your personal site pointing to `/intl503/`
(or the full URL). Edit that in your personal site's own generator config.

---

## Updating later
From the project folder, just:
```bash
quarto publish gh-pages
```
Source changes can also be saved with `git add . && git commit && git push`.

## Notes
- **No password.** GitHub Pages can't password-protect. If you ever need
  that, see `DEPLOY.md` for the Netlify-subdomain route instead.
- **The `_headers` file does nothing on GitHub Pages** (it's Netlify-only).
  Harmless to leave; ignore it here.
- **Subpath just works** — Quarto uses relative links, so no `_quarto.yml`
  change is needed to live under `/intl503/`. If any asset ever 404s, the
  fix is to set `site-url: https://YOURDOMAIN.com/intl503/` in `_quarto.yml`.
- **Private repo option:** GitHub Pages can serve from a private repo on
  paid plans. If you'd rather not have the source public, tell me and I'll
  adjust — but the published site is public either way.
