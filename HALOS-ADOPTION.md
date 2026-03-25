# HALOS Adoption — northharbor-dev-web

This repository is adopting **HALOS (Human-Agent Living Operating System)** principles.

HALOS introduces governance for:
- human-AI collaboration
- attribution and provenance
- transparency of AI involvement
- conflict-aware decision making

This adoption is **brownfield-first**: HALOS is being integrated into an existing system
without disrupting current workflows unless explicitly approved by a human maintainer.

---

## Repository Context

`northharbor-dev-web` is the public website for [NorthHarbor Development](https://northharbor.dev),
a Jekyll static site deployed to GitHub Pages. It serves as the home for the HALOS project
and related NorthHarbor open-source work.

Because this site is the public face of the HALOS framework itself, it carries an
especially strong expectation that its own operation reflects HALOS principles.

**Stack:** Jekyll 4.3, GitHub Pages, GitHub Actions CI
**License:** CC-BY-4.0
**Primary agent in use:** Claude Code (Anthropic)
**Machine-readable profile:** [`halos.yaml`](./halos.yaml)

---

## Adoption Principles

### 1. Human Primacy

Humans are the final decision-makers for:
- governance changes
- policy conflicts
- destructive or irreversible actions
- changes to published site content
- deployment configuration changes

Agents must **never silently reinterpret or override existing repo rules**.

### 2. Additive First (Non-Disruptive)

HALOS is introduced through:
- overlays
- mapping documents
- supplemental policies
- manifests

Existing documents remain authoritative unless explicitly updated by a human.

### 3. Conflict Transparency

When HALOS and existing repo rules differ:

Agents **must**:
- surface the conflict explicitly
- explain both sides
- present options
- request human decision

No silent resolution is allowed.

### 4. Provenance and Attribution

Agents must:
- distinguish between existing repo behavior, inferred meaning, and proposed changes
- annotate AI involvement where appropriate
- avoid presenting generated artifacts as purely human-authored

### 5. Incremental Adoption

Adoption proceeds in phases:

1. **Discover** ← *current phase*
2. Map
3. Flag gaps/conflicts
4. Propose overlays
5. Escalate decisions
6. Implement approved changes

---

## Agent Expectations

The primary AI agent in this repository is **Claude Code** (Anthropic). Its permitted
shell operations are declared in `.claude/settings.local.json`.

All agents working in this repo must:

- Treat `.claude/settings.local.json` as the authoritative local permission boundary
- Apply HALOS as an overlay, not a replacement, for any existing constraints
- Surface conflicts rather than resolve them silently

### Allowed (Safe Additive)

- Create HALOS mapping documents
- Generate manifests (`halos.yaml`)
- Propose workflows or documentation changes
- Annotate gaps or conflicts in HALOS registers
- Run local Jekyll build/serve operations

### Review Needed

- Modifying site content beyond trivial copy edits
- Adding CI checks (non-blocking advisory only, while in `discover` phase)
- Introducing metadata requirements in front-matter or layouts

### Human Decision Required

- Changing governance meaning or ownership
- Enforcing new blocking rules (CI or review gates)
- Altering license or attribution terms
- Replacing or substantively rewriting existing policies
- Authorizing new agents or expanding existing agent permissions

---

## Conflict Handling Template

When a conflict is found, agents must surface it using this format:

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

All open conflicts are tracked in [`HALOS-CONFLICT-REGISTER.md`](./HALOS-CONFLICT-REGISTER.md).

---

## Expected HALOS Artifacts

This repository now includes:

| Artifact | Purpose |
|---|---|
| `halos.yaml` | Machine-readable governance profile |
| `HALOS-ADOPTION.md` | This document — human-readable adoption statement |
| `HALOS-COMPATIBILITY-MAP.md` | Mapping of existing artifacts to HALOS concepts |
| `HALOS-CONFLICT-REGISTER.md` | Open gaps and conflicts requiring human decision |

These are additive and do not replace existing docs.

---

## References

- [HALOS Principles v1.0](https://github.com/northharbor-dev/halos-spec/blob/main/spec/principles/v1.0.md)
- [HALOS Adoption Guide](https://github.com/northharbor-dev/halos-spec/blob/main/adopt/GUIDE.md)
- [HALOS Profile Schema](https://github.com/northharbor-dev/halos-spec/blob/main/spec/schema/halos-profile.schema.json)
- [HALOS Profiles Directory](https://github.com/northharbor-dev/halos-spec/blob/main/profiles/)
