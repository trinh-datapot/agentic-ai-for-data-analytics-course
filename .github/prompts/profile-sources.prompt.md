---
description: Meet a data source for the first time, profile it safely, and exit on a source card.
argument-hint: the file or the table to profile
---

# /profile-sources — "Meet the source"

Meet a data source for the first time: profile it safely, distill what may be committed, and exit on a
source card. The keystone discipline: **real values live and die in the temp zone — only structure
leaves it.**

## Use when

Finding out what is actually in a source: which tables, which columns, the types, how much is missing,
duplicates, out-of-range values.

## NOT for

- An ad-hoc data pull: use `/quick-analysis`.
- Shaping and cleaning the data: use `/prepare-data`.
- A live card that already answers the question: **re-read the card, no probe.**

## Required inputs

1. `knowledge/sources/` first. If a live card already answers, exit with the card confirmed and profile
   only the gap.
2. `org-context/glossary.md` — the business vocabulary, so the fields are named the way this org names
   them.
3. The project's business documentation where one exists, to know which fields matter to the problem.
4. `knowledge/models/<model-name>/dictionary.md` where one already exists, read before the exit step
   updates it. The analyst names the target model.

**Never run against a source the analyst has not named.**

## Playbook

1. **Name the PII before the data is read.** List the fields that can identify one person: full name,
   email, phone, address, personal ID number. Report that list before anything else happens.
2. **Safe profile — aggregates only, safe by construction.** Per table: row counts, null %,
   distinct/uniqueness, duplicate rows, and the value range of the numeric and date columns. Never a raw
   value of a PII field.
3. **Every issue carries counted evidence.** How many rows, in which column. No evidence, not an issue.
4. **Capture the source baseline.** Per table that will be used: row counts, the sum of the key numeric
   column, and the time window when the table has a date column — aggregates only. Freeze it **before
   the data is cleaned or transformed**: this is the ONLY thing `/check` reconciles against later.
   Without it, `/check` has nothing independent to compare.
5. **Approval gate.** Present the issues and propose **up to 10 `dq:` rules**, seeded by what the
   profile surprised you with, then stop for the analyst to choose which ones to keep. Keep only what
   touches the project's analysis questions.
6. **Exit on the source card.** Write `knowledge/sources/<source-name>.md`: the source information
   (file, how it was obtained, when it was profiled), the structure of every table and column, the
   agreed `dq:` rules, and the **"What we take"** table naming the tables this problem will use.
7. **Coverage — name what is not taken.** For every table NOT carried into "What we take", state one
   line of reason. Never silently skipped.
8. **Doc-sync the Data Dictionary.** From the structure just profiled, update
   `knowledge/models/<model-name>/dictionary.md`: one row per field of every table carried into "What we
   take", with the table, the field, the data type, its meaning, and whether it is PII. The dictionary is
   **derived from the card, never typed twice**. Meaning comes from the glossary and the business
   documentation: a field nobody can explain becomes an Open Question, not a guessed row. An existing
   dictionary is updated in place, row by row, never overwritten wholesale.

## Outputs

- A source card in `knowledge/sources/`, its source-baseline section filled.
- `knowledge/models/<model-name>/dictionary.md` covering the fields of the tables taken, each row marked
  for PII, with the unexplained fields left as Open Questions.
- The detailed profile, where it runs long, kept in `work/`. It never enters the card.
- The advisory footer: `artifacts:` · `state:` · `suggested next:` — a suggestion, never auto-run.

## Guardrails

- Lifting a raw PII value into the card, into another file, or into the reply. **Refuse and carry the
  alternative**: report the aggregate, or mask the field.
- A conclusion about data quality with no counted evidence behind it.
- Capturing the source baseline after the data was cleaned. A late baseline is not an independent one.
- Overwriting a source card, or a dictionary, the analyst has not approved.
- Guessing the meaning of a field to fill the dictionary row, or letting the dictionary drift from the
  structure recorded in the source card.
