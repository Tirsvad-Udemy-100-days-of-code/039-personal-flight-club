# MIL-004 Notification and main program

## Metadata
| Key | Value |
| --- | --- |
| ID | MIL-004 |
| CrossReference | [BC-001] |
| Language | en |
| Domain | it |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-24 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version | [1c49ffe] |

---

## Purpose

Decide whether the whole run works: all sheet rows checked, cheaper flights recorded and announced on WhatsApp.

## Deliverable

NotificationManager sending a WhatsApp message through the optional WhatsApp module, and main.py wiring sheet, search, comparison, price update and notification, with tests.

## Go / No-Go Criteria

| # | Criterion (objectively checkable) | Go | No-Go |
| --- | --- | --- | --- |
| 1 | Message text holds price, origin, destination, out date and return date | Pass | Fail |
| 2 | No notification and no price update when the price is N/A or not lower | Pass | Sent |
| 3 | Every sheet row is checked | Pass | Rows skipped |
| 4 | A missing WhatsApp module or send failure prints the message and does not crash the run | Pass | Crash |

## Dependencies

| Depends on | Reason |
| --- | --- |
| MIL-002 | Needs the data manager |
| MIL-003 | Needs search and parsing |

## Traceability

| Business Case objective / KPI / user story | Reference |
| --- | --- |
| Objectives 1 to 3 | [BC-001] |

## Ownership

| Role | Stakeholder ID (SA) |
| --- | --- |
| Owner | S01 |
| Approving reviewer | S01 |

## Target Date

2026-11-03 — within the two-week plan window of the Project Plan.

## Tasks

| # | Task | Summary | Needs its own Use Case/User Story? | Reference |
| --- | --- | --- | --- | --- |
| 1 | NotificationManager | Implement message building and `send_whatsapp(message)` using `pywhatkit` imported lazily and the number from the environment; fall back to printing the message. | No | |
| 2 | Main wiring | In main.py compute tomorrow and six months ahead, loop over `sheet_data`, call check_flights and find_cheapest_flight, skip N/A, and when the price is lower update the sheet and notify. | No | |
| 3 | Main and notification tests | Test the comparison logic and message text with fakes for the data manager, search and sender. | No | |
| 4 | Environment template update | Add the final variable names (WhatsApp number, provider setting) to `.env.example`. | No | |

---

[BC-001]: ../business-case.md
[1c49ffe]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/1c49ffebbd94841e90fa1ff84ba0e6bf39ea3625
