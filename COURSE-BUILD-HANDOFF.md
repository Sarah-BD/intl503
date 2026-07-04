# Course Build Handoff Note

*Lessons learned building INTL 503 (IPE, Summer 2026), written to carry into a new course project in a different folder. Paste this into the new project's instructions or drop it in the new folder so Claude starts with these conventions instead of relearning them.*

---

## How to start the new project

When you open the new course folder, before generating anything:

1. **Establish the course facts first.** Ask me (or confirm) the meeting pattern, dates, textbook/editions, assessment structure, and grade weights. Don't draft a syllabus or schedule until these are pinned. Convert any relative dates to absolute calendar dates.
2. **Save those facts to memory** as a single project file, the way the 503 facts were stored. Anything that can't be re-derived from the files later (assessment philosophy, "we reversed the Ch 12/13 pairing," etc.) belongs in memory.
3. **Set up the same folder skeleton and a README** (see below) before writing content, so files land in predictable places from day one.

## Folder structure that worked (Quarto site)

```
_quarto.yml        site config: navbar, theme, output dir
index.qmd          home page
syllabus.qmd       syllabus (rendered to site)
syllabus-canvas.html   Canvas-formatted copy for upload
schedule.qmd       daily schedule, readings, assignments
resources.qmd      student-facing resources
theme.scss         site theme
slides/            lecture decks: dayXX-chapterXX.qmd  (+ SLIDE-CONVENTIONS.md, _theme/)
content/           short daily landing pages: dayXX.qmd
assignments/       one page per assignment
readings/          instructor working copies (NOT distributed via site)
teaching-notes/    my lecture-prep notes (not published)
test-bank/         publisher test bank source for quiz items
_archive/          superseded drafts + planning logs (paper trail, not built)
_extensions/       Quarto Pandoc extensions
```

Build artifacts that regenerate and can be deleted freely: `_site/`, `_freeze/`, `.quarto/`, `*_files/`, `*_cache/`. If the folder ever goes into git, `.gitignore` these plus `.DS_Store`, `.Rhistory`, `.Rproj.user/`.

## File and workflow conventions

- **Naming:** `dayXX-chapterXX.qmd` for decks, `dayXX.qmd` for content landing pages. Zero-pad day numbers.
- **Archive policy:** superseded `.qmd` files go to `_archive/old-slide-versions/`, planning logs to `_archive/planning-logs/`. Never keep `-v1`/`-v2`/`-final-final` files in the active tree.
- **Separation of concerns:** instructor-only material (readings, teaching notes, test bank) stays out of the rendered site. Grades, rosters, and student submissions live in Canvas and never in this folder.
- **Maintain a README** at the root listing what each file/folder is for and where things live. It pays for itself every time the project is reopened.

## Slide deck conventions

The single highest-leverage thing from 503 was a `slides/SLIDE-CONVENTIONS.md` file that every deck must follow, so 16 lectures feel like one course instead of 16 separate ones. **Create the equivalent file early in the new course and read it before building any deck.** Key patterns that worked:

- **A required "Today's Plan" slide** on every deck: a one-sentence "Big Question" callout banner that frames the day's intellectual stakes (not just the topic), stacked above a table listing the day's sections with plain-language "what you'll be able to do" descriptions.
- **Section titles in the plan must match the section-divider slides exactly**, so the plan acts as a memory anchor when students hit each divider later.
- **Stack the question above the agenda, don't put them side by side** — the question deserves the visual weight, and side-by-side crops the table.
- **Keep table font sizes consistent across decks** so visual weight matches.
- Let the conventions file grow as new cross-deck patterns emerge (divider styling, article-discussion layouts, exam-review patterns).

## Assessment philosophy

For 503 I moved away from take-home writing and policy memos toward **in-class assessment** — quizzes, a final, short in-class writing prompts graded credit/no-credit, and a student-led article presentation. The motivation: reduce AI-use concerns and keep engagement high in a compressed format. Carry this default into the new course unless the format argues otherwise, and don't reintroduce take-home reflection papers or memos without flagging it.

## How I like you to work

- **Be concise and direct.** Cut words that don't change the meaning. No preamble like "Let me…" or "Now I'll…".
- **No hedge language when asking for feedback.** Don't say "let me know how it lands," "curious what you think," or "happy to iterate." Either ask the real question — "does this work?" — or just stop.
- **Flag, don't silently fix.** If a deck is missing a required convention or a fact looks stale, say so and offer the fix rather than quietly changing things.
- I'm a mixed-methods political scientist (IR/IPE). Pitch explanations accordingly.

---

*Source course: INTL 503, Summer 2026. Adapt dates, textbook, and assessment specifics to the new course; keep the structure, conventions, and working style.*
