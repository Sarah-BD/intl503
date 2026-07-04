# Deploying INTL 503 (Netlify, free, shared password)

Goal: publish the Quarto site with one shared password that protects every
page *and* the reading PDFs, kept under (or linked from) your personal site.

## Why Netlify and not GitHub Pages
GitHub Pages can't enforce a password on the server, so linked PDFs stay
publicly fetchable even with "client-side" password tricks. Netlify's free
tier supports real HTTP Basic Auth via a `_headers` file, which gates the
whole site including the PDFs. Your personal site stays on GitHub Pages.

## One-time setup

### 1. Pick the shared password
Edit `_headers` in the project root and replace the example line:

```
/*
  Basic-Auth: intl503:CHANGE-ME-summer2026
```

Use whatever `username:password` you'll hand the class.

### 2. Make Quarto copy `_headers` into the published site
Add this line under the `project:` block in `_quarto.yml`:

```yaml
project:
  type: website
  output-dir: _site
  resources:
    - _headers          # <-- add this so the password file lands in _site/
```

### 3. Render
```bash
quarto render
```
Confirm the file copied:
```bash
ls _site/_headers
```

### 4. Deploy to Netlify (fastest = drag-and-drop)
1. Sign up / log in at https://app.netlify.com (free).
2. "Add new site" -> "Deploy manually."
3. Drag the entire `_site` folder onto the drop zone.
4. Visit the resulting `*.netlify.app` URL — you should get a username/password
   prompt. Enter the credentials from `_headers`.

(Alternative: "Import from Git" connects the GitHub repo and rebuilds on every
push. Set build command `quarto render` and publish directory `_site`. Only
worth it once the weekend rebuild cadence settles.)

### 5. (Optional) Put it under your domain
- If your personal site uses a **custom domain** (e.g. `yourname.com`) on GitHub
  Pages: in Netlify -> Domain settings, add a subdomain like
  `ipe.yourname.com`, then add the CNAME record Netlify shows you at your DNS
  provider. Result: `https://ipe.yourname.com`, feels like a subsite.
- If your personal site is `username.github.io` with **no** custom domain: keep
  the `*.netlify.app` URL (or buy a cheap domain) and link to it prominently
  from your homepage. A literal subpath isn't possible across two hosts.

## Each weekend update
Just re-run `quarto render` and re-drag `_site` onto the same Netlify site
(or `git push` if you connected Git). The password persists.

## Notes
- Basic Auth prompt is the plain browser dialog (no "logout"; closes with the
  browser). Fine for a class.
- Copyright: the password makes distribution to enrolled students defensible.
  The **full Oatley textbook** (all chapter PDFs) is the riskiest piece — prefer
  IU library e-reserves for the textbook; keep articles + your own materials on
  the site.
