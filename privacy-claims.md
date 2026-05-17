# Privacy Claims Review

## Scope

- Product/App: Atlas Notes
- Evidence set: E-001 to E-004 (see trust-boundaries.md)

## Source claims

| Claim ID | Source | Source URL/Path | Claim text | Evidence ID(s) | Verification outcome | Confidence | Gap |
| --- | --- | --- | --- | --- | --- | --- | --- |
| P-001 | Privacy Policy | `/privacy` | "Users can request deletion at any time." | E-002 | Partially verified | High | No in-app deletion workflow; manual support dependency. |
| P-002 | README / Docs | `README.md` | "Minimal analytics only." | E-003 | Not verified | High | Analytics events include persistent identifiers not disclosed in claim. |
| P-003 | Security Docs | `docs/security.md` | "All API traffic is encrypted in transit." | E-001 | Verified | Medium | No explicit mention of TLS version/pinning expectations. |
| P-004 | Privacy Docs | `docs/privacy.md` | "Backups retained for 30 days." | E-004 | Partially verified | Medium | Deletion SLA for restored snapshots is unspecified. |

## Missing user controls

| Control area | Current state | Risk | Recommended control | Priority |
| --- | --- | --- | --- | --- |
| Data export path | Support-assisted only | Delayed DSAR response, inconsistent fulfillment | Add authenticated self-serve export endpoint + audit log | Next |
| Data deletion path | Support email request only | High friction and unverifiable completion | Add in-product deletion flow with confirmation receipt | Now |
| Retention disclosure | Policy references 30-day backups without operational detail | Ambiguous expectation for erased data | Publish backup purge workflow and recovery edge-case notice | Next |
| Contact/escalation path | General support inbox only | Privacy incidents may be under-routed | Publish dedicated privacy contact + escalation SLA | Now |

## Unresolved assumptions

| Assumption ID | Assumption | Evidence needed | Owner | Status |
| --- | --- | --- | --- | --- |
| A-002 | Analytics excludes note content payloads | Event schema inspection and redaction tests | Product engineering manager | Open |
| A-003 | Backup purge runs within stated policy windows | Ops runbook and deletion job logs | Platform ops | Open |
