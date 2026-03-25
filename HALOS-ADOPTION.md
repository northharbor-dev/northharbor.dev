# HALOS Adoption — NorthHarbor Development Website

This repository is adopting **HALOS (Human-Agent Lineage and Origin Standard)** principles.

HALOS introduces governance for:
- human-AI collaboration
- attribution and provenance
- transparency of AI involvement
- conflict-aware decision making

## Repository Context

**Repo:** `northharbor-dev/northharbor-dev-web`
**Live at:** https://northharbor.dev
**Tech stack:** Jekyll static site, deployed via GitHub Pages
**License:** CC-BY-4.0

This is the public website for NorthHarbor Development — an open source organization
building principled tools for human-AI collaboration. The site itself is authored with
AI assistance (Claude Code), making HALOS adoption especially meaningful here: this
repo is a live demonstration of the principles it exists to promote.

This adoption is **brownfield-first**: HALOS integrates into an existing working site
without disrupting current workflows unless explicitly approved by a human.

---

## Adoption Principles

### 1. Human Primacy

Humans are the final decision-makers for:
- governance changes
- policy conflicts
- destructive or irreversible actions
- changes to agent permissions or behavior

Agents must **never silently reinterpret or override existing repo rules.**

### 2. Additive First (Non-Disruptive)

HALOS is introduced through:
- overlays
- mapping documents
- supplemental policies
- machine-readable manifests (`halos.yaml`)

Existing documents remain authoritative unless explicitly updated by a human.

### 3. Conflict Transparency

When HALOS and existing repo rules differ, agents MUST:
- surface the conflict explicitly
- explain both sides
- present options
- request human decision

No silent resolution is allowed. All conflicts are recorded in `HALOS-CONFLICT-REGISTER.md`.

### 4. Provenance and Attribution

Agents must:
- distinguish between existing repo behavior, inferred meaning, and proposed changes
- annotate AI involvement where appropriate
- avoid presenting AI-generated artifacts as purely human-authored
- honor the CC-BY-4.0 license obligations already present in this repo

### 5. Incremental Adoption

Adoption proceeds in phases:

1. **Discover** — understand the repo's existing governance landscape
2. **Map** — catalog existing artifacts against HALOS concepts
3. **Flag** — identify gaps and conflicts
4. **Propose** — draft overlays and supplemental policies
5. **Escalate** — surface all conflicts for human decision
6. **Implement** — apply approved changes only

**Current phase:** Map (Phase 2)

---

## Agent Expectations

Agents working in this repo must:

- Read `.claude/settings.local.json` first — treat it as authoritative local guidance
- Apply HALOS as an overlay, not a replacement
- Surface conflicts before acting on them

### Allowed (Safe Additive)
- Create HALOS mapping documents
- Generate manifests (`halos.yaml`)
- Propose workflows
- Annotate gaps in `HALOS-CONFLICT-REGISTER.md`

### Review Needed
- Modifying `.claude/settings.local.json` agent permissions
- Adding CI checks (non-blocking / advisory only)
- Introducing metadata requirements to existing pages

### Human Decision Required
- Changing governance meaning or ownership
- Enforcing new blocking rules
- Altering the CI/CD pipeline in enforcing ways
- Replacing or superseding existing policies
- Any change that affects how content is attributed or published

---

## Conflict Handling Template

When a conflict is found, agents must use:

```
HALOS Adoption Decision Required

Current repo behavior:
<summary>

HALOS-preferred behavior:
<summary>

Why this matters:
<summary>

Options:
A. Keep current behavior (document divergence)
B. Add HALOS overlay (non-enforcing)
C. Partial migration
D. Full adoption

Recommended:
<lowest-risk option>

Human decision required.
```

All conflicts are tracked in [`HALOS-CONFLICT-REGISTER.md`](./HALOS-CONFLICT-REGISTER.md).

---

## Expected HALOS Artifacts

This repo now includes:

| Artifact | Purpose |
|---|---|
| `halos.yaml` | Machine-readable governance profile |
| `HALOS-ADOPTION.md` | This document — human-readable adoption overview |
| `HALOS-COMPATIBILITY-MAP.md` | Maps existing artifacts to HALOS concepts |
| `HALOS-CONFLICT-REGISTER.md` | Tracks all gaps and conflicts for human decision |

These are additive and do not replace existing documentation.

---

## References

- [HALOS Principles v1.0](https://github.com/northharbor-dev/halos-spec/blob/main/spec/principles/v1.0.md)
- [HALOS Adoption Guide](https://github.com/northharbor-dev/halos-spec/blob/main/adopt/GUIDE.md)
- [HALOS Profile Schema](https://github.com/northharbor-dev/halos-spec/blob/main/spec/schema/halos-profile.schema.json)
