# HALOS Compatibility Map — northharbor-dev-web

**Generated:** 2026-03-25
**HALOS Profile:** [`halos.yaml`](./halos.yaml)
**Adoption Phase:** Discover
**Assessment method:** Static file scan + CI/workflow inspection

This document maps every significant governance, agent, policy, and infrastructure
artifact in this repository to its corresponding HALOS concept. Alignment is assessed
as **Full**, **Partial**, or **Gap**.

No existing files have been modified. This is a read-only mapping.

---

## 1. Agent Behavior Contracts

HALOS concept: A declared, human-readable document specifying what agents are authorized
to do, what they must escalate, and how conflicts are handled (e.g., CLAUDE.md, AGENTS.md).

| Artifact | Alignment | Notes |
|---|---|---|
| `.claude/settings.local.json` | **Partial** | Declares permitted Bash commands and tool-access rules for Claude Code. Operative as a permission boundary, but is machine-oriented (JSON allow-list), not a human-readable behavior contract. No escalation policy, no conflict-handling rules, no principle alignment. |
| CLAUDE.md | **Gap** | Does not exist. No human-readable agent behavior contract is present. |
| AGENTS.md | **Gap** | Does not exist. No multi-agent registry or capability declaration. |
| .cursor/rules/ | **Gap** | Does not exist. No Cursor-specific rules. |

**Domain coverage: Partial** — permissioned operations exist but no behavior contract.

---

## 2. Agent Capabilities

HALOS concept: Documentation of what each agent can and cannot do, its scope of access,
and what categories of action require human approval.

| Artifact | Alignment | Notes |
|---|---|---|
| `.claude/settings.local.json` (allow list) | **Partial** | Lists specific allowed Bash invocations (bundle exec, jekyll, git add/push, curl health-checks). Implicitly scopes Claude Code to site-development operations. However, no capability registry, no forbidden list, and no human-approval categories are declared in a human-readable form. |
| Agent capability registry | **Gap** | No HALOS-style `existingAgents` declaration exists outside `halos.yaml` (newly created). |

**Domain coverage: Partial** — scope is implicitly constrained; not explicitly documented.

---

## 3. Governance Policies

HALOS concept: Policies governing how decisions are made, how contributions are
reviewed, what requires human approval, and how the project is maintained.

| Artifact | Alignment | Notes |
|---|---|---|
| `LICENSE` (CC-BY-4.0) | **Partial** | Covers intellectual-property attribution for published content. Does not address AI-generated contributions or agent involvement. |
| `README.md` | **Partial** | Describes site structure and local dev workflow. No contribution policy, no review requirements, no agent policy. |
| CONTRIBUTING.md | **Gap** | Does not exist. No human contribution guidelines. |
| CODE_OF_CONDUCT.md | **Gap** | Does not exist. |
| CODEOWNERS | **Gap** | Does not exist. No ownership mapping. |
| Pull-request template | **Gap** | No `.github/pull_request_template.md`. No structured review requirement or AI-attribution field. |

**Domain coverage: Partial** — licensing exists; contribution and review governance absent.

---

## 4. Decision Provenance

HALOS concept: A record of significant decisions, why they were made, who made them,
and what alternatives were considered (ADRs, decision logs, etc.).

| Artifact | Alignment | Notes |
|---|---|---|
| `docs/decisions/` | **Gap** | Does not exist. No ADR directory or decision log. |
| Git commit history | **Partial** | Provides an implicit artifact-level record of changes but commits are not structured with decision rationale, agent vs. human attribution, or alternatives considered. Several commits are agent-authored (Claude) with no labeling. |
| GitHub PR descriptions | **Partial** | PRs exist and provide some narrative context, but there is no template enforcing rationale, attribution, or HALOS-aligned decision capture. |

**Domain coverage: Partial** — git history gives basic traceability; no structured decision record.

---

## 5. Data Provenance and Traceability

HALOS concept: Labeling of AI-generated content, distinguishing human vs. agent
contributions, and tracing the lineage of artifacts.

| Artifact | Alignment | Notes |
|---|---|---|
| AI involvement labeling (commits) | **Gap** | Commits authored by Claude Code carry no `[AI]` prefix, co-author trailer, or other label distinguishing them from human commits. |
| AI involvement labeling (content) | **Gap** | Site pages (index.md, about.md) do not disclose which portions were AI-assisted. |
| Provenance metadata (front-matter) | **Gap** | Jekyll front-matter contains no `author`, `ai_assisted`, or attribution fields. |
| Artifact lineage tracking | **Gap** | No mechanism to trace which artifacts were AI-generated, AI-assisted, or human-authored. |

**Domain coverage: Gap** — no traceability or AI-involvement labeling currently exists.

---

## 6. Infrastructure and Deployment

HALOS concept: CI/CD pipelines, deployment controls, and infrastructure declarations
that reflect human-primacy and change-control principles.

| Artifact | Alignment | Notes |
|---|---|---|
| `.github/workflows/pages.yml` | **Partial** | Automated Jekyll build + GitHub Pages deployment on push to `main`. Permissions are scoped (contents:read, pages:write, id-token:write). Concurrency configured to prevent overlapping deploys. No HALOS checks, no advisory gate for AI-generated changes, no attribution step. |
| Branch protection rules | **Gap** | Cannot be confirmed from local scan; no `.github/branch-protection.yml` or equivalent found. If absent, direct push to `main` is not blocked. |
| Deployment review gate | **Gap** | No manual approval step in CI before deployment. Changes merged to `main` auto-deploy. |

**Domain coverage: Partial** — solid CI foundation; no HALOS-aligned deployment controls.

---

## Coverage Summary Matrix

| Domain | Artifacts Present | Full | Partial | Gap |
|---|---|---|---|---|
| 1. Agent behavior contracts | 1 of 4 | 0 | 1 | 3 |
| 2. Agent capabilities | 1 of 2 | 0 | 1 | 1 |
| 3. Governance policies | 2 of 6 | 0 | 2 | 4 |
| 4. Decision provenance | 2 of 3 | 0 | 2 | 1 |
| 5. Data provenance / traceability | 0 of 4 | 0 | 0 | 4 |
| 6. Infrastructure and deployment | 1 of 3 | 0 | 1 | 2 |
| **Total** | **7 of 22** | **0** | **7** | **15** |

**Overall alignment:** Early-stage. Seven partial alignments exist, almost entirely from the
presence of `LICENSE`, `README.md`, `.claude/settings.local.json`, and `.github/workflows/pages.yml`.
No artifact achieves full HALOS alignment. Data provenance and traceability is the largest gap.

Open conflicts are enumerated in [`HALOS-CONFLICT-REGISTER.md`](./HALOS-CONFLICT-REGISTER.md).
