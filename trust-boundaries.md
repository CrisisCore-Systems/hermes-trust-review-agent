# Trust Boundaries

## Scope

- Product/App: Atlas Notes (`https://atlasnotes.example.com`)
- Repo: `https://github.com/example/atlas-notes`
- Public Docs Reviewed:
  - `README.md`
  - `docs/security.md`
  - `docs/privacy.md`
  - `https://atlasnotes.example.com/privacy`

## Evidence register

| Evidence ID | Source URL/Path | Claim text observed | Verification outcome |
| --- | --- | --- | --- |
| E-001 | `docs/security.md` | "All API traffic is encrypted in transit." | Verified: TLS termination documented and required at ingress. |
| E-002 | `/privacy` | "Users can request account deletion at any time." | Partially verified: support email path exists; self-serve path absent. |
| E-003 | `README.md` | "Minimal analytics only." | Not verified: analytics SDK events include persistent user identifiers. |
| E-004 | `docs/privacy.md` | "Backups retained for 30 days." | Verified in policy docs; operational deletion procedure not evidenced. |

## Boundary map

| Boundary | Data crossing boundary | Trust assumption | Evidence ID(s) | Verification status | Confidence |
| --- | --- | --- | --- | --- | --- |
| Client -> API | Credentials, note content, session tokens | TLS + auth controls prevent interception/impersonation | E-001 | Partially verified (transport yes, auth docs incomplete) | Medium |
| API -> Database | User profile data, notes, metadata | Service identity and least privilege are enforced | E-001 | Unverified (no explicit DB role policy in reviewed docs) | Low |
| API -> Third-party email service | Transactional email address and template payload | Vendor only processes bounded data and no note content | E-004 | Partially verified (retention stated, payload minimization unclear) | Medium |
| API -> Analytics vendor | Event telemetry with user identifiers | Collected telemetry is minimal and documented | E-003 | Not verified (claim conflicts with observed SDK usage) | High |
| Human reviewer -> Agent output | Risk decisions, sign-off metadata | Reviewer verifies evidence before approval | E-001, E-002, E-003, E-004 | Verified via packet governance requirements | High |

## Unresolved assumptions

| Assumption ID | Assumption | Impact if wrong | Owner | Target resolution date | Status |
| --- | --- | --- | --- | --- | --- |
| A-001 | DB roles enforce row-level access controls | Unauthorized internal data access risk increases | Security lead | 2026-06-15 | Open |
| A-002 | Analytics configuration excludes note content fields | Potential privacy claim violation and over-collection | Product engineering manager | 2026-06-01 | Open |
| A-003 | Backup purge executes within policy window | Data deletion commitments may be inaccurate | Platform ops | 2026-06-20 | Open |
