---
description: A quick ad-hoc analysis, a cut of our numbers rendered into a self-contained HTML page.
argument-hint: the business question to answer, or the report card to build
---

# /quick-analysis — "Show me the numbers / make it shareable"

Render cited analysis into a self-contained HTML deliverable, computed from the project's real data.
One exit only, a rendered page, and **never a raw-row dump**.

## Use when

Pulling a number or a cut — "revenue by region this year" — or turning the questions already listed in
a report card into a deliverable.

## NOT for

- A definition or lineage question: answer it from `org-context/glossary.md` and the source card.
- A wrong number: use `/check`.
- A Power BI report page: that is `/build-report`, in the later sessions.

## Required inputs

Cards first. Before any number is computed, read:

1. `org-context/org-profile.md` and `org-context/glossary.md` — who the business is, and how each term
   is understood here.
2. The source card in `knowledge/sources/` — what each column means, and the caveats that ride with it.
3. The metric card in `knowledge/metrics/` when the question touches a governed metric.
4. The report card in `knowledge/reports/` when a specific report is named.

Context that is missing is asked for, never guessed.

## Playbook

1. **Scope the cut.** Name it back: which question is answered, who reads it, which file the data comes
   from.
2. **Render the calculation before running it.** Per question: the columns, the arithmetic, the filters.
   A column carrying a caveat in the source card is surfaced here, not after the fact.
3. **Approval gate.** Present the scope and the calculation, and stop for the analyst's go-ahead.
   Nothing renders before it.
4. **Compute against the real data.** Read the data file itself. No estimate, and no number carried over
   from an earlier turn.
5. **Render the deliverable — self-contained, cited HTML.** One chart per question, each with one line
   of reading. The source data file and the render timestamp are cited at the foot of the page. Content
   must already exist in the cards: **a number with no card behind it stops at the evidence rule**.
6. **Self-verify.** Report the baseline the analyst reconciles against: the total of the headline metric
   across the whole dataset, and the row count read. Excluded rows are named, with the reason.

## Outputs

- One HTML file in the session folder, named after what it answers.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- **Refuse a raw-row or PII ask**, and carry the alternative: the aggregate, or the masked field. A
  refusal never dead-ends.
- A number in the deliverable that cannot be computed from the data in the repo.
- Editing the source data. Intermediate results land in `work/`, which is never a source of truth.
