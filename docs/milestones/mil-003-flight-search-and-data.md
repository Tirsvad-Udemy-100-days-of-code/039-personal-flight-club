# MIL-003 Flight search and flight data

## Metadata
| Key | Value |
| --- | --- |
| ID | MIL-003 |
| CrossReference | [BC-001] |
| Language | en |
| Domain | it |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-24 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version | [1c49ffe] |

---

## Purpose

Decide whether the cheapest flight for a destination can be found and parsed, including the cases with no flights or a missing price.

## Deliverable

FlightSearch.check_flights() against SerpAPI Google Flights or the mock flight service, FlightData and find_cheapest_flight(data, return_date), and tests with sample JSON.

## Go / No-Go Criteria

| # | Criterion (objectively checkable) | Go | No-Go |
| --- | --- | --- | --- |
| 1 | find_cheapest_flight returns the lowest priced flight over best_flights and other_flights | Pass | Fail |
| 2 | Empty data returns a FlightData with N/A values | Pass | Exception |
| 3 | A flight with no price is skipped | Pass | Exception |
| 4 | check_flights prints API errors and returns no data instead of crashing | Pass | Crash |

## Dependencies

| Depends on | Reason |
| --- | --- |
| MIL-001 | Needs constants and tooling |
| MIL-002 | Sheet rows supply the destination codes |

## Traceability

| Business Case objective / KPI / user story | Reference |
| --- | --- |
| Objective 2 | [BC-001] |

## Ownership

| Role | Stakeholder ID (SA) |
| --- | --- |
| Owner | S01 |
| Approving reviewer | S01 |

## Target Date

2026-10-31 — within the two-week plan window of the Project Plan.

## Tasks

| # | Task | Summary | Needs its own Use Case/User Story? | Reference |
| --- | --- | --- | --- | --- |
| 1 | FlightData class | Add `FlightData` holding price, origin_airport, destination_airport, out_date and return_date. | No | |
| 2 | FlightSearch with SerpAPI | Implement `FlightSearch` reading `SERPAPI_API_KEY` and `check_flights(origin_city_code, destination_city_code, from_time, to_time)` using engine google_flights, type 1, one adult, currency GBP; print API errors. | No | |
| 3 | Mock flight provider | Add a provider for the course's mock flight service (app id and key from the environment), selectable by an environment setting, for when no SerpAPI key or quota is available. | No | |
| 4 | find_cheapest_flight | Combine best_flights and other_flights, skip entries without a price, take the lowest, keep only the date part of the time string, and return an N/A FlightData when nothing is found. | No | |
| 5 | Flight tests | Test parsing, empty data, missing price and error handling with sample JSON and mocked HTTP. | No | |

---

[BC-001]: ../business-case.md
[1c49ffe]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/1c49ffebbd94841e90fa1ff84ba0e6bf39ea3625
