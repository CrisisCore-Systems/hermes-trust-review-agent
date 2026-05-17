# hermes-trust-review-agent

Hermes challenge submission for **Build With Hermes Agent**:
**Trust Hardening Agent for Protective Computing**.

## Challenge objective

Demonstrate that a bounded AI agent can improve trust outcomes by producing **auditable, reviewer-gated risk analysis** instead of unreviewed automation.

## What was built

A documentation-first trust review workflow that:
1. Ingests a project trust surface (repository + public policy/docs URLs).
2. Maps trust boundaries and validates public privacy/security claims.
3. Produces structured risk findings with severity, evidence, confidence, and assumptions.
4. Requires explicit human decisions before findings are accepted.
5. Publishes a versioned Defensibility Packet for stakeholders.

## Why it matters

Most agent demos optimize for speed. This project optimizes for **defensibility**:
- decisions are traceable to evidence,
- uncertainty is explicitly recorded,
- and humans remain accountable for acceptance.

## Rubric alignment

| Rubric area | How this submission addresses it |
| --- | --- |
| Accountability | Every major finding includes reviewer decision, owner, and disposition in packet artifacts. |
| Auditability | Evidence IDs, source links, claim text, verification outcomes, and change log entries are preserved. |
| Human-in-the-loop | Review checkpoints and approval criteria are defined before packet publication. |
| Practical impact | Outputs are immediately actionable as Now/Next/Later remediation work with owners and acceptance signals. |

## Scope of exemplar review

This submission includes one coherent exemplar scenario for a fictional SaaS product, **Atlas Notes**, across all artifacts:
- Product URL: `https://atlasnotes.example.com`
- Repo URL: `https://github.com/example/atlas-notes`
- Docs reviewed:
  - `README.md`
  - `docs/security.md`
  - `docs/privacy.md`
  - Public Privacy Policy (`/privacy`)

## Architecture / flow (text diagram)

`User Client -> Atlas API -> Postgres`

`Atlas API -> Queue Worker -> Email Vendor`

`Atlas API -> Analytics SDK`

`Hermes Agent -> Defensibility Packet -> Human Reviewer -> Approved/Rejected Decisions`

## How to run a trust review

1. Define scope (product, repo, and public documents to review).
2. Create/update `trust-boundaries.md` with concrete boundaries and assumptions.
3. Capture source claims in `privacy-claims.md` and verify each claim against implementation/docs evidence.
4. Record prioritized findings in `risk-findings.md` with severity, confidence, and recommendation.
5. Convert recommendations into phased actions in `now-next-later.md`.
6. Finalize governance decisions, review outcomes, and revision history in `defensibility-packet.md`.
7. Obtain explicit reviewer approval before publishing packet artifacts.

## Artifact completion checklist

- [ ] Scope fields are fully populated with concrete URLs/paths.
- [ ] Every claim/finding references evidence ID(s) and source text.
- [ ] Confidence level is assigned to each claim verification and risk finding.
- [ ] Unresolved assumptions are listed with owner and due date.
- [ ] Reviewer decision states are set (Approved / Needs Changes / Rejected).
- [ ] Change log includes version, author, date, and rationale.

## Submission snapshot

- [Defensibility Packet](./defensibility-packet.md): governance record, approval criteria, and revision log.
- [Trust Boundaries](./trust-boundaries.md): boundary map with assumptions and verification outcomes.
- [Privacy Claims Review](./privacy-claims.md): claim-by-claim validation with confidence and gaps.
- [Risk Findings](./risk-findings.md): prioritized risk register with recommendations and decisions.
- [Now / Next / Later](./now-next-later.md): implementation roadmap for trust hardening.

## Before vs after outcomes

| State | Typical output | Hermes trust review output |
| --- | --- | --- |
| Before | Broad trust statements and ad-hoc notes | Structured evidence-linked packet artifacts |
| Before | Implicit assumptions | Explicit assumptions and unresolved items with owners |
| Before | Security/privacy issues without triage | Severity-ranked findings with reviewer decisions |
| After | Hard to audit historical decisions | Versioned change log and reproducible review trail |

## Evolution roadmap

- **Now:** maintain complete exemplar packet and enforce reviewer sign-off workflow.
- **Next:** add reusable intake form and standardized scoring model.
- **Later:** automate evidence extraction and diff-based trust regression detection.
