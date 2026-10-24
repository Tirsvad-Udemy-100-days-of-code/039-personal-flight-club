# Business Case

## Metadata
| Key | Value |
| --- | --- |
| ID | BC-001 |
| CrossReference | [SA-001] |
| Language | en |
| Domain | it |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-24 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version | pending |

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

## Scope

### In Scope

- Python 3.13+ project with `src/` and `tests/`, `pyproject.toml`, a local `.venv`, pytest, `constants.py`, a Doxyfile and a Python `.gitignore`.
- The assignment classes: `DataManager`, `FlightSearch`, `FlightData` with `find_cheapest_flight()`, `NotificationManager`, and `main.py`.
- Response caching with `requests_cache`, and WhatsApp delivery through the participant's logged-in WhatsApp Web session.
- README from the framework template, wiki in three languages, screenshots, CI workflows from the TirSystem workflow repository, repository description and topics.

### Out of Scope

- Twilio SMS or WhatsApp (replaced by the WhatsApp Python module).
- Automated tests that call the real Sheety, SerpAPI, mock-flight or WhatsApp services, or that read the real `.env`.
- A user interface, a database, scheduling of the daily run, and booking of flights.

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

## Risks

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Free-tier quotas run out (SerpAPI 100/month, Sheety 200/month) | Development stops | Cache with `requests_cache`; use the mock flight service; keep 3 to 5 destinations |
| Secrets committed by mistake | Credential leak | `.env` and cache files in `.gitignore`; only `.env.example` committed; secret scan before each PR |
| WhatsApp Web automation is fragile (needs a browser and a logged-in session) | Notification fails | Import the module lazily; isolate it behind `NotificationManager`; print the message on failure |
| The WhatsApp module differs from the participant's intent | Rework | Assumption recorded below; the module is used in one function in one file |
| CI workflows from the TirSystem repository do not fit this project | Red pipeline | Install only the needed workflows; stop and report after three failed fixes |

## Assumptions

- The WhatsApp Python module the participant means is `pywhatkit`, which sends through WhatsApp Web in a browser where the participant is logged in. It is an optional dependency, imported only when a message is sent.
- The Sheety project exposes a `prices` sheet with the fields `city`, `iataCode`, `lowestPrice` and `id`, with Bearer authentication and PUT enabled.
- The participant (S01) is Product Owner, developer and reviewer; in autonomous mode the AI acts as stand-in reviewer and every such review says so.
- The origin airport is LHR and the currency is GBP, as in the assignment; both are constants.
- Real tokens exist only in the participant's local `.env`, are used only by the participant's own runs, and are never used by tests.

## Constraints

- Python 3.13 or newer; `venv`; pytest; a `constants.py` for constants; `pyproject.toml` for configuration.
- Doxygen comments in source and a Doxyfile.
- Hosted at `https://git.tirsystem.com/Tirsvad-Udemy-100_days_of_code` (this project is the `039-personal-flight-club` repository); one branch and pull request per step.
- No more runtime dependencies than needed.

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
