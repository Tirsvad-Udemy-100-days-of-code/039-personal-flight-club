# MIL-006 Framework baseline

## Metadata
| Key | Value |
| --- | --- |
| ID | MIL-006 |
| CrossReference | [BC-001], [PP-001], [MIL-005] |
| Language | en |
| Domain | education |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-11-16 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version; accepted with the Go verdict of the review record (autonomous, not independent) | [2267fc7] |

---

## Purpose

This gate decides whether Personal Flight Club has the baseline of the framework: the adopted framework release, the wiki in English, Danish and Bahasa Malaysia with the sidebar in the framework's shape (title, one list of the English pages, the Languages section last), the README in the framework template with an appendix that lists only the documents of the repository, complete licence and project URL metadata, a passing test suite, a traceability matrix and reviewed documents, merged to the default branch with a green build. The work is delivered on the branch `mil-006-baseline` and one pull request. It changes no behaviour of the program.

## Deliverable

A merged pull request that holds: the updated Business Case, Project Plan and Artifact Registry, this milestone, the new Traceability Matrix and their review records; the wiki sidebar in `docs/wiki/`; the README without the private framework files in its appendix; `pyproject.toml` with the licence expression, the project URLs, the author and a build requirement that reads the licence expression; `.editorconfig` and `.env.example` of the framework baseline (with the placeholders of the program); and the framework release adopted by the project. The program (`src/`) and its tests do not change.

## Go / No-Go Criteria

| # | Criterion (objectively checkable) | Go | No-Go |
| --- | --- | --- | --- |
| 1 | BC-001, PP-001 and MIL-006 each have an `Accepted` Version History row and a review record, and the wiki has a review record | Verdict `Go` (the wiki `Go-with-conditions` until it is checked on the host) | Any missing or `No-Go` |
| 2 | `python -m pytest` runs (the tests use fakes and need no Sheety, SerpAPI or WhatsApp account; no request leaves the machine) | Exit code 0 | Any failure |
| 3 | `docs/wiki/` has `_Sidebar.md` and the pages Home and Getting-Started in en, da and ms, each starting with the language line, and the sidebar has the title, one list of the English pages and the Languages section last, with no Related section | 6 pages and the sidebar | A page or language missing, a page without the language line first, or a sidebar of another shape |
| 4 | `framework/scripts/check-readme.sh`, `framework/scripts/check-languages.sh` and `framework/scripts/check-editorconfig.sh` run | Exit code 0 | Any finding |
| 5 | `pyproject.toml` sets `license` (a licence expression), `license-files` and the project URLs for the repository, the documentation and the issue tracker, and requires a setuptools version that reads the licence expression | All set | Any missing |
| 6 | `.env.example` holds empty placeholders for the framework tokens and still holds every variable of the README table of the program | Both present, no real value | Either missing or a real value present |
| 7 | All CI checks of the pull request | Green | Red or pending |
| 8 | The pull request carries one `Closes #N` line per task of this milestone | Every issue is closed after the merge | An issue stays open |

## Dependencies

| Depends on | Reason |
| --- | --- |
| [MIL-005] accepted | Documents and baselines the finished program, its tests, its README and its wiki |

## Traceability

| Business Case objective / KPI / user story | Reference |
| --- | --- |
| Objectives 1 to 5 | Criterion 2 (the behaviour is unchanged and its tests pass) |
| Objective 6 | Criteria 1, 3, 4, 5, 6 and 8 (documents, wiki, README, licence, environment template and issues) |
| Success criterion 7 | Criteria 1 and 7 |

## Ownership

| Role | Stakeholder ID (SA) |
| --- | --- |
| Owner | S01 |
| Approving reviewer | S01 (AI as stand-in, autonomous mode, not independent) |

## Target Date

2026-11-23: one week after the start, as the Business Case constraint for this milestone requires.

## Tasks

| # | Task | Summary | Needs its own Use Case/User Story? | Reference |
| --- | --- | --- | --- | --- |
| 1 | Adopt the framework release | Track the `framework/` submodule and `.gitmodules` (lowercase repository URL), install the skills and hooks, add `.editorconfig`, bring `.env.example` to the framework's template and keep the placeholders of the program, and ignore the AI prompt log, so the project follows the same rules as the other projects of the portfolio. | No | BC-001 objective 6 |
| 2 | Update and review the planning documents | Add this milestone to the Business Case and Project Plan, link the milestones of the git host in the plan, set the domain of the changed documents to education, bring the Artifact Registry up to date, create the Traceability Matrix and review each changed document against its QC checklist, so the plan-first gate is met. | No | BC-001 objective 6 |
| 3 | Bring the wiki to the framework's shape | Replace the three page lists of the sidebar by one list of the English pages and a Languages section and add a review record for the wiki. | No | BC-001 objective 6 |
| 4 | Bring the README to the framework template | Keep the text of the README, describe the framework files in the Overview, name the licence expression and give the appendix only the documents that are in the repository, so the README is complete and checkable. | No | BC-001 objective 6 |
| 5 | Complete the package metadata | Set the licence expression and the licence file, the author and the project URLs in `pyproject.toml` and raise the build requirement to the setuptools version that reads a licence expression, so package tools can read them. | No | BC-001 objective 6 |

---

[BC-001]: ../business-case.md
[PP-001]: ../project-plan.md
[MIL-005]: ./mil-005-documentation-and-wiki.md

---

[BC-001]: ../business-case.md
[PP-001]: ../project-plan.md
[MIL-005]: ./mil-005-documentation-and-wiki.md
[2267fc7]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/2267fc7ec4a058d6044ab320ecee62f472c15cea
