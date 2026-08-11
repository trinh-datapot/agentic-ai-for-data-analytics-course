---
description: Something changed on the running estate — classify the change, scope its blast radius, update the docs first, and exit on a dated record with a regression test.
argument-hint: the change to handle
---

# /fix — "Something changed on the running estate"

Apply a change to a handed-over project without breaking what runs: classify it, scope its **blast radius**,
update the documentation before the deliverable, and exit on a **dated change record**. Nothing is applied
un-proposed.

## Use when

The business requirement, the audience, or the data source has changed, and a running project has to follow.

## NOT for

- Something that should be right and is wrong: that is a defect. Root-cause it with `/check`, then fix at the
  layer that caused it.
- Building new: `/build-model` or `/build-report` own their layers.
- A change nobody has stated clearly: settle it with the requester first, never guess.

## Required inputs

1. The change as stated: who asked, why, and the expected outcome.
2. The documentation as it stands — cards first: `knowledge/reports/` (Report Proposal, business questions,
   report spec), `knowledge/metrics/`, `knowledge/models/`, `knowledge/sources/`.
3. For a source change: the path to the new source.

## Playbook

1. **Classify the change first, and render it as the first line of prose.**
   `change class: <new-use-case | new-audience | new-source>` — a new question, the same question at a
   different grain, or a new source. The class is rendered even when the target is still ambiguous, because
   **the wrong class scopes the blast radius wrong.**
2. **Documentation first — reuse before re-deriving.** Read the existing cards before any fresh analysis. A
   card that already answers beats re-deriving it.
3. **Scope the blast radius.** Build the table: which layer is touched, which files change, and what already
   running could be affected. Walk it in order — source card → Data Dictionary → model → measures → report
   spec → report pages. **Name the layers NOT touched**, so considered is distinguishable from overlooked.
4. **Approval gate.** Present the blast-radius table and the update plan, and stop. **Propose the fix, don't
   guess it**: never "just re-run, rebuild, or re-model" ahead of the evidence.
5. **Update the documentation before the deliverable.** Editing the deliverable and returning to the docs
   later is how the two drift; after a few rounds nobody trusts the docs.
6. **On a source change, hold one entity, one shared dimension.** A new table describing a business entity
   that already has a dimension joins the existing one. **Two tables for one entity double-count the
   numbers.**
7. **Regression test.** Capture the current values of the headline metrics **before** the change, re-run them
   after, and reconcile. Every difference has to be explainable by this change, not by something that broke.
8. **Record the exit.** Write `knowledge/records/change-<date>.md`: the change, who asked, the files updated,
   and the regression table. **The change is not done until the record exists.**

## Outputs

- The documentation and the deliverable updated in the same change.
- `knowledge/records/change-<date>.md` with the regression table.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Changing the deliverable without the matching documentation update.
- Reporting done before the regression test ran, or before the record exists.
- Widening scope past the requested change. Something else worth fixing is recorded as a proposal, never done
  in passing.
- A second dimension table for a business entity that already has one.
