---
description: Build or change the semantic model over MCP — tables, relationships and DAX measures, each measure traced to a metric card.
argument-hint: the part of the model to build or change
---

# /build-model — "Build or change the semantic model"

Shape the star-schema semantic model — tables, relationships, measures, DAX — with **every measure traced
to a metric card**. Propose-first is the keystone: **render the design in the reply and get sign-off
BEFORE anything touches the model.**

## Use when

Creating or changing a table in the model, a relationship between tables, a DAX measure, or the marking of
the date table.

## NOT for

- Cleaning the data before it is loaded: use `/prepare-data`.
- Deciding what to measure: use `/business-model`.
- A number that is suspected wrong: use `/check`.

## Required inputs

1. **The metric-card entry gate**: `knowledge/metrics/` holds the priority metric cards, each with its
   formula and how it is verified. A measure with no card behind it does not get built.
2. `knowledge/models/*/dictionary.md` — the real table and column names.
3. An MCP connection to the right open Power BI project (`.pbip`).

## Playbook

1. **Confirm the model before anything else.** List the tables in the connected model and have the analyst
   confirm this is the project's model. **The wrong target overwrites another model** — every later
   operation lands in the wrong place.
2. **Confirm the star — grain first.** State what one row of the fact table is: one unit sold, or one line
   item on an order. **The wrong grain makes every number downstream wrong.** Name the dimensions shared
   across facts, and hold the **date-table law**: a model with time analysis has one marked date table.
3. **Render the design in the reply.** Building a model: the fact and dimension tables, and the
   relationship table with the key columns on both sides, the cardinality, and the filter direction.
   Writing a measure: the full DAX expression plus one line on how it works.
4. **Approval gate.** Stop for the analyst to sign the rendered design. Nothing is applied before it.
5. **Execute over MCP.** Create exactly what was signed. Mark the date table where the model carries time
   analysis.
6. **The smoke gate — the transient-edit trap.** An MCP edit is transient until it is **serialized back to
   `<Name>.SemanticModel/definition/`**; confirm the files changed on disk, not just the live model. Then
   run at least two probes: count the fact rows and reconcile against the source, and total one metric
   along one dimension against the overall total. **The two totals must match.** On a difference, name the
   suspected layer — usually the filter direction, or duplicate keys.
7. **Exit on the model card.** Write `knowledge/models/<model-name>/model-card.md`: the tables, the
   relationship table, the measures with their formulas, and the results of both probes.

## Outputs

- The model saved, the changes serialized into `<Name>.SemanticModel/definition/`.
- The model card in `knowledge/models/<model-name>/model-card.md`.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Touching the model before the target is confirmed, or before the design is signed.
- Reporting done before the probes ran, or while the edits are still transient.
- A bidirectional relationship with no stated reason and no separate sign-off: bidirectional filtering is
  the common cause of double-counted numbers.
- A snowflaked dimension with no reason recorded.
- A measure over a table or column name that does not exist in the model.
