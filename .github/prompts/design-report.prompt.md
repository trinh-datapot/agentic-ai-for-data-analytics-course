---
description: THE design gate — turn an approved brief into a locked, implementable report spec before any page is built.
argument-hint: the report to design
---

# /design-report — THE design gate (before the build)

Turn a signed brief into an approved, implementable design: which question each page answers, which chart
carries it, which measure it reads, under which interface conventions. **The spec is the ONE contract**, and
this gate runs before any report page exists.

## Use when

Designing pages and layout from a brief, with the business questions, the metric set and a verified model
already in hand.

## NOT for

- No signed brief yet: `/gather-requirements` first.
- Implementing an approved design: use `/build-report`.
- An HTML deliverable of findings that already exist: use `/quick-analysis`.

## Required inputs

1. A **signed** brief: `knowledge/reports/*/report-proposal.md` and `business-questions.md`. None means
   STOP and propose `/gather-requirements`. Its **data-shape gate must be checked** — unchecked sends the
   work back there, not forward.
2. `knowledge/metrics/` — the priority metric cards, so each question has the metric that answers it.
3. `knowledge/models/*/model-card.md` — the tables, relationships and measures that really exist.
4. The project's interface conventions where there are any: theme colours, font, page size.

## Playbook

1. **Inputs before bindings.** Read the model inventory with the profiling evidence beside it, then per
   business question check three things: a metric answers it, that metric already has a measure, and the
   grain supports the cut the question needs. **Design binds only to measures and columns that exist, or
   that are named as prerequisites: page questions may precede the model, bindings may not.** Anything
   short is named now, never discovered at build time.
2. **Feed the org inputs.** Business: who reads each page, the situation in which they open it, the question
   it answers. Technical: page size, the theme colours and font, the naming conventions for pages and
   visuals. Experience: the information hierarchy — where the totals sit, where the detail sits.
3. **Plan the pages.** One row per page: the name, its readers, the question it answers, the metrics it
   uses, and the flow from this page onward.
4. **Chart selection — by question type, with the reason.** Every visual records the question it answers,
   the measure it reads, and the dimension it cuts by. **Never a chart proposed because it looks good.**
5. **Approval gate.** Present the whole spec in the reply and stop for approval. Nothing is written, and
   **no page whatsoever is built, before the spec is approved** — chat approval is not the sign-off; the
   spec carries it.
6. **Write the locked spec.** `knowledge/reports/<report-name>/report-spec.md`: the three groups of
   requirements, the page plan, and per page every visual with its question, measure and dimension. Once
   locked and signed, `/build-report` implements it and never re-designs.
7. **Name what is not designed in this round**, with the reason, so an unresolvable claim ends as a
   **descope** on the record rather than a hopeful signature.

## Outputs

- `knowledge/reports/<report-name>/report-spec.md`, signed.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Building a page in this run. Design and build are two jobs; the build is `/build-report`.
- A visual bound to a measure or column that does not exist in the model.
- Writing the spec before it is approved.
- A chart with no question behind it.
