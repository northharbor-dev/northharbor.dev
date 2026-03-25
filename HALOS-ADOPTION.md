# HALOS Adoption — NorthHarbor Development Web

This repository is adopting **HALOS (Human-Agent Lineage and Origin Standard)** principles.

HALOS introduces governance for:
- human-AI collaboration
- attribution and provenance
- transparency of AI involvement
- conflict-aware decision making

---

## Repository Context

**Repository:** `northharbor-dev/northharbor-dev-web`
**Live site:** https://northharbor.dev
**Type:** Jekyll static site — public website for the NorthHarbor Development organization
**License:** CC-BY-4.0
**Deployment:** GitHub Pages, automatic on push to `main`

This is the public-facing website for the organization that maintains the HALOS specification.
As such, it is both a subject of HALOS adoption and a demonstration of how the framework
applies in practice — including to low-code/content-heavy repositories.

This adoption is **brownfield**: HALOS is being integrated into an existing repository
without disrupting current workflows unless explicitly approved by a human.

---

## Adoption Principles

### 1. Human Primacy

Humans are the final decision-makers for:
- all published site content
- governance changes and policy updates
- destructive or irreversible actions (deletions, force pushes)
- onboarding new agents or modifying existing agent permissions

Agents must **never silently reinterpret or override existing repo rules**.

### 2. Additive First (Non-Disruptive)

HALOS is introduced through:
- overlay documents (`halos.yaml`, `HALOS-ADOPTION.md`)
- mapping documents (`HALOS-COMPATIBILITY-MAP.md`)
- conflict registers (`HALOS-CONFLICT-REGISTER.md`)

Existing documents — including `.claude/settings.local.json`, workflows, and site content —
remain authoritative unless explicitly updated by a human.

### 3. Conflict Transparency

When HALOS principles and existing repo practices differ, agents **must**:
- surface the conflict explicitly
- explain both the current behavior and the HALOS-preferred behavior
- present options with tradeoffs
- request a human decision

No silent resolution is allowed.

### 4. Provenance and Attribution

Agents must:
- distinguish between existing repo behavior, inferred meaning, and proposed changes
- annotate AI involvement in artifacts where appropriate
- not present AI-generated content as purely human-authored

This is particularly relevant for this repository, as it publishes content representing
the NorthHarbor organization's voice.

### 5. Incremental Adoption

Adoption proceeds in phases:

| Phase | Status |
|-------|--------|
| 1. Discover | **Current** |
| 2. Map | Pending |
| 3. Flag gaps and conflicts | Initiated (see HALOS-CONFLICT-REGISTER.md) |
| 4. Propose overlays | Pending human approval |
| 5. Escalate decisions | Pending human decision |
| 6. Implement approved changes | Pending |

---

## Agent Expectations

Agents working in this repository must:

1. Read `.claude/settings.local.json` as the authoritative local permission contract
2. Treat it as binding — HALOS is an overlay, not a replacement
3. Apply HALOS as supplemental governance, not superseding local rules

### Allowed (Safe Additive)

- Create HALOS mapping documents
- Generate or update `halos.yaml`
- Propose new workflows (non-blocking)
- Annotate gaps and conflicts in the register
- Make additive content changes (new pages, copy improvements)
- Run local Jekyll build and test

### Review Needed

- Modifying `.claude/settings.local.json` permissions
- Adding CI checks (even non-blocking ones)
- Introducing metadata requirements for content files
- Dependency updates (`Gemfile`)

### Human Decision Required

- Publishing any content to the live site (`main` branch push)
- Changing governance meaning or agent scope
- Enforcing new blocking rules
- Altering ownership or approval flows
- Modifying `.github/workflows/pages.yml`
- Replacing or significantly altering existing policies

---

## Conflict Handling Template

When a conflict is found, agents must surface it using:

```
HALOS Adoption Decision Required

Current repo behavior:
<summary of what the repo does today>

HALOS-preferred behavior:
<summary of what HALOS principles suggest>

Why this matters:
<impact of the gap>

Options:
A. Keep current behavior (document divergence)
B. Add HALOS overlay (non-enforcing)
C. Partial migration
D. Full adoption

Recommended: <lowest-risk option>

Human decision required.
Resolution: *(record decision here)*
```

---

## Existing HALOS Artifacts in This Repository

| Artifact | Status | Notes |
|----------|--------|-------|
| `halos.yaml` | Created | Machine-readable governance profile |
| `HALOS-ADOPTION.md` | Created (this file) | Human-readable adoption statement |
| `HALOS-COMPATIBILITY-MAP.md` | Created | Full compatibility scan |
| `HALOS-CONFLICT-REGISTER.md` | Created | 7 open conflicts requiring human decision |

---

## References

- [HALOS Principles v1.0](https://github.com/northharbor-dev/halos-spec/blob/main/PRINCIPLES/halos-principles-v1.0.md)
- [HALOS Adoption Guide](https://github.com/northharbor-dev/halos-spec/blob/main/adopt/GUIDE.md)
- [HALOS Profile Schema](https://github.com/northharbor-dev/halos-spec/blob/main/spec/schema/halos-profile.schema.json)
- [Phase 2: Provenance Spec](https://raw.githubusercontent.com/northharbor-dev/halos-spec/main/PROVENANCE/halos-provenance-spec-v0.1.md)
