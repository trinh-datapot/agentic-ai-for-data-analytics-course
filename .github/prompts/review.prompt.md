---
description: Red-team the build before certification — hostile lenses, an evidence filter, and one GO / CAUTION / STOP recommendation.
argument-hint: the scope to review, for example the whole project before Checkpoint 1
---

# /review — "Red-team this before certification"

Try hard to **break** a model and its report before it is certified — wrong metric definitions, data-failure
modes, needless complexity — then let the human adjudicate. review states findings and one recommendation;
**it never fixes**.

## Use when

Before a certification gate: moving stage, handing over to someone else, or letting a report go outward.

## NOT for

- Verifying one number or one measure: use `/check`.
- Fixing what was found: the skill that owns the broken layer does that.
- A review with nothing built yet: finish the work first.

## Builder ≠ reviewer — the hard LAW

The builder does not adjudicate their own build. In this course the builder and the reviewer are the same
person, so the law holds as a **method constraint**: the reviewer runs the lenses **sequentially, each a
clean pass, explicitly not reusing the build rationale**, starting over from the evidence in the files and
in the model. A finding that rests on "it was done right at build time" carries no weight.

## Required inputs

1. The checklist or the criteria of the gate being faced.
2. Everything inside scope: the context store, the source card, the Data Dictionary, the metric cards, the
   model card, the prep log, the test log.

## Playbook

**RENDER-THEN-GATE.** Render the review scaffold — scope, the lenses, the builder≠reviewer check — and STOP
for scope confirmation. Do **not** read the data and the model until the human confirms scope.

1. **Scope.** Which solution, and which gate it faces.
2. **Approval gate.** Wait for the scope to be confirmed.
3. **Run the hostile review, one lens per pass.** Four lenses: the data and its source documentation · the
   model and its relationships · the formulas and their numbers · the completeness of the documentation.
   **Hostile stance, findings only — no fixes.** Each pass is clean and never reuses the conclusion of the
   pass before it.
4. **Evidence filter.** **Auto-reject** any finding that does not cite a **file and line**, a table or
   measure name, or **a result against an independent baseline**. No evidence, dropped. **Cap surviving
   findings at 15, most-severe first.** Each records the problem, the evidence, the consequence of letting
   it stand, and the skill that owns the fix.
5. **One recommendation, the human keeps the gate.** **GO / CAUTION / STOP, never a pass/fail** — the
   sign-off belongs to the analyst. Offer the adjudication: apply all, review each, or reject all. Confirmed
   defects route to the owning skill; **the reviewer never edits the cards.**

## Outputs

- The review record at `knowledge/records/review-<date>.md`: the scope, the findings with their evidence,
  and the recommendation.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Changing anything inside a review run.
- A surviving finding with no citation.
- A GO recommendation while a severe finding is still open.
- Leaning on the build rationale to conclude that something is right.
