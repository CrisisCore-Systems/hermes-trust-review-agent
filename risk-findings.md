# Risk Findings

## Findings

| ID | Severity | Surface | Finding | Evidence ID(s) | Recommendation | Confidence | Review decision |
| --- | --- | --- | --- | --- | --- | --- | --- |
| R-001 | High | Privacy controls | No self-serve account deletion path despite policy promise of at-will deletion. | E-002 | Implement authenticated deletion workflow with confirmation, SLA tracking, and audit events. | High | Approved |
| R-002 | High | Data minimization | Public "minimal analytics" claim conflicts with observed persistent user identifiers in analytics instrumentation. | E-003 | Update telemetry schema to minimize identifiers and align external claim language with actual collection. | High | Approved |
| R-003 | Medium | Data lifecycle | Backup retention claim exists, but operational purge verification is not documented. | E-004 | Publish purge controls and add periodic evidence capture of purge execution. | Medium | Needs Changes |
| R-004 | Medium | Access control assumptions | Database least-privilege controls are not evidenced in reviewed public docs. | E-001 | Add control narrative and internal verification artifact references for DB role boundaries. | Low | Needs Changes |

## Risk language watchlist

| Category | Observed language | Why risky | Action |
| --- | --- | --- | --- |
| Ambiguous guarantees | "Minimal analytics" | Undefined term creates mismatch risk between expectation and implementation. | Replace with explicit event categories and data elements. |
| Missing caveats | "Deletion at any time" | Omits manual dependency and expected completion window. | Add workflow caveat and completion SLA. |
| Contradictory claims | Privacy minimization vs persistent identifiers | Reduces trust and creates potential compliance exposure. | Align claim text to verified implementation after remediation. |

## Decision notes

- Reviewer role: Privacy engineering lead
- Decision state meanings:
  - **Approved:** remediation accepted and scheduled.
  - **Needs Changes:** additional evidence or revision required before closure.
  - **Rejected:** finding invalid based on contradictory evidence.
