# Business Case

## Metadata
| Key | Value |
| --- | --- |
| ID | BC-001 |
| CrossReference | [SA-001], [PP-001], [MIL-006] |
| Language | en |
| Domain | education |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-24 | Deprecated | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version | [1c49ffe] |
| 2026-11-16 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Added objective 6, success criterion 7, a scope item, an out-of-scope item, a risk and a constraint for the baseline milestone MIL-006; corrected the owner name in the hosting URL; set the domain to education; reviewed in autonomous mode, not independent | pending |

---

## Executive Summary

Day 39 of Udemy's "100 Days of Code: The Complete Python Pro Bootcamp" is a capstone: a flight-deal finder. The program reads destinations and price limits from a Google Sheet (through Sheety), searches the cheapest return flight for the next six months (SerpAPI Google Flights, or the course's mock flight service), and sends a WhatsApp message when a price is below the limit. This project delivers that program as a small, tested, documented Python 3.13+ repository for the course participant and for other participants who compare solutions.

## Methodological and Standards Foundation

The work follows the SQA and QC framework mounted at `framework/`: artifacts are reviewed against QC checklists tagged with ISO/IEC 25010:2023 characteristics, and code follows the `coding-conventions` and `clean-architecture` skills. Source code is documented with Doxygen comments and tested with pytest.

## Problem Statement

Finding a cheap flight by hand means checking many dates and destinations every day. The course assignment asks for the automation, but the starter files are empty stubs and the assignment text mixes several APIs. Without a plan the result is untested, may hold secrets in code and is hard for other participants to run.

## Business Opportunity

A clean reference solution lets the participant finish the course and reuse the repository as a portfolio piece. Other participants (S02) and GitHub visitors (S03) get readable code with the assignment's function names and clear run instructions.

## Objectives

1. Read destinations (city, IATA code, lowest price) from Sheety and update the lowest price when a cheaper flight is found.
2. Find the cheapest flight from tomorrow to six months ahead for every sheet row, from SerpAPI or the mock flight service.
3. Send a WhatsApp message with price, origin, destination and both dates when a flight is cheaper than the sheet price.
4. Keep secrets in `.env`, never in the repository, and cache API responses to save free-tier quota.
5. Publish a documented repository: README, wiki in English, Danish and Bahasa Malaysia with screenshots, Doxygen configuration, CI workflows, description and topics.
6. Bring the finished project to the common baseline of the framework: the adopted framework release, the wiki sidebar in the framework's shape, complete licence and project URL metadata, a README that lists only the documents of the repository, a traceability matrix and review records for every changed document ([MIL-006]).

## Scope

### In Scope

- Python 3.13+ project with `src/` and `tests/`, `pyproject.toml`, a local `.venv`, pytest, `constants.py`, a Doxyfile and a Python `.gitignore`.
- The assignment classes: `DataManager`, `FlightSearch`, `FlightData` with `find_cheapest_flight()`, `NotificationManager`, and `main.py`.
- Response caching with `requests_cache`, and WhatsApp delivery through the participant's logged-in WhatsApp Web session.
- README from the framework template, wiki in three languages, screenshots, CI workflows from the TirSystem workflow repository, repository description and topics.
- The baseline milestone [MIL-006]: the framework release, the wiki sidebar in the framework's shape, the README without the private framework files in its appendix, licence and project URL metadata, `.editorconfig`, `.env.example`, review records and a traceability matrix. It changes no behaviour of the program.

### Out of Scope

- Twilio SMS or WhatsApp (replaced by the WhatsApp Python module).
- Automated tests that call the real Sheety, SerpAPI, mock-flight or WhatsApp services, or that read the real `.env`.
- A user interface, a database, scheduling of the daily run, and booking of flights.
- Any change to `src/` or `tests/` in the baseline milestone [MIL-006].

## Expected Benefits

### Tangible Benefits

- A working, runnable capstone solution with automated tests.
- A repository other participants can clone and run from the README alone.

### Intangible Benefits

- Practice with OOP, APIs, datetime, caching and environment secrets.
- A reusable template for later course days.

## Strategic Alignment

The project supports the participant's learning goal (completing the bootcamp) and the shared goal of publishing readable solutions that others can learn from.

## Success Criteria

| # | Criterion | Target | Measure |
| --- | --- | --- | --- |
| 1 | Unit tests pass | 100% of tests pass, no network or `.env` access | `pytest` exit code 0 |
| 2 | Run instructions work | A fresh clone runs by following the README steps only | Manual run of the README steps |
| 3 | Notification content | Message holds price, origin, destination, out date and return date | Unit test on the message text |
| 4 | Repository metadata | Description and at least 5 topics set | Check on the git host |
| 5 | Wiki languages | en, da and ms pages exist, each with screenshots | File review |
| 6 | Runtime dependencies | Only packages the assignment needs | `pyproject.toml` review |
| 7 | The baseline milestone is done (objective 6) | The wiki sidebar has the framework's shape, `framework/scripts/check-readme.sh`, `framework/scripts/check-languages.sh` and `framework/scripts/check-editorconfig.sh` exit with code 0, 100 % of the continuous integration (CI) checks of the pull request of [MIL-006] pass | Files in `docs/wiki/`, the script exit codes and the pull request status on the git host |

## Risks

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Free-tier quotas run out (SerpAPI 100/month, Sheety 200/month) | Development stops | Cache with `requests_cache`; use the mock flight service; keep 3 to 5 destinations |
| Secrets committed by mistake | Credential leak | `.env` and cache files in `.gitignore`; only `.env.example` committed; secret scan before each PR |
| WhatsApp Web automation is fragile (needs a browser and a logged-in session) | Notification fails | Import the module lazily; isolate it behind `NotificationManager`; print the message on failure |
| The WhatsApp module differs from the participant's intent | Rework | Assumption recorded below; the module is used in one function in one file |
| CI workflows from the TirSystem repository do not fit this project | Red pipeline | Install only the needed workflows; stop and report after three failed fixes |
| The documents of the baseline milestone [MIL-006] change documents that were accepted earlier, and the AI stand-in for S01 reviews them | A defect is missed because the review is not independent | Every review record of the baseline says `Mode: autonomous, not independent`, the program is not changed, the tests run before and after, and the end-of-run summary lists the reviews for challenge |

## Assumptions

- The WhatsApp Python module the participant means is `pywhatkit`, which sends through WhatsApp Web in a browser where the participant is logged in. It is an optional dependency, imported only when a message is sent.
- The Sheety project exposes a `prices` sheet with the fields `city`, `iataCode`, `lowestPrice` and `id`, with Bearer authentication and PUT enabled.
- The participant (S01) is Product Owner, developer and reviewer; in autonomous mode the AI acts as stand-in reviewer and every such review says so.
- The origin airport is LHR and the currency is GBP, as in the assignment; both are constants.
- Real tokens exist only in the participant's local `.env`, are used only by the participant's own runs, and are never used by tests.

## Constraints

- Python 3.13 or newer; `venv`; pytest; a `constants.py` for constants; `pyproject.toml` for configuration.
- Doxygen comments in source and a Doxyfile.
- Hosted at `https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code` (this project is the `039-personal-flight-club` repository); one branch and pull request per step.
- No more runtime dependencies than needed.
- The baseline milestone [MIL-006] starts 2026-11-16 and is finished within one week, by 2026-11-23. For that milestone only, an AI stand-in for S01 reviews and accepts the changed documents.
- The Product Owner (PO) language is English and the PO domain is education (it was IT until [MIL-006]; the documents that [MIL-006] does not change keep the domain `it`, see the Open Issues of [PP-001]).

## Cost–Benefit Assessment

| Costs | Benefits |
| --- | --- |
| The participant's spare time; free-tier API accounts; AI assistance | A finished capstone, a portfolio repository and a reusable template. Qualitative assessment: the project is small and the cost is time only. |

## Stakeholders

| Stakeholder ID (SA) | Interest in this project |
| --- | --- |
| S01 | Finish the capstone, own the product and review it |
| S02 | Compare solutions; runnable code with the assignment's names |
| S03 | Browse for ideas; clear description, topics and README |

## Recommendation

Proceed — the scope is small, the risks are mitigated, and the result serves all three stakeholders.

---

[SA-001]: ./stakeholder-analysis.md
[PP-001]: ./project-plan.md
[1c49ffe]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/1c49ffebbd94841e90fa1ff84ba0e6bf39ea3625
[MIL-006]: ./milestones/mil-006-framework-baseline.md
