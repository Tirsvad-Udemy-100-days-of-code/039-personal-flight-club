# MIL-002 Data manager (Sheety)

## Metadata
| Key | Value |
| --- | --- |
| ID | MIL-002 |
| CrossReference | [BC-001] |
| Language | en |
| Domain | it |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-24 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version | [1c49ffe] |

---

## Purpose

Decide whether destination data can be read and the lowest price written back safely, with secrets from the environment and caching configured.

## Deliverable

DataManager with get_destination_data() and update_lowest_price(row_id, new_price), Bearer authentication from the environment, cache setup that excludes Sheety, all covered by tests that mock requests.

## Go / No-Go Criteria

| # | Criterion (objectively checkable) | Go | No-Go |
| --- | --- | --- | --- |
| 1 | Tests for get_destination_data and update_lowest_price pass with mocked HTTP | Pass | Fail |
| 2 | No test reads the real `.env` or calls the network | Verified | Violated |
| 3 | Sheety responses are never cached | Verified by a test of the cache setup | Cached |

## Dependencies

| Depends on | Reason |
| --- | --- |
| MIL-001 | Needs the skeleton, constants and tooling |

## Traceability

| Business Case objective / KPI / user story | Reference |
| --- | --- |
| Objectives 1 and 4 | [BC-001] |

## Ownership

| Role | Stakeholder ID (SA) |
| --- | --- |
| Owner | S01 |
| Approving reviewer | S01 |

## Target Date

2026-10-28 — within the two-week plan window of the Project Plan.

## Tasks

| # | Task | Summary | Needs its own Use Case/User Story? | Reference |
| --- | --- | --- | --- | --- |
| 1 | DataManager GET | Implement `DataManager.get_destination_data()` returning the sheet's `prices` list (the `sheet_data` of main), reading the Sheety endpoint and Bearer token from the environment loaded with python-dotenv. | No | |
| 2 | DataManager PUT | Implement `update_lowest_price(row_id, new_price)`, which PUTs the new `lowestPrice` for one row and raises a clear error on a failed response. | No | |
| 3 | Request cache setup | Install `requests_cache` at the top of main with a 3600 second expiry in `flight_cache.sqlite`, excluding the Sheety host so sheet data is always fresh. | No | |
| 4 | DataManager tests | Test both methods with mocked responses (no network, no `.env`), including an error response. | No | |

---

[BC-001]: ../business-case.md
[1c49ffe]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/1c49ffebbd94841e90fa1ff84ba0e6bf39ea3625
