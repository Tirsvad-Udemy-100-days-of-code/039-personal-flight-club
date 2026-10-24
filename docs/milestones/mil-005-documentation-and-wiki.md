# MIL-005 Documentation and wiki

## Metadata
| Key | Value |
| --- | --- |
| ID | MIL-005 |
| CrossReference | [BC-001] |
| Language | en |
| Domain | it |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-24 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version | [1c49ffe] |

---

## Purpose

Decide whether the repository is ready to share with course participants and visitors.

## Deliverable

README from the framework template with run and test instructions and a screenshot, wiki pages in English, Danish and Bahasa Malaysia with screenshots, and a Doxygen build that runs.

## Go / No-Go Criteria

| # | Criterion (objectively checkable) | Go | No-Go |
| --- | --- | --- | --- |
| 1 | README follows the framework template and passes `check-readme.sh` | Pass | Fail |
| 2 | README documents creating a `.venv`, upgrading pip, installing, running and testing | Present | Missing |
| 3 | Wiki has en, da and ms pages, each with a screenshot | Present | Missing |
| 4 | Doxygen runs without errors | Pass | Errors |

## Dependencies

| Depends on | Reason |
| --- | --- |
| MIL-004 | Needs the finished program to document and capture |

## Traceability

| Business Case objective / KPI / user story | Reference |
| --- | --- |
| Objective 5 | [BC-001] |

## Ownership

| Role | Stakeholder ID (SA) |
| --- | --- |
| Owner | S01 |
| Approving reviewer | S01 |

## Target Date

2026-11-07 — within the two-week plan window of the Project Plan.

## Tasks

| # | Task | Summary | Needs its own Use Case/User Story? | Reference |
| --- | --- | --- | --- | --- |
| 1 | README | Fill README.md from `framework/templates/README-template.md`: purpose, requirements, venv setup with `python -m pip install --upgrade pip`, install, configuration, running, testing. | No | |
| 2 | Screenshots | Capture screenshots of a test run and of a sample message using mock data (no real tokens, numbers or private data visible) and store them in `docs/images/`. | No | |
| 3 | Wiki in three languages | Write the wiki following `framework/process/wiki.md` in English, Danish and Bahasa Malaysia, with the screenshots. | No | |
| 4 | Doxygen build check | Run doxygen with the Doxyfile and fix warnings in source comments. | No | |

---

[BC-001]: ../business-case.md
[1c49ffe]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/1c49ffebbd94841e90fa1ff84ba0e6bf39ea3625
