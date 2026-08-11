---
description: Turn the ask into a buildable brief — report context, business questions, and a Report Proposal with testable acceptance criteria.
argument-hint: the report request to clarify
---

# /gather-requirements — "turn the ask into a buildable brief"

Produce the brief: the report context (WHY and for WHOM) → the business questions (WHAT) → testable
acceptance criteria and the NOT-list. The posture is **ADVISORY**: load the project's own documentation,
draft recommendations, confirm by exception, never interrogate the requester with questions the
documentation already answers. An intake ends as **acceptance criteria, never a wish list**; what nobody
can answer is marked as an assumption, never invented.

## Use when

Defining scope and acceptance criteria before a build: there is a request, but who uses it, which
decision it serves, and what counts as done are all still open.

## NOT for

- A vague ask that needs settling with the requester first: that conversation comes before this skill.
- Page layout and chart design: that is the design gate, `/design-report`.
- A Report Proposal already approved, with one detail to change: edit the file, never re-run.

## Required inputs

1. `org-context/org-profile.md` — the project's business requirement.
2. `org-context/glossary.md` — every term in the brief uses the name agreed here.
3. `knowledge/models/*/dictionary.md` and `knowledge/sources/` — the inventory the data-shape gate walks
   at the end.

## Playbook

1. **Capture the ask verbatim.** Copy the request as it was given, with no interpretation, so the brief
   can be reconciled against the original ask later.
2. **Frame the report context, four parts.** The audience · the situation to solve · the decision it
   serves · the expected outcome. Infer from the project's documentation first, then SHOW the inferences
   for a one-glance veto, rather than asking each cell blank.
3. **Advisory draft.** Every cell is a recommendation plus its rationale. A cell with no evidence and no
   practice behind it is marked `ASSUMPTION — for reaction only`, never quietly filled.
4. **Confirm by exception — ≤3 questions per round.** The questions are **VETOES**: "here is the
   recommendation and why, confirm or adjust", never blank elicitation of what the documentation already
   answers. An answer assumed on the requester's behalf is read out as an assumption at sign-off.
5. **Write the business questions.** Each states who reads the answer, which decision it serves, and
   which metric measures it. Each must be measurable against the data at hand.
6. **Acceptance-criteria discipline.** Every criterion is testable: **a number, a file, or a visible
   state. No adjectives** — not "visual", not "easy to read", not "complete".
7. **Approval gate.** Show the drafted sections in the reply, under their own section names, before
   anything is written to file. Persisting waits for the requester's go-ahead; showing the content never
   waits for it.
8. **Data-shape gate — "can the data carry the story?"** Checked BEFORE any design. Per business
   question, walk the brief against the Data Dictionary and the source card: the grain exists, the needed
   fields exist or are derivable, comparison baselines exist. Each failing row is decided by the human:
   **descope the question, or insert the prerequisite** data-preparation step as a named step.

## Outputs

- `knowledge/reports/<report-name>/analysis-requirement.md` — the four-part report context.
- `knowledge/reports/<report-name>/business-questions.md` — the business questions.
- `knowledge/reports/<report-name>/report-proposal.md` — objective, audience, questions answered,
  metrics, scope, the NOT-list, acceptance criteria.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Inventing stakeholder meaning. What has to be guessed is marked as an assumption and read out.
- Writing files before the draft is approved.
- Acceptance criteria written as adjectives instead of something testable.
- Skipping the data-shape gate. A brief the data cannot carry is not buildable.
