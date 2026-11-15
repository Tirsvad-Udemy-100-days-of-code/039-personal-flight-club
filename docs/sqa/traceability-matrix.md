# Traceability Matrix: Personal Flight Club

## Metadata
| Key | Value |
| --- | --- |
| ID | TM-001 |
| CrossReference | [BC-001], [SA-001], [PP-001], [MIL-001], [MIL-002], [MIL-003], [MIL-004], [MIL-005], [MIL-006], [RC-001], [RC-002], [RC-003], [RC-004], [RC-005], [RC-006], [RC-007], [RC-008], [RC-009], [RC-010], [RC-011] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-11-16 | Accepted | Jens Tirsvad Nielsen | AI as stand-in for S01 | Initial version; created with the baseline milestone and its review records (autonomous, not independent) | [2267fc7] |

---

## Purpose

Tracks backward and forward links between the artifact instances of Personal Flight Club so that the traceability of the documents is measurable. A row is added or updated whenever an instance is created or reviewed.

## Traceability Table

| Artifact Instance | Type | Language | Domain | Upstream (Backward Link) | Downstream (Forward Link) | Last Reviewed (RC-ID) |
| --- | --- | --- | --- | --- | --- | --- |
| [BC-001] | BC | en | education | - | [SA-001], [PP-001], [MIL-001], [MIL-002], [MIL-003], [MIL-004], [MIL-005], [MIL-006] | [RC-008], [RC-001] |
| [SA-001] | SA | en | it | [BC-001] | [PP-001] | [RC-002] |
| [PP-001] | PP | en | education | [BC-001], [SA-001] | [MIL-001], [MIL-002], [MIL-003], [MIL-004], [MIL-005], [MIL-006] | [RC-009] |
| [MIL-001] | MIL | en | it | [BC-001], [PP-001] | [MIL-002] | [RC-003] |
| [MIL-002] | MIL | en | it | [BC-001], [PP-001], [MIL-001] | [MIL-003] | [RC-004] |
| [MIL-003] | MIL | en | it | [BC-001], [PP-001], [MIL-002] | [MIL-004] | [RC-005] |
| [MIL-004] | MIL | en | it | [BC-001], [PP-001], [MIL-003] | [MIL-005] | [RC-006] |
| [MIL-005] | MIL | en | it | [BC-001], [PP-001], [MIL-004] | [MIL-006] | [RC-007] |
| [MIL-006] | MIL | en | education | [BC-001], [PP-001], [MIL-005] | - | [RC-010] |
| Wiki | Wiki | en, da, ms | education | [BC-001], [MIL-006] | - | [RC-011] |

## Concern Coverage

| Concern (CN-ID) | Views that answer it | Decisions (ADR) | Quality check (TP) | Status |
| --- | --- | --- | --- | --- |
| - | - | - | - | Not applicable: [SA-001] lists the concerns of the stakeholders without CN-IDs, so there is no concern to cover by ID; the Traceability table of each milestone maps the objectives of [BC-001] to its Go/No-Go criteria |

## Open Inconsistencies

| # | Views | Inconsistency | Found in (RC-ID) | Status | Resolved in |
| --- | --- | --- | --- | --- | --- |
| - | - | none found | - | Closed | - |

## Coverage Notes

- `-` in Upstream means the instance is foundational, in Downstream that nothing is built on it yet, and in Last Reviewed that no `RC-*` exists yet.
- This matrix was created with [MIL-006]; until then the project had no traceability matrix. [PP-001] was accepted without a QC checklist; it is reviewed against `QC-PP-001` for the first time in [RC-009].
- The wiki (`docs/wiki/`) is documentation, not an artifact with an ID or a Language and Domain row; it has its own review record, [RC-011].
- The domain of [BC-001], [PP-001], [MIL-006] and the wiki is `education` since [MIL-006]. The other documents keep the domain `it` they were accepted with; a change of their domain would need a new review of each (see the Open Issues of [PP-001]).
- [MIL-006] changes no source file and no test, so the source code is not reviewed again. No view, design or test-plan artifact exists (the scope excludes them), so the milestones' Go/No-Go criteria are the quality checks.

---

[BC-001]: ../business-case.md
[SA-001]: ../stakeholder-analysis.md
[PP-001]: ../project-plan.md
[MIL-001]: ../milestones/mil-001-baseline-and-setup.md
[MIL-002]: ../milestones/mil-002-data-manager.md
[MIL-003]: ../milestones/mil-003-flight-search-and-data.md
[MIL-004]: ../milestones/mil-004-notification-and-main.md
[MIL-005]: ../milestones/mil-005-documentation-and-wiki.md
[MIL-006]: ../milestones/mil-006-framework-baseline.md
[RC-001]: ./reviews/rc-001-business-case.md
[RC-002]: ./reviews/rc-002-stakeholder-analysis.md
[RC-003]: ./reviews/rc-003-mil-001-baseline-and-setup.md
[RC-004]: ./reviews/rc-004-mil-002-data-manager.md
[RC-005]: ./reviews/rc-005-mil-003-flight-search-and-data.md
[RC-006]: ./reviews/rc-006-mil-004-notification-and-main.md
[RC-007]: ./reviews/rc-007-mil-005-documentation-and-wiki.md
[RC-008]: ./reviews/rc-008-business-case-baseline.md
[RC-009]: ./reviews/rc-009-project-plan-baseline.md
[RC-010]: ./reviews/rc-010-milestone-006.md
[RC-011]: ./reviews/rc-011-wiki.md
[2267fc7]: https://git.tirsystem.com/Tirsvad-Udemy-100-days-of-code/039-personal-flight-club/commit/2267fc7ec4a058d6044ab320ecee62f472c15cea
