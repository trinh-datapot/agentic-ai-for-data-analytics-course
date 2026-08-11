---
description: Implement the approved design — build the report pages verbatim from the signed spec, then verify the numbers on the page.
argument-hint: the page to build, or the part to change
---

# /build-report — "implement the approved design"

Turn an approved design — a signed `report-spec.md` from `/design-report` — or a page edit into real pages.
**This playbook never re-designs: it implements the spec verbatim; a design change routes back to
`/design-report`.**

## Use when

Building or editing report pages, visuals and slicers against a signed spec.

## NOT for

- No signed spec: use `/design-report` first.
- A different chart type or layout than the spec: back to `/design-report`, never changed here.
- A measure or a relationship in the model: use `/build-model`.
- A number on the page that looks wrong: use `/check`.

## Required inputs

1. The locked `knowledge/reports/*/report-spec.md`, and only **if it carries its sign-off**: **a spec-shaped
   file without it is NOT consumable** — that routes back to `/design-report`. Locked means consume, never
   re-plan.
2. An MCP connection to the right open Power BI project (`.pbip`).
3. `knowledge/models/*/model-card.md` — the real measure and column names. An edit reads the report card
   first: the built page is the reference.

## Playbook

1. **Confirm the project before anything else.** List the existing pages and have the analyst confirm this
   is the project's report. The wrong target clobbers another report.
2. **Re-read the spec and state the scope of this run.** Which page, which visuals, and the question each
   visual answers. Where the spec lacks what the build needs, ask; never settle it here.
3. **Approval gate.** Present the scope and the visual list, and stop before touching the report.
4. **The draft-build gate — minimal decoration first.** Build the bindings and the layout from the spec with
   no colour or formatting work yet, then review the real render against the spec's reasoning: per page, the
   question it answers. **Polish comes after the numbers are right.** A small edit to an existing page skips
   this gate.
5. **Reconcile the numbers on the page against the measures.** Per visual, compare what is displayed with
   the result computed straight from the measure. Report every difference.
6. **Apply the theme and finish the formatting** once the numbers are right: colours per the convention,
   meaningful titles, number formats and units. The theme owns the chrome — never hand-set what it rules.
7. **Coverage re-walk.** Walk the spec row by row against the BUILT visuals: every question is realized by a
   placement, or recorded as descoped. **An orphan is a build gap fixed before sign-off** — a defect of the
   build, not of the spec.
8. **Exit on the report card.** Write `knowledge/reports/<report-name>/report-card.md`: the pages built, the
   visuals and their questions, and the reconciliation results.

## Outputs

- The report pages saved, the changes landing in `<Name>.Report/`.
- The report card in `knowledge/reports/<report-name>/report-card.md`.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Changing the chart type, the layout or the scope against the signed spec. Drift here is a build bug.
- Building while the spec is unsigned.
- "Done, verify later": reporting done before the numbers were reconciled against the measures.
- Adjusting a visual's filters so the number matches the expectation, instead of root-causing the difference.
- A visual bound to a measure or column that does not exist in the model.
