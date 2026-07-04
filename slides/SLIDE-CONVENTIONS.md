# INTL 503 — Slide Deck Conventions

This document defines required patterns for every lecture slide deck in this course. Read this before creating or editing any `dayXX-chapterXX.qmd` file.

## The "Today's Plan" Slide

**Every lecture deck must include a "Today's Plan" slide at the end of the Course Logistics section, immediately before the first substantive content section (e.g., before `# Defining IPE` on Day 1 or its equivalent on later days).**

The slide has two stacked elements:

1. **A Big Question callout banner** at the top — a single sentence that frames the day's intellectual stakes.
2. **A kable table** below it listing the day's sections with substantive descriptions.

### Canonical structure

```markdown
## Today's Plan

::: {.callout-important appearance="minimal" icon=false}
## Today's Big Question
**[One sentence framing the day's intellectual stakes — what is the question this lecture is trying to answer?]**
:::

​```{r}
#| label: tbl-plan

plan <- data.frame(
  Section = c("1 · [Section title 1]",
              "2 · [Section title 2]",
              "3 · [Section title 3]",
              "4 · [Section title 4]",
              "5 · [Section title 5]",
              "6 · [Section title 6]"),
  Cover = c("[Plain-language description of what students will learn or be able to do]",
            "[Plain-language description...]",
            "[Plain-language description...]",
            "[Plain-language description...]",
            "[Plain-language description...]",
            "[Plain-language description...]")
)

kable(plan, col.names = c("Section", "What we'll cover"),
      align = c("l", "l")) %>%
  kable_styling(font_size = 22, full_width = TRUE) %>%
  row_spec(0, bold = TRUE, color = "white", background = iu_crimson) %>%
  column_spec(1, bold = TRUE, color = iu_crimson, width = "32%") %>%
  column_spec(2, width = "68%")
​```
```

### Rules for writing the Big Question

- One sentence, not two.
- Bold inside the callout body.
- Should frame the intellectual stakes — what is at stake or what is interesting about the day's material — not just restate the chapter topic.
- Examples that work: "How does the global economy shape your life — and how do you shape it back?" (Day 1, Ch. 1); "If free trade benefits everyone, why is it so politically difficult?" (Day 2, Ch. 2 — already used as the Day 1 "Looking Ahead" preview).

### Rules for writing the section rows

- The **Section column** must use the exact text of the corresponding section divider slide (the `# Section Name {background-color="#990000"}` slides). Students need to recognize the transitions when they appear later in the deck.
- The **What we'll cover column** must be written in plain language and tell students what they will know or be able to do after the section — not restate the section title in different words.
- Avoid jargon, abstract restatements, and procedural phrasing ("Application" or "Discussion") in this column. Concrete is good: "Smith, List, and Marx on the politics of trade" beats "Founding thinkers."
- Each row's "What we'll cover" cell should be one short sentence or phrase, roughly 8–12 words.

### Why this layout

- **Stacked, not side-by-side.** Putting the question and the agenda in two columns creates a balance problem — the table either gets cropped or shrunk, and the question loses prominence. Vertical stacking gives each its own real estate.
- **Question first.** The Big Question is the intellectually weighty content and deserves the visual prominence. It primes the audience for the lecture and anchors the agenda below it.
- **Section titles match section dividers.** When students hit the `# Defining IPE` crimson divider 10 slides later, they should recognize "Defining IPE" from this slide. The plan acts as a memory anchor.
- **`font_size = 22` matches the deck's other tables** (Assignments Overview, Session Structure) so visual weight is consistent across the deck.

---

## Other Conventions (Add as They Emerge)

This file should grow as more cross-deck conventions get established. Future entries might include: section-divider styling, lecture opening slides, scholarly-article-discussion slide layouts, exam-review patterns, etc.
