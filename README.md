# INTL 503 — International Political Economy

This folder is the working directory and Quarto source for **INTL 503: International Political Economy**, Summer 2026, taught online by Sarah Bauerle Danzman at Indiana University. It contains the source files for the course website, lecture decks, assignment descriptions, instructor notes, and reference materials.

The course meets July 6–31, 2026, Monday/Tuesday/Thursday/Friday (Wednesdays are non-meeting reading days). Textbook: Oatley, *International Political Economy* (7th ed.).

## What's at the root

| File | Purpose |
|------|---------|
| `_quarto.yml` | Site config — navbar, theme, output directory |
| `index.qmd` | Site home page |
| `syllabus.qmd` | Syllabus (rendered to the public site) |
| `syllabus-canvas.html` | Canvas-formatted syllabus for upload |
| `schedule.qmd` | Daily schedule with readings and assignments |
| `resources.qmd` | Student-facing resources page |
| `theme.scss` | Custom site theme |
| `503 - IPE.Rproj` | RStudio project file |
| `PUBLISH-GITHUB.md` | One-time GitHub Pages setup notes + the ongoing `quarto publish gh-pages` workflow |

## What's in each subfolder

| Folder | Contents |
|--------|----------|
| `slides/` | Lecture decks (`dayXX-chapterXX.qmd`). **Read `slides/SLIDE-CONVENTIONS.md` before creating or editing any deck.** Theme assets live in `slides/_theme/`. |
| `content/` | Short daily landing pages (`dayXX.qmd`) linking that day's deck, readings, and writing prompt |
| `assignments/` | Individual assignment description pages (quizzes, writing prompts, final exam, article presentation) |
| `readings/oatley/` | Oatley textbook chapter PDFs — instructor working copies, not distributed via the site |
| `readings/articles/` | Article PDFs *(planned: migrate these into a Zotero collection `INTL 503 — Summer 2026` and distribute via Canvas)* |
| `teaching-notes/` | Lecture-prep notes for my own use; not published to the site |
| `exams/` | Quiz 1-3, the cumulative final, and the grading rubrics (docx, with answer keys) — built for Canvas upload |
| `exams/test-bank/` | Oatley publisher test bank Word docs — source material for quiz item development |
| `_archive/` | Superseded drafts, old versions, planning logs. Kept for paper trail; not built into the site. |
| `_extensions/` | Quarto Pandoc extensions (Font Awesome, etc.) |

## Privacy — what never gets pushed to GitHub

The repo is **public**, so `.gitignore` excludes everything with copyrighted, paywalled, or answer-key content: `readings/` (textbook + article PDFs), `exams/` (quizzes, final, rubrics), `test-bank/` (publisher test bank, now nested under `exams/test-bank/` but still matched), `teaching-notes/` (lecture prep), and `_archive/`.

If you ever add a new folder that shouldn't be public, add it to `.gitignore` on its own line and confirm it with `git check-ignore -v <path>` — a real match prints the rule that caught it; no output means it's *not* excluded. Note: a `#` only starts a comment if it's the first character on the line — a trailing `# note` after a pattern becomes part of the pattern itself and silently breaks the rule (this bug is what let 283 files leak into the public repo in June/July 2026 — see the remediation note in git log / ask Claude if you need the story again).

## Build artifacts (regenerated automatically)

These are produced by `quarto render` and can be deleted at any time — they will regenerate on the next render (deleting `_freeze/` makes the next render slower because cached chunks are recomputed):

- `_site/` — rendered HTML output
- `_freeze/` — Quarto chunk cache
- `.quarto/` — Quarto internal state
- `syllabus_files/`, `slides/dayXX_files/`, `slides/dayXX_cache/` — per-document sidecars

## Building the site

From the project root:

```bash
quarto render
```

Or use the **Build** pane in RStudio. The site outputs to `_site/`.

## Where things live (workflow at a glance)

| Thing | Lives where |
|-------|-------------|
| Course website source | This folder (Quarto), pushed to `main` on GitHub |
| Live course site | GitHub Pages, published from the `gh-pages` branch via `quarto publish gh-pages` |
| Student-facing readings | Canvas modules + IU library reserves |
| My article PDFs + annotations | Zotero collection `INTL 503 — Summer 2026` |
| Textbook chapter PDFs | `readings/oatley/` (instructor only) |
| Grades, rosters, student submissions | Canvas (never in this folder) |
| Lecture prep notes for me | `teaching-notes/` |
| Exams, quizzes, rubrics | `exams/` (instructor only — never pushed) |

## Conventions

- **Slide decks** — see `slides/SLIDE-CONVENTIONS.md` for required patterns (e.g., the "Today's Plan" slide layout)
- **File naming** — `dayXX-chapterXX.qmd` for slide decks, `dayXX.qmd` for content landing pages; zero-pad day numbers
- **Archive policy** — superseded `.qmd` files go to `_archive/old-slide-versions/`; planning logs to `_archive/planning-logs/`. Don't keep `-v1`/`-v2`/`-final-final` files in the active tree.
- **No browser storage in any rendered artifact** (Quarto-side)

## TODO / future hygiene

- [x] Add a `.gitignore` — fixed (was silently broken by inline comments; confirmed working via `git check-ignore -v`) and history was reset to purge previously-exposed private material from the public GitHub repo
- [x] Decide on hosting for the live Quarto site — GitHub Pages
- [x] Delete stray local-only clutter: `PUBLISH-GITHUB.html` + `PUBLISH-GITHUB_files/`, `testfile_delete_me.txt`, `slides/day01-chapter01_cache/` all removed. (`slides/day01-chapter01_files/` was kept — it holds hand-placed images the Day 1 deck actually uses, not just render cache.)
- [ ] Migrate article PDFs to Zotero; remove `readings/articles/` once empty
- [ ] Confirm all 16 day decks are rendering cleanly end to end before the term opens

---

*Last updated: 2026-07-04*
