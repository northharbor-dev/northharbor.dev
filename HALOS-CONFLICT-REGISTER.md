# HALOS Conflict Register — northharbor-dev-web

**Repo:** `northharbor-dev/northharbor-dev-web`
**Generated:** 2026-03-25
**HALOS phase:** Map (Phase 2)
**Status:** All conflicts OPEN — human decisions required

This register documents every gap and partial alignment identified in
[`HALOS-COMPATIBILITY-MAP.md`](./HALOS-COMPATIBILITY-MAP.md).

No changes have been made to the repository based on these findings.
Each entry requires a human decision before any remediation is applied.

---

## CONFLICT-001: No Formal Agent Behavior Contract

**Severity:** High
**Status:** Open
**Domain:** Agent behavior contracts

### Current repo behavior
`.claude/settings.local.json` exists and scopes Claude Code's shell permissions
(which commands it may run). There is no AGENTS.md, CLAUDE.md, or equivalent
document that declares:
- what agents are expected to do (and not do) in this repo
- how agents must handle conflicts with existing rules
- what requires human escalation
- how AI-generated content should be attributed

### HALOS-preferred behavior
A human-readable agent behavior contract (e.g., `AGENTS.md` or `CLAUDE.md`)
that defines behavioral expectations, conflict protocols, escalation triggers,
and attribution requirements for all agents operating in this repo.

### Why this matters
Without a behavioral contract, an agent's conduct is governed only by its
default training and the permission allowlist. There is no explicit, auditable
statement of what the agent is expected to do when it encounters a governance
conflict, an ambiguous situation, or a gap between its defaults and repo norms.
For a repo that exists to model principled human-AI collaboration, this is a
meaningful gap.

### Options
A. Keep current behavior — document divergence in this register; rely on the
   permission allowlist and agent defaults.
B. Add HALOS overlay — create a non-enforcing `AGENTS.md` that describes
   expected behavior without changing any existing configuration.
C. Partial migration — add a `CLAUDE.md` with Claude-specific behavioral
   guidance scoped to this repo's content and governance needs.
D. Full adoption — create a comprehensive `AGENTS.md` covering all agents,
   plus update `.claude/settings.local.json` to reference it.

**Recommended:** B — create a lightweight `AGENTS.md` as a non-enforcing overlay.
This is additive, reversible, and directly demonstrates HALOS principle 1
(human primacy) in the repo that promotes it.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-002: No AI Content Attribution Policy

**Severity:** High
**Status:** Open
**Domain:** Data provenance and traceability

### Current repo behavior
This repo's content (pages, copy, site structure) is authored with AI assistance
(Claude Code). There is no convention, policy, or metadata standard for:
- indicating which content was AI-assisted or AI-generated
- distinguishing human-authored from machine-authored contributions
- labeling commits or PRs that contain AI-generated content
- satisfying the spirit of CC-BY-4.0 attribution when AI is a meaningful contributor

### HALOS-preferred behavior
A declared policy — even a lightweight one — for how AI involvement is acknowledged
in this repo's content and version history. This could be as simple as a commit
trailer convention (`Co-authored-by: Claude <claude@anthropic.com>`), a PR
description template, or a frontmatter field in content pages.

### Why this matters
The CC-BY-4.0 license already requires attribution. HALOS `transparency` principle
(declared `required` in `halos.yaml`) extends this to AI involvement. A public
website for a human-AI collaboration organization that does not acknowledge AI
authorship in its own content is in tension with its stated mission.

### Options
A. Keep current behavior — document divergence; accept that AI involvement
   is implicit and untracked.
B. Add HALOS overlay — establish a non-enforcing convention (e.g., commit
   trailers, PR template) for AI attribution without blocking anything.
C. Partial migration — add frontmatter to content pages (`ai_assisted: true`)
   and a PR description template.
D. Full adoption — implement a full provenance standard with per-artifact
   tracking and CI advisory checks.

**Recommended:** B — introduce a lightweight PR description template and commit
trailer convention. Non-enforcing, additive, and immediately meaningful.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-003: No Contribution Process or Governance Documentation

**Severity:** Medium
**Status:** Open
**Domain:** Governance policies

### Current repo behavior
No `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, or equivalent document exists.
There is no documented process for:
- proposing changes to site content or structure
- how community contributions (if any) are reviewed
- standards of conduct for contributors

### HALOS-preferred behavior
A `CONTRIBUTING.md` that describes the contribution process, including how
HALOS principles apply: what requires human review, what agents may do
autonomously, and how conflicts are escalated.

A `CODE_OF_CONDUCT.md` aligned with HALOS ethical guardrails.

### Why this matters
Without a contribution guide, the implicit process is whatever the repo owner
decides ad hoc. For a public repo modeling principled human-AI collaboration,
the absence of documented governance is a credibility gap. HALOS
`governanceThroughProposal` (declared `recommended`) is not achievable without
a documented proposal process.

### Options
A. Keep current behavior — document divergence; accept that this is a small
   internal site with informal governance.
B. Add HALOS overlay — create a minimal `CONTRIBUTING.md` that documents the
   current informal process and adds HALOS context.
C. Partial migration — create `CONTRIBUTING.md` with a HALOS-aware section and
   adopt a standard `CODE_OF_CONDUCT.md` (e.g., Contributor Covenant).
D. Full adoption — full governance documentation including proposal templates,
   review requirements, and enforcement.

**Recommended:** B — a minimal `CONTRIBUTING.md` is low-effort and immediately
improves transparency without committing to a heavy process.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-004: No CODEOWNERS or Formal Decision Provenance

**Severity:** Medium
**Status:** Open
**Domain:** Decision provenance

### Current repo behavior
No `CODEOWNERS` file exists in the repo or `.github/` directory. File ownership
is not declared. There is no changelog or Architecture Decision Record (ADR)
structure. The only decision provenance available is raw git history and GitHub
PR records (if any).

### HALOS-preferred behavior
Declared ownership of key paths (especially governance artifacts) via `CODEOWNERS`,
so that changes to critical files automatically require human review. A lightweight
changelog or decision log for significant structural decisions.

### Why this matters
Without `CODEOWNERS`, any agent (or contributor) can modify governance artifacts
without triggering a required human review. HALOS `humanPrimacy` (declared
`required`) depends on humans being in the loop for governance changes. Without
formal routing, this depends entirely on process discipline rather than
structure.

### Options
A. Keep current behavior — document divergence; rely on informal review processes.
B. Add HALOS overlay — create a `CODEOWNERS` file assigning the repo owner to
   HALOS governance artifacts specifically (`halos.yaml`, `HALOS-*.md`).
C. Partial migration — `CODEOWNERS` for governance files plus a minimal
   `CHANGELOG.md`.
D. Full adoption — `CODEOWNERS` for all significant paths, branch protection
   rules, and a structured decision log.

**Recommended:** B — a `CODEOWNERS` file scoped to HALOS governance artifacts
is a minimal, targeted, immediately valuable addition.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-005: No Provenance Capture for AI-Generated Content

**Severity:** Low
**Status:** Open
**Domain:** Data provenance and traceability

### Current repo behavior
No system exists for capturing or storing the agent conversations, prompts, or
intermediate reasoning that informed content decisions. Once a conversation
ends, the provenance of any generated content is lost. `halos.yaml` reflects
this: `provenance.capture.conversations: disabled` and
`provenance.capture.artifacts: disabled`.

### HALOS-preferred behavior
At minimum, a convention for linking published content back to the agent session
or prompt that generated it. At full adoption, a structured provenance store
(e.g., conversation logs in a `provenance/` directory or an external system).

### Why this matters
Without any provenance capture, it is impossible to audit why a particular piece
of content was written the way it was, or to understand what agent reasoning led
to a structural decision. This limits accountability and makes it harder to
identify errors introduced by agents. For Phase 1 (governance), this is a
low-severity gap; it becomes more significant in Phase 2 (provenance).

### Options
A. Keep current behavior — accept that provenance capture is out of scope for
   Phase 1. Document divergence.
B. Add HALOS overlay — establish a convention for linking PRs to the agent
   session that generated changes (e.g., a PR description field).
C. Partial migration — add a `provenance/` directory with lightweight session
   notes for significant content decisions.
D. Full adoption — integrate a provenance capture system; enable
   `provenance.capture.conversations: partial` in `halos.yaml`.

**Recommended:** A for Phase 1 — provenance capture is appropriately deferred
to Phase 2. Document divergence and revisit when moving to
`spec/provenance/v0.1.md`.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## Summary

| ID | Title | Severity | Status | Recommended |
|---|---|---|---|---|
| CONFLICT-001 | No formal agent behavior contract | High | Open | B — add AGENTS.md overlay |
| CONFLICT-002 | No AI content attribution policy | High | Open | B — PR template + commit trailers |
| CONFLICT-003 | No contribution process or governance docs | Medium | Open | B — minimal CONTRIBUTING.md |
| CONFLICT-004 | No CODEOWNERS or formal decision provenance | Medium | Open | B — CODEOWNERS for HALOS artifacts |
| CONFLICT-005 | No provenance capture for AI-generated content | Low | Open | A — defer to Phase 2 |

**Total conflicts:** 5
**High severity:** 2
**Medium severity:** 2
**Low severity:** 1
**Human decisions required:** 5

---

## Next Steps

All five conflicts require human decisions before any remediation is applied.
Once decisions are recorded above, Phase 3 (Flag → Propose) can proceed.

When ready to advance to provenance tracking, see:
- [`spec/provenance/v0.1.md`](https://github.com/northharbor-dev/halos-spec/blob/main/spec/provenance/v0.1.md)
- [HALOS profiles](https://github.com/northharbor-dev/halos-spec/blob/main/profiles/)
