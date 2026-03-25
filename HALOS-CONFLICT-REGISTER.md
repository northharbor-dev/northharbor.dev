# HALOS Conflict Register — NorthHarbor Development Web

**Repository:** `northharbor-dev/northharbor-dev-web`
**Generated:** 2026-03-25
**Adoption phase:** Discover
**Open conflicts:** 7
**Status:** Awaiting human decisions

All conflicts identified below require a human decision before any change is made.
No conflict may be silently resolved by an agent.

---

## CONFLICT-001: No Agent Behavior Contract Document

**Severity:** Medium
**Status:** Open

### Current repo behavior

Agent behavior is controlled exclusively by `.claude/settings.local.json`, which lists
allowed bash commands, read paths, and node operations. There is no human-readable document
explaining the intent, scope, or boundaries of agent involvement in this repo. There is no
`CLAUDE.md`, `AGENTS.md`, or equivalent document.

### HALOS-preferred behavior

HALOS (HALOS-CORE-1, Human Primacy) expects an explicit, human-readable agent behavior
contract that defines:
- What agents are permitted to do in this repository
- What actions require human escalation
- What is explicitly out of scope for agents
- How conflicts between agent suggestions and repo rules are handled

### Why this matters

Without a behavior contract, agents operating in this repo (including Claude Code, future
agents, or collaborators using AI tools) have no authoritative reference for scope boundaries.
This creates risk of scope creep, silent override of conventions, or inconsistent behavior
across sessions. For the HALOS organization's own website, the absence is symbolically notable.

### Options

A. Keep current behavior (document divergence in `halos.yaml` — already done)
B. Add a `CLAUDE.md` as a non-enforcing overlay documenting agent scope and escalation rules
C. Expand `.claude/settings.local.json` with structured comments explaining intent
D. Create a full `AGENTS.md` covering all agents (ClaudeCode + GitHub Actions)

**Recommended:** B — Create `CLAUDE.md` as an additive overlay. Low risk, high clarity.

**Human decision required.**
**Resolution:** *(record decision here)*

---

## CONFLICT-002: No AI Attribution or Transparency Policy

**Severity:** High
**Status:** Open

### Current repo behavior

The repository uses CC-BY-4.0 for content licensing, which requires attribution for
derivative works. There is no policy defining whether AI-assisted content requires
disclosure, how AI involvement should be attributed, or whether AI-generated text
satisfies the "human authorship" expectation implied by CC-BY-4.0 attribution.

Claude Code is an active agent in this repository, meaning content — including site
copy, documentation, and potentially design decisions — may be AI-assisted.

### HALOS-preferred behavior

HALOS-CORE-4 (Transparency of AI Involvement) requires that AI participation in content
creation be visible. HALOS-CORE-3 (Attribution and Provenance) requires that agent
contributions be disclosable and traceable.

For a public-facing website that represents the HALOS organization, undisclosed AI
involvement in published content would be a direct tension with the organization's
stated principles.

### Why this matters

This is the highest-severity conflict because:
1. The organization's credibility is tied to its adherence to HALOS principles
2. Published content on northharbor.dev implicitly represents human authorship unless stated otherwise
3. The CC-BY-4.0 license's attribution requirement is ambiguous for AI-assisted work
4. There is currently no mechanism to flag, annotate, or track AI involvement in any content file

### Options

A. Keep current behavior (accept undisclosed AI involvement, document divergence)
B. Add a site-wide AI disclosure notice (e.g., footer note, `/colophon` page)
C. Add front matter convention to content files (`ai_assisted: true/false`)
D. Full provenance tracking per HALOS Phase 2 spec

**Recommended:** B + C — A site-wide disclosure note is low-friction; front matter convention
is additive and does not require changing existing files.

**Human decision required.**
**Resolution:** *(record decision here)*

---

## CONFLICT-003: No CONTRIBUTING.md

**Severity:** Low
**Status:** Open

### Current repo behavior

There is no `CONTRIBUTING.md` file. Contribution expectations are not documented in the
repository. The `about.md` page references GitHub Issues and an RFC process for the
broader NorthHarbor organization, but nothing scoped to this specific repository.

### HALOS-preferred behavior

HALOS governance (HALOS-CORE-7, Governance Through Proposal) suggests that repositories
document how contributions are made, reviewed, and approved — including how agent-assisted
contributions are handled.

### Why this matters

Without contribution guidelines:
- External contributors have no guidance on expectations
- There is no documented human review requirement for PRs
- AI-assisted contributions have no stated disclosure or review protocol

### Options

A. Keep current behavior (rely on org-level norms)
B. Add a minimal `CONTRIBUTING.md` covering review expectations and AI disclosure
C. Add PR template only (lower friction, captures info at contribution time)
D. Full contribution governance document with agent-specific section

**Recommended:** B — A minimal `CONTRIBUTING.md` is additive and covers the gap adequately
for a content site.

**Human decision required.**
**Resolution:** *(record decision here)*

---

## CONFLICT-004: No CODEOWNERS File

**Severity:** Low
**Status:** Open

### Current repo behavior

There is no `CODEOWNERS` file. Any contributor with write access can push to `main` and
trigger an automatic deployment to northharbor.dev. There is no declared human owner for
any section of the repository.

### HALOS-preferred behavior

HALOS-CORE-1 (Human Primacy) implies that there are identifiable humans accountable for
the output of human-agent collaboration. A `CODEOWNERS` file makes that accountability
explicit and can enforce required review before deployment.

### Why this matters

The absence of CODEOWNERS means:
- No required human review is enforced by GitHub before merging to `main`
- Any push to `main` automatically deploys to the live site
- There is no declared ownership for governance documents like `halos.yaml`

### Options

A. Keep current behavior (rely on contributor discipline)
B. Add `CODEOWNERS` declaring ownership without enabling required review enforcement
C. Add `CODEOWNERS` + enable branch protection requiring owner review before merge
D. Add `CODEOWNERS` + branch protection + required status checks

**Recommended:** B — Additive, declarative, does not change current workflow. Option C
is a meaningful improvement but requires branch protection configuration (human decision).

**Human decision required.**
**Resolution:** *(record decision here)*

---

## CONFLICT-005: No Pull Request Template

**Severity:** Low
**Status:** Open

### Current repo behavior

There is no `.github/pull_request_template.md`. PRs have no structured format, and
there is no prompt for contributors to declare AI involvement, describe the change
rationale, or indicate what review is needed.

### HALOS-preferred behavior

HALOS-CORE-3 (Attribution and Provenance) and HALOS-CORE-4 (Transparency) suggest that
the contribution workflow surface AI involvement at the point of contribution. A PR
template is the lowest-friction place to capture this.

### Why this matters

Without a PR template, AI-assisted contributions can be merged without any disclosure.
For the HALOS org's website, this is a visible gap between stated principles and practice.

### Options

A. Keep current behavior (no template)
B. Add a minimal PR template with an AI involvement checkbox and change description field
C. Add a full PR template with HALOS attribution, provenance, and review sections

**Recommended:** B — Minimal template with AI disclosure checkbox. Low friction, high signal.

**Human decision required.**
**Resolution:** *(record decision here)*

---

## CONFLICT-006: No Decision Provenance (ADRs or Equivalent)

**Severity:** Low
**Status:** Open

### Current repo behavior

Architectural and governance decisions — such as the choice of Jekyll, CC-BY-4.0,
GitHub Pages deployment, HALOS design token integration in CSS, and the "blueprint"
template pattern — are not documented with rationale. The `README.md` describes the
current state but not the decisions that led to it.

### HALOS-preferred behavior

HALOS-CORE-8 (Innovation with Accountability) suggests that technical and governance
decisions should be traceable. Decision records allow future contributors (human or agent)
to understand constraints, avoid re-litigating settled questions, and identify when
circumstances have changed.

### Why this matters

Without decision records:
- Future agents may re-evaluate and propose changes to settled decisions
- Contributors cannot distinguish "chosen this way" from "ended up this way"
- The HALOS governance artifacts themselves (this adoption) have no recorded rationale

### Options

A. Keep current behavior (rely on git history and commit messages)
B. Add a `decisions/` directory with lightweight ADRs for key decisions going forward
C. Retroactively document key decisions + new decisions going forward
D. Adopt a formal ADR format (Nygard, MADR, etc.)

**Recommended:** B — Lightweight forward-looking ADRs. Retroactive documentation (C) is
valuable but not urgent; it can follow as a separate initiative.

**Human decision required.**
**Resolution:** *(record decision here)*

---

## CONFLICT-007: No Provenance Tracking for AI-Assisted Content

**Severity:** High
**Status:** Open

### Current repo behavior

Git commit history provides a record of changes by author, but does not distinguish
AI-assisted commits from purely human commits. There is no convention for flagging AI
involvement in commit messages, no front matter schema for content files, and no session
or conversation log storage. Claude Code sessions leave no persistent artifact.

### HALOS-preferred behavior

HALOS-CORE-3 (Attribution and Provenance) requires that agent contributions be disclosable
and traceable. HALOS Phase 2 (Provenance Spec) defines mechanisms for capturing session
context, conversation lineage, and artifact provenance.

### Why this matters

This is a foundational gap for Phase 2 adoption. Without provenance infrastructure:
- It is impossible to determine which published content was AI-assisted
- The git history is not a reliable provenance record for HALOS purposes
- The organization cannot credibly claim HALOS provenance compliance for its own site
- Future audits or attribution requirements cannot be satisfied retroactively

### Options

A. Keep current behavior (accept provenance gap, document divergence)
B. Adopt a commit message convention (e.g., `[ai-assisted]` tag) going forward
C. Add front matter convention to content files for AI involvement annotation
D. Implement Phase 2 provenance infrastructure (session logs, artifact metadata)

**Recommended:** B + C as interim measures. Phase 2 (D) is the full solution but requires
significant infrastructure work — that is a separate adoption phase.

**Human decision required.**
**Resolution:** *(record decision here)*

---

## Conflict Summary

| ID | Title | Severity | Status | Recommended Option |
|----|-------|----------|--------|-------------------|
| CONFLICT-001 | No agent behavior contract document | Medium | Open | Create `CLAUDE.md` overlay (B) |
| CONFLICT-002 | No AI attribution or transparency policy | **High** | Open | Site disclosure + front matter (B+C) |
| CONFLICT-003 | No CONTRIBUTING.md | Low | Open | Minimal `CONTRIBUTING.md` (B) |
| CONFLICT-004 | No CODEOWNERS file | Low | Open | Declarative `CODEOWNERS` (B) |
| CONFLICT-005 | No pull request template | Low | Open | Minimal PR template (B) |
| CONFLICT-006 | No decision provenance | Low | Open | Lightweight ADRs going forward (B) |
| CONFLICT-007 | No AI provenance tracking | **High** | Open | Commit convention + front matter (B+C) |

**High severity:** 2 (CONFLICT-002, CONFLICT-007)
**Medium severity:** 1 (CONFLICT-001)
**Low severity:** 4 (CONFLICT-003, CONFLICT-004, CONFLICT-005, CONFLICT-006)

All conflicts require human decision before any remediation begins.
