---
description: Root the metrics upward — decompose the headline metric into a KPI tree, choose the priority set, and write the metric cards.
argument-hint: the headline KPI or the area to decompose
---

# /business-model — "Root the metrics upward"

Decide what will be measured before any data model exists: the **metric tree** rooting every metric
upward, then a priority set, then one **metric card** per priority metric — enough that someone else
recomputes the same number. Elicitation is human work: **never guess business meaning** to fill a gap.

## Use when

The business questions exist, and what is still open is which metric measures them and how that metric is
composed.

## NOT for

- Writing DAX in Power BI: use `/build-model`.
- Turning a request into a brief: use `/gather-requirements`.
- A number that is suspected wrong: use `/check`.

## Required inputs

1. `knowledge/reports/*/business-questions.md` — the axis on which a branch stays or goes.
2. `knowledge/models/*/dictionary.md` — whether a formula has real fields behind it.
3. `org-context/glossary.md` — metric names use the vocabulary already agreed.

## Playbook

1. **Name the root.** Per business question, name the headline metric and one line of rationale.
2. **Draft the strawman, every row marked.** Decompose along how the metric is composed — revenue as
   units sold times unit price — then along the analysis dimensions the data actually holds. Every row
   with no evidence in the project's documentation is marked `ASSUMPTION — for reaction only`.
3. **Present it IN CHAT as the reaction surface**, never only inside a file write: **a strawman nobody
   sees elicits nothing.**
4. **Prune what no question needs.** Every branch serves one named business question. A branch that maps
   to none is proposed for removal, with the reason. Keeping it for the look of completeness is drift.
5. **Rank by three criteria.** Per metric: does it track a business question, is it measurable, do the
   current fields support computing it. Propose the priority set and the dropped list, each drop carrying
   its reason.
6. **Approval gate.** The write happens only AFTER the human signs off the in-chat tree. Never open with
   a file-permission ask.
7. **One metric card per priority metric**, five parts: the name, a one-sentence definition, the formula,
   the unit, and how it is verified — the number that reconciles against the real data.
8. **Cross-check the dictionary.** Walk every field in every formula against the Data Dictionary. A field
   that is not there becomes an **Open Question**, each with the question that resolves it, never an
   inferred meaning.

## Outputs

- `knowledge/metrics/kpi-tree.md` — the metric tree, with the pruned branches and their reasons.
- `knowledge/metrics/<metric-name>.md` — one card per priority metric.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Authoring the business definition of a metric. **The analyst never signs meaning they invented**;
  definition belongs to the metric owner, and gaps become Open Questions.
- A fabricate-the-model ask: refuse it, and carry the alternative — the questions that would resolve it.
- Writing metric cards before the priority set is signed.
- A formula over a field that is not in the Data Dictionary.
