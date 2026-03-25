# HALOS Compatibility Map — northharbor-dev-web

**Repo:** `northharbor-dev/northharbor-dev-web`
**Scan date:** 2026-03-25
**HALOS phase:** Map (Phase 2)
**Assessor:** Claude Code (AI agent) — human review required before acting on gaps

This document maps every significant governance, agent, policy, and infrastructure
artifact in this repository to its corresponding HALOS concept. Gaps and partial
alignments are surfaced for human decision; nothing is changed here.

---

## Assessment Key

| Symbol | Meaning |
|--------|---------|
| FULL | Existing artifact satisfies the HALOS concept |
| PARTIAL | Artifact exists but has gaps relative to HALOS |
| GAP | No current repo equivalent |

---

## Domain 1: Agent Behavior Contracts

HALOS concept: explicit, human-readable declarations of what agents are permitted
to do, how they must behave under conflict, and what requires human escalation.

| Artifact | Path | Assessment | Notes |
|---|---|---|---|
| Agent permissions | `.claude/settings.local.json` | PARTIAL | Declares Claude Code shell permissions (what commands are allowed) but does not define behavioral expectations, conflict protocols, or escalation requirements. Satisfies capability scoping but not behavior contracting. |
| Agent behavior doc | `AGENTS.md` | GAP | Does not exist. No human-readable document defines how agents should behave in this repo. |
| Agent behavior doc | `CLAUDE.md` | GAP | Does not exist. No Claude-specific instructions document is present. |
| Cursor rules | `.cursor/rules/` | GAP | Does not exist. No Cursor-specific agent instructions present. |

**Domain coverage: PARTIAL** — capability scoping exists; behavioral contract is absent.

---

## Domain 2: Agent Capabilities

HALOS concept: declared, bounded agent capabilities scoped to specific tasks.
Agents should not have unbounded access; capabilities should be documented and
auditable.

| Artifact | Path | Assessment | Notes |
|---|---|---|---|
| Shell permission allowlist | `.claude/settings.local.json` | FULL | Explicit allowlist of permitted shell commands: Jekyll bundle commands, git push/add, curl health checks, pkill for jekyll. Capability scoping is present and deliberate. |
| Agent tool configuration | n/a | GAP | No formal declaration of which AI tools/agents are authorized to work in this repo beyond Claude Code. No multi-agent capability policy. |

**Domain coverage: PARTIAL** — Claude Code capabilities are scoped; formal multi-agent
policy and documentation of the capability boundary rationale are absent.

---

## Domain 3: Governance Policies

HALOS concept: documented policies for code review, content publishing, change
approval, and contribution.

| Artifact | Path | Assessment | Notes |
|---|---|---|---|
| Contribution guide | `CONTRIBUTING.md` | GAP | Does not exist. No documented process for proposing changes to content or structure. |
| Code of conduct | `CODE_OF_CONDUCT.md` | GAP | Does not exist. No community standards document. |
| Codeowners | `CODEOWNERS` or `.github/CODEOWNERS` | GAP | Does not exist. Ownership of files/paths is undeclared. |
| License | `LICENSE` | FULL | CC-BY-4.0 is present and unambiguous. Establishes attribution obligations for all content. Aligns with HALOS `ideasAsAssets` and `attribution` principles. |
| Site configuration | `_config.yml` | PARTIAL | Defines the Jekyll site's basic identity (title, description, URL). Does not address governance, attribution policy, or AI involvement. |
| README | `README.md` | PARTIAL | Describes the project and local dev setup. Does not address contribution process, AI involvement policy, or governance. |

**Domain coverage: PARTIAL** — license is strong; contribution process, code of
conduct, and ownership are absent.

---

## Domain 4: Decision Provenance

HALOS concept: a record of who made which decisions, when, and why — especially
for governance-level changes.

| Artifact | Path | Assessment | Notes |
|---|---|---|---|
| Pull request reviews | GitHub PRs | PARTIAL | GitHub PR history provides some decision provenance (who approved what). However, no formal requirement for human review is documented in-repo (no branch protection rules file, no CODEOWNERS). |
| Commit history | git log | PARTIAL | Git history records what changed and when, but not structured rationale for decisions. No commit message convention is enforced. |
| Changelog | `CHANGELOG.md` | GAP | Does not exist. No human-readable record of significant decisions or changes over time. |
| Decision log | `decisions/` or `ADRs/` | GAP | No Architecture Decision Records or equivalent. Rationale for structural choices is not captured. |

**Domain coverage: PARTIAL** — raw git and PR history exist; structured, queryable
decision provenance does not.

---

## Domain 5: Data Provenance and Traceability

HALOS concept: knowing which content was human-authored, which was AI-assisted,
and being able to trace artifacts back to their origin.

| Artifact | Path | Assessment | Notes |
|---|---|---|---|
| AI content labeling | n/a | GAP | No convention for marking AI-assisted or AI-generated content in pages, commits, or PRs. |
| Provenance metadata | n/a | GAP | No frontmatter, commit trailer, or metadata standard for tagging human vs. AI origin. |
| Attribution in content | `index.md`, `about.md` | PARTIAL | Content pages do not declare authorship. The CC-BY-4.0 license mandates attribution when redistributing, but no per-page attribution mechanism exists. |
| Conversation capture | n/a | GAP | No system for preserving agent conversation logs that informed content decisions. |

**Domain coverage: GAP** — this is the most significant unaddressed domain.
No provenance or AI labeling infrastructure exists today.

---

## Domain 6: Infrastructure and Deployment

HALOS concept: deployment pipelines should be auditable, reviewable, and — where
possible — include HALOS-aware checks.

| Artifact | Path | Assessment | Notes |
|---|---|---|---|
| CI/CD pipeline | `.github/workflows/pages.yml` | FULL | GitHub Actions workflow for Jekyll build and GitHub Pages deploy is present, clear, and well-structured. Triggered on push to main. |
| HALOS CI checks | n/a | GAP | No HALOS-awareness in CI. No check for AI labeling, attribution, or provenance metadata. Advisory mode would be the appropriate starting point. |
| Branch protection | GitHub settings | PARTIAL | Cannot be assessed from repo files alone — branch protection rules live in GitHub repository settings, not in-repo. Likely minimal for a small static site. |
| Deploy environment | GitHub Pages | FULL | Deployment target is declared and consistent (GitHub Pages from main). No ambiguity. |

**Domain coverage: PARTIAL** — core CI/CD is solid; HALOS-aware checks and
formal branch protection documentation are absent.

---

## Summary Coverage Matrix

| Domain | Coverage | Key Gap |
|---|---|---|
| 1. Agent behavior contracts | PARTIAL | No AGENTS.md / CLAUDE.md behavioral contract |
| 2. Agent capabilities | PARTIAL | No multi-agent policy; single-agent scoping exists |
| 3. Governance policies | PARTIAL | No CONTRIBUTING.md, CODEOWNERS, CODE_OF_CONDUCT.md |
| 4. Decision provenance | PARTIAL | No changelog, ADRs, or structured decision log |
| 5. Data provenance & traceability | GAP | No AI labeling, per-page attribution, or provenance metadata |
| 6. Infrastructure & deployment | PARTIAL | No HALOS CI checks; branch protection unverifiable |

**Overall assessment: PARTIAL alignment across most domains; one full GAP domain (provenance).**

All identified gaps are tracked with recommended options in
[`HALOS-CONFLICT-REGISTER.md`](./HALOS-CONFLICT-REGISTER.md).
Human decisions are required before any remediation is applied.
