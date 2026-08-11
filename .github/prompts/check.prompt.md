---
description: One verb for verification — pick a mode (which surface) and a depth (how hard), then conclude with cited evidence.
argument-hint: what to verify, and against what — for example the Revenue measure
---

# /check — "Is this right / safe?" (one verb, mode × depth)

One verb for every verification short of a full red-team: pick a **mode** (which surface) and a **depth**
(how hard you look). **check reports, it never fixes** — findings route to their owning skill.

## Use when

Checking whether a number, a measure, a relationship or a file is right, root-causing a wrong number, or
scanning for PII before something is shared.

## NOT for

- A full red-team review before certification: use `/review`.
- Fixing what was found: the owning skill does that, `/build-model` for a wrong measure.
- Creating a measure: use `/build-model`.

## The matrix — mode × depth

**Mode = which surface** you point the check at; **depth = how hard** you look. The two are orthogonal:
any mode runs at any depth.

| Mode | Surface it verifies |
|---|---|
| data | source / prep data quality (row counts, grain, freshness, reconcile) |
| model | relationships, cardinality, star conformance |
| dax | measure correctness vs an independent baseline |
| safe | PII / safe-to-share, before anything leaves |

Depth: **quick** (spot PASS/FAIL) · **standard** (the default, evidence-checked reconciliation) ·
**investigate** (root-cause dive on one disputed number → verdict → hand the fix over).

## Required inputs

1. The target, named by the analyst. No target is a question back, never a guess.
2. The metric card in `knowledge/metrics/`: a governed metric resolves through its card first.
3. An **independent baseline**: the source baseline frozen at profiling time, the prep log, or a number
   computed straight from the raw data file.

## Playbook

**RENDER-THEN-GATE.** Render the check plan before running anything — name the **mode**, the **claim +
threshold** (exact, or the tolerance), and the **independent baseline** you will reconcile against — so the
human sees what will be checked and how.

1. **Scope and pick the mode.** Name the cited target per the evidence rule: the file, the table, the
   measure.
2. **Pick the depth.** quick · standard · investigate.
3. **Run read-only — benchmark, never trust.** **An agent-authored number is reconciled against an
   INDEPENDENT baseline, never its own re-run.** For a profiled source that baseline is a committed
   artifact: the source baseline frozen at profiling time. A source never profiled with a baseline is the
   fallback case — say so in the row, then reconcile live. Nothing is modified during a check.
4. **Exit on structured evidence.** Results land in the **test log**: one row per item, with the value at
   hand, the baseline value, **PASS / FAIL / BLOCKED**, and the source of the baseline. An item that cannot
   be checked is **BLOCKED, never silently skipped**. **No citation, no claim.**
5. **Root-cause every FAIL.** Name the layer that is wrong — the source data, a cleaning step, a
   relationship, or the formula — and cite the evidence for that verdict.
6. **Route the finding — never fix here.** Close on the verdict plus the skill that owns the fix, and let
   the analyst decide. check's own exit is the verdict and its evidence, with nothing mutated.

## Outputs

- The test log at `knowledge/models/<model-name>/test-log.md` when the analyst asks to keep it.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Changing anything inside a check run.
- A PASS with no independent baseline behind it.
- A skipped item with no BLOCKED row and no reason.
- A PII value in the test log.
