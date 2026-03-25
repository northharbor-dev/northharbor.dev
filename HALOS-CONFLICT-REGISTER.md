# HALOS Conflict Register — northharbor-dev-web

**Generated:** 2026-03-25
**HALOS Profile:** [`halos.yaml`](./halos.yaml)
**Status:** Open — all conflicts below require human review

This register documents divergences between HALOS principles and current repository
practices. No existing files have been modified. All proposed options require explicit
human approval before any implementation begins.

---

## How to Use This Register

1. Review each conflict and its options.
2. Record your decision in the **Resolution** field.
3. If choosing an option that requires implementation, open a GitHub issue or create an ADR.
4. Mark the conflict status as `Resolved` with the decision date.

---

## Conflict Index

| ID | Title | Severity | Status |
|---|---|---|---|
| CONFLICT-001 | No agent behavior contract (CLAUDE.md / AGENTS.md) | Medium | Open |
| CONFLICT-002 | AI-authored commits carry no labeling or attribution | Medium | Open |
| CONFLICT-003 | No contribution guidelines or pull-request template | Low | Open |
| CONFLICT-004 | No structured decision provenance (ADRs / decision log) | Medium | Open |
| CONFLICT-005 | No conflict disclosure mechanism in existing workflows | Medium | Open |

---

## CONFLICT-001: No agent behavior contract (CLAUDE.md / AGENTS.md)

**Severity:** Medium
**Status:** Open

### Current repo behavior

The only agent configuration present is `.claude/settings.local.json`, a machine-readable
JSON allow-list of specific Bash commands and tool permissions for Claude Code. There is no
CLAUDE.md, AGENTS.md, or equivalent human-readable document describing what the agent is
expected to do, what it must escalate, or how it should behave in ambiguous situations.

### HALOS-preferred behavior

HALOS principle **Human Primacy** (HALOS-CORE-1) and the agent behavior contract domain
call for a human-readable document that declares:
- the agent's authorized scope and role
- what categories of action require human approval
- how conflicts with existing rules should be handled
- escalation paths

### Why this matters

Without a behavior contract, new contributors (human or agent) have no clear reference
for what Claude Code is authorized to do. The permission boundary in settings.local.json
is opaque to humans and does not encode behavioral expectations. Expanding agent access
in future without a contract risks silent scope creep.

### Options

**A. Keep current behavior (document divergence)**
Accept that settings.local.json is the operative constraint and record this divergence
in halos.yaml. No new files created.

**B. Add HALOS overlay (non-enforcing)**
Create a CLAUDE.md that describes Claude Code's role, authorized scope, and escalation
expectations, without changing the settings.local.json permission boundary.

**C. Partial migration**
Create CLAUDE.md and align it with settings.local.json, ensuring the human-readable
contract and machine-readable permissions are consistent.

**D. Full adoption**
Create CLAUDE.md (behavior contract) and AGENTS.md (multi-agent registry), and update
settings.local.json to reference or align with them.

**Recommended:** B — additive, non-disruptive, provides immediate HALOS alignment
at low cost.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-002: AI-authored commits carry no labeling or attribution

**Severity:** Medium
**Status:** Open

### Current repo behavior

Several commits in this repository's history were authored by Claude Code (git author:
`Claude <noreply@anthropic.com>`). These commits appear identically to human commits in
the git log — there is no `[AI]` prefix, `Co-authored-by` trailer, or other signal that
distinguishes AI-generated changes from human-authored ones.

### HALOS-preferred behavior

HALOS principle **Transparency of AI Involvement** (HALOS-CORE-4) and **Attribution and
Provenance** (HALOS-CORE-3) require that AI participation in creating artifacts is
visible and traceable. Commits should signal AI involvement so reviewers and future
contributors understand the provenance of changes.

### Why this matters

The northharbor.dev site is the public face of the HALOS project. If its own commits
silently omit AI involvement while HALOS advocates for transparency, that creates a
credibility and integrity gap. It also prevents tooling from accurately tracing which
changes were agent-generated.

### Options

**A. Keep current behavior (document divergence)**
Accept current practice and note it as a known divergence. The git author email
(`noreply@anthropic.com`) provides implicit signal to informed readers.

**B. Add HALOS overlay (non-enforcing)**
Add a commit message convention guideline (e.g., in CONTRIBUTING.md or CLAUDE.md)
asking that AI-generated commits include `[AI]` in the subject line or a
`Co-authored-by: Claude Code <noreply@anthropic.com>` trailer. Non-enforcing — no CI gate.

**C. Partial migration**
Implement option B and add a non-blocking advisory CI check that detects unlabeled
agent commits and adds a comment.

**D. Full adoption**
Enforce AI attribution via a blocking CI check or commit-msg hook. Retroactively
annotate existing AI-authored commits (requires a rebase — destructive).

**Recommended:** B — clear guidance without retroactive disruption or CI overhead.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-003: No contribution guidelines or pull-request template

**Severity:** Low
**Status:** Open

### Current repo behavior

No `CONTRIBUTING.md` or `.github/pull_request_template.md` exists. README.md covers
local development setup but does not address how contributions should be structured,
reviewed, or attributed.

### HALOS-preferred behavior

HALOS principle **Governance Through Proposal** (HALOS-CORE-7) and the governance
policies domain expect a documented process for contributions, including how AI-assisted
work should be labeled in PRs and what review is required before merging.

### Why this matters

Without a PR template, there is no structured place to declare AI involvement, rationale,
or attribution in a pull request. This is a low-friction gap to close and directly
supports HALOS transparency goals.

### Options

**A. Keep current behavior (document divergence)**
Accept that informal review is sufficient for a small, focused site repository.

**B. Add HALOS overlay (non-enforcing)**
Create a minimal `.github/pull_request_template.md` with an AI involvement disclosure
field and a brief checklist. Non-enforcing — requires human reviewer judgment only.

**C. Partial migration**
Create CONTRIBUTING.md with contribution and attribution guidelines plus a PR template.

**D. Full adoption**
Full contribution governance: CONTRIBUTING.md, PR template, CODEOWNERS, and branch
protection rules enforcing review.

**Recommended:** B — lightweight and immediately useful, supports HALOS-CORE-4.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-004: No structured decision provenance (ADRs / decision log)

**Severity:** Medium
**Status:** Open

### Current repo behavior

Significant decisions (e.g., choice of Jekyll, CC-BY-4.0 license, GitHub Pages
deployment model, agent permission scope) are not recorded in any structured form.
The git log provides a partial record of *what* changed but not *why*, *who decided*,
or *what alternatives were considered*.

### HALOS-preferred behavior

HALOS principle **Attribution and Provenance** (HALOS-CORE-3) expects that decisions
with lasting impact are traceable. Particularly for agent-involved decisions, the
rationale and human-vs-agent contribution should be distinguishable.

### Why this matters

As Claude Code contributes more to this repository, future maintainers will have
decreasing ability to distinguish human strategic decisions from agent-generated
implementations. Without decision records, the "why" behind the site's architecture
and governance choices is lost.

### Options

**A. Keep current behavior (document divergence)**
Accept git history as the sole decision record. Document this divergence in halos.yaml.

**B. Add HALOS overlay (non-enforcing)**
Create a `docs/decisions/` directory with a README explaining the ADR convention and
a template. No existing decisions need to be back-filled immediately.

**C. Partial migration**
Create `docs/decisions/` and write one or two ADRs for the most significant existing
decisions (e.g., Jekyll + GitHub Pages, CC-BY-4.0 license).

**D. Full adoption**
Require ADRs for all significant future decisions via a CONTRIBUTING.md policy and
PR template checklist.

**Recommended:** B — establishes the structure with no immediate burden.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## CONFLICT-005: No conflict disclosure mechanism in existing workflows

**Severity:** Medium
**Status:** Open

### Current repo behavior

There is no pull-request template, CI check, or documented process that requires
conflicts between agent behavior and existing repo rules to be surfaced. If an agent
modifies content or configuration in a way that diverges from intended practice, there
is no structured path to flag or escalate it.

### HALOS-preferred behavior

HALOS principle **Conflict Disclosure** (a HALOS governance requirement) and the
`conflictHandling` spec in halos.yaml both require that conflicts be explicitly
surfaced, described using the structured template, and resolved by a human — never
silently by the agent.

### Why this matters

This is the meta-conflict: without a mechanism to surface conflicts, all other
conflicts in this register could be silently bypassed. For a repository that is
the reference implementation of HALOS principles, an absent conflict disclosure
path is a meaningful credibility gap.

### Options

**A. Keep current behavior (document divergence)**
Rely on agent instructions (HALOS-ADOPTION.md) and human reviewer judgment. Accept
this as an informal, undeclared process.

**B. Add HALOS overlay (non-enforcing)**
Add a conflict disclosure section to a PR template and to CLAUDE.md (if created per
CONFLICT-001), directing agents to use the structured conflict template before merging.

**C. Partial migration**
Implement option B and add a non-blocking advisory CI check that scans PR descriptions
for the conflict template marker and adds a reminder comment if absent.

**D. Full adoption**
Enforce conflict disclosure via a blocking CI gate on all PRs touching governance files.

**Recommended:** B — adds the mechanism with no enforcement overhead, consistent with
the `discover` adoption phase.

**Human decision required.**

**Resolution:** *(record decision here)*

---

## Next Steps

Once human decisions are recorded above, implementation follows these steps:

1. For each resolved conflict, open a GitHub issue referencing the conflict ID.
2. For HALOS overlays (option B outcomes), create the artifact in a new PR with
   AI involvement labeled per CONFLICT-002 guidance.
3. Update `halos.yaml` `spec.adoption.currentPhase` from `discover` to `map` (or
   further) as conflicts are resolved.
4. When ready for Phase 2 (provenance), see:
   - [`spec/provenance/v0.1.md`](https://github.com/northharbor-dev/halos-spec/blob/main/spec/provenance/v0.1.md)
   - [HALOS Profiles directory](https://github.com/northharbor-dev/halos-spec/blob/main/profiles/)
