# Data Inventory Index

This file catalogs the key input and scoping tables used in the regulatory burden project.
Each row represents one “artifact” that may be referenced in code, analysis, or memos.

For each file we record:
- `id`: short handle used in scripts and notes
- `filename`: relative path under `data/`
- `universe`: which part of the regulatory universe it belongs to
- `coverage`: brief description of what the file covers
- `stage`: `AI_DRAFT`, `HITL_IN_PROGRESS`, `HITL_DONE_NEEDS_EVAL`, or `HITL_FINAL`
- `notes`: any nuance worth remembering

---

## Title 34 – Non-HEA Regulations

| id                       | filename                                                  | universe            | coverage                                                                                          | stage          | notes                                       |
|------------------------|----------|----------|----------|-------|-------|
| non-hea-regs-from-title-34 | TBD  | non-HEA | only title 34 | with RAs for HITL validation | pulled with AI
---

## Title 34 – HEA / Chapter VI (placeholder)

| id                     | filename | universe | coverage | stage | notes |
|------------------------|----------|----------|----------|-------|-------|
| hea-regs-chap_VI                  |  hea_regs_capture.xlsx  | HEA      | title 34 chapter VI    | HITL_DONE_NEEDS_EVAL | run evals |

---

## Accreditation Inventory (placeholder)

| id              | filename | universe       | coverage                    | stage          | notes |
|-----------------|----------|----------------|----------------------------|----------------|-------|
| accred-regs           | accreditors_landscape_full.xlsx    | accreditation  | all accreditors found                      | HITL_FINAL    | done |
