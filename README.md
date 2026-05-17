# hermes-trust-review-agent

Hermes challenge submission prototype for **Build With Hermes Agent**:
**“Trust Hardening Agent for Protective Computing.”**

## Why this project

Most agent demos optimize for speed. This project tests accountability:

- can an agent preserve context across sessions?
- can it execute bounded workflows without losing objective?
- can it produce auditable outputs for human review?

## Core workflow

1. Ingest a project trust surface (repo + public policy/docs URLs).
2. Identify trust boundaries, privacy claims, weak trust language, and missing controls.
3. Produce a structured **Defensibility Packet**.
4. Require explicit human review/approval of findings.
5. Publish final trust artifacts.

## Input surface

- README URL
- Privacy policy URL
- Security policy URL
- App/product URL
- GitHub repo URL

## Output artifacts

- `trust-boundaries.md`
- `privacy-claims.md`
- `risk-findings.md`
- `now-next-later.md`
- `defensibility-packet.md`

## Suggested challenge framing

> Most AI agent demos show speed. I wanted to test accountability. Hermes is used as a bounded review agent that inspects a project’s public trust surface and produces a human-reviewable Defensibility Packet.
