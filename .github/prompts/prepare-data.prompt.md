---
description: Shape a profiled source into clean, model-ready tables, with a prep log carrying the map and the why.
argument-hint: the table or the file to clean
---

# /prepare-data — "Shape the data for the model"

Turn a signed-off source into clean, **model-ready tables**: the analyst signs the business rules and the
grain, the agent does the work, and it exits on the prep rationale. The keystone: **nothing touches the
real data un-proposed**, and the prep log carries the map and the why.

## Use when

Writing or fixing the cleaning layer: type cleanup, inconsistent labels, one column holding several
facts, a matrix-shaped table that has to be unpivoted to long form, dedup.

## NOT for

- Profiling a source: use `/profile-sources` first.
- Measures and formulas: use `/build-model`.
- One number to answer one question: use `/quick-analysis`.

## Required inputs

1. A **signed source card** in `knowledge/sources/` carrying the recorded `dq:` issues. No source card
   is **STOP + propose `/profile-sources`**.
2. The Data Dictionary in `knowledge/models/` — above all its PII column.
3. The business questions in `knowledge/reports/` — which issues matter, and which are left alone.

## Playbook

1. **Mask the PII first.** Read the PII column in the Data Dictionary, name the columns that will be
   dropped or replaced by an anonymous key, and do that before any other transformation. The raw values
   of those columns are never displayed and never written to any file.
2. **Decide the shape — propose-first, render it in the reply.** Before any transformation is written,
   render the plan: one row per table, with the issue, the treatment, the declared **grain** afterwards,
   and the expected state. Name **where each business rule lives** — fixed in the data now, or left to a
   measure later. Name the issues **deliberately left alone** because they do not touch the business
   questions; that is the decision record, not an oversight.
3. **Approval gate.** Stop for the analyst to sign the plan. No data changes before it is signed.
4. **Build step by step, record every step.** One line per step: the table, the column, the treatment,
   the rows affected. A step not recorded is a step nobody can repeat.
5. **Reconcile.** Per prepared table, verify **row counts and one column total** against the source, and
   cite both — before and after. Every difference has to be explainable.
6. **Exit on the prep log.** Write `knowledge/models/<model-name>/prep-log.md`: the steps, the
   reconciliation numbers, and the deliberately-unfixed issues with the reason for each.

## Outputs

- The prepared tables in `data/clean/`. The raw data in `data/raw/` is left untouched.
- The prep log in `knowledge/models/<model-name>/prep-log.md`.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Reading, displaying or writing out a raw PII value.
- Writing over the raw data in `data/raw/`.
- Cleaning at large, past what the project's business questions need.
- Transforming without recording the step, or reporting done before the reconciliation is cited.
