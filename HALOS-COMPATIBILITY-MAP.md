# HALOS Compatibility Map — NorthHarbor Development Web

**Repository:** `northharbor-dev/northharbor-dev-web`
**Scan date:** 2026-03-25
**Adoption phase:** Discover
**Scan method:** Full repository traversal — all files, workflows, configuration

---

## Repository Inventory

Before mapping to HALOS domains, a complete inventory of governance-relevant artifacts:

| Artifact | Type | Purpose |
|----------|------|---------|
| `.claude/settings.local.json` | Agent config | Claude Code permissions (read, bash, node ops) |
| `.github/workflows/pages.yml` | CI/CD | Jekyll build and GitHub Pages deploy |
| `LICENSE` | Legal | CC-BY-4.0 content license |
| `README.md` | Documentation | Project setup and blueprint usage guide |
| `CNAME` | Infrastructure | Custom domain binding (northharbor.dev) |
| `_config.yml` | Site config | Jekyll configuration (title, URL, plugins) |
| `Gemfile` | Dependencies | Ruby/Jekyll dependency declarations |
| `about.md` | Content | Organization about page |
| `index.md` | Content | Homepage with project listings |
| `assets/style.css` | Frontend | Design system with HALOS-derived color tokens |
| `_layouts/default.html` | Frontend | Site layout with navigation and reading controls |
| `_includes/project-card.html` | Frontend | Reusable project card component |

**Not present:**
- `CLAUDE.md` — no agent behavior contract document
- `AGENTS.md` — no agent registry
- `CONTRIBUTING.md` — no contribution guidelines
- `CODEOWNERS` — no ownership declarations
- `.github/pull_request_template.md` — no PR template
- `.github/ISSUE_TEMPLATE/` — no issue templates
- `ADR/` or `decisions/` — no architecture decision records
- Any AI provenance annotation system

---

## Domain 1: Agent Behavior Contracts

*Does the repo define what agents are allowed to do, how they should behave, and what escalation is required?*

### `.claude/settings.local.json`

**HALOS concept:** Agent behavior contract

**Alignment:** Partial

**What it covers:**
- Defines allowed bash operations (jekyll, git, curl, bundle)
- Defines allowed read paths
- Defines node/server detection operations
- Restricts implicitly by omission (only listed operations allowed)

**Gaps:**
- No prose explanation of agent scope or intent
- No guidance on what agents should escalate vs. decide independently
- No versioning or ownership of the permissions file
- No CLAUDE.md or equivalent human-readable companion doc
- No definition of which actions require human approval before execution
- No explicit prohibition on silent conflict resolution

**Conflict ID:** CONFLICT-001

---

## Domain 2: Agent Capabilities

*Does the repo declare what agents can access, create, modify, or deploy?*

### `.claude/settings.local.json` (capabilities scope)

**HALOS concept:** Agent capability declaration

**Alignment:** Partial

**What it covers:**
- Implicitly scopes Claude Code to local development operations
- Allows git operations (status, diff, log, commit, push)
- Allows Jekyll serve and build commands
- Allows HTTP checks against localhost

**Gaps:**
- No explicit capability boundary for content creation vs. code changes
- No declaration of what Claude Code cannot do (e.g., no `rm -rf`, no force push)
- No separation between read-only and write capabilities
- GitHub Actions (`pages.yml`) capabilities are not declared anywhere as agent capabilities — they run automatically on push with `contents:read`, `pages:write`, `id-token:write`

**Conflict ID:** CONFLICT-001 (shared with Domain 1)

---

## Domain 3: Governance Policies

*Does the repo have contribution guidelines, ownership declarations, code review requirements, or behavioral standards?*

### LICENSE (CC-BY-4.0)

**HALOS concept:** Content authorship and rights framework

**Alignment:** Partial

**What it covers:**
- Requires attribution for derivative works
- Allows sharing and adaptation

**Gaps:**
- Does not address AI-generated contributions
- Does not define how AI involvement is attributed under CC-BY-4.0
- No guidance on whether AI-assisted content satisfies "human authorship" for the license

**Conflict ID:** CONFLICT-002

### Missing: CONTRIBUTING.md

**HALOS concept:** Contribution governance

**Alignment:** Gap

**What HALOS suggests:** A contribution governance document should define:
- Who can contribute
- How changes are reviewed
- What kinds of changes require human approval
- How agent-assisted contributions are handled

**Conflict ID:** CONFLICT-003

### Missing: CODEOWNERS

**HALOS concept:** Ownership and accountability mapping

**Alignment:** Gap

**What HALOS suggests:** Ownership declarations ensure human accountability for each part of the repo.

**Conflict ID:** CONFLICT-004

### Missing: Pull Request Template

**HALOS concept:** Structured contribution provenance

**Alignment:** Gap

**What HALOS suggests:** PR templates can capture AI involvement, attribution, and change rationale at contribution time.

**Conflict ID:** CONFLICT-005

---

## Domain 4: Decision Provenance

*Does the repo record why architectural or governance decisions were made?*

### README.md (partial)

**HALOS concept:** Decision documentation

**Alignment:** Partial

**What it covers:**
- Explains project structure at a high level
- Documents the "blueprint" usage pattern
- Describes deployment approach

**Gaps:**
- No rationale for technology choices (Jekyll over other SSGs)
- No history of significant decisions
- No ADR format or equivalent

### Missing: ADRs / Decision Records

**HALOS concept:** Decision provenance

**Alignment:** Gap

**What HALOS suggests:** Significant decisions (e.g., Jekyll adoption, CC-BY-4.0 choice, HALOS color token integration, GitHub Pages deployment) should have lightweight records explaining the decision context, options considered, and outcome.

**Conflict ID:** CONFLICT-006

---

## Domain 5: Data Provenance and Traceability

*Is it possible to trace who (human or agent) contributed what, and when?*

### Git History

**HALOS concept:** Contribution traceability

**Alignment:** Partial

**What it covers:**
- Git commit history provides a log of changes with author and timestamp
- GitHub attribute commits to accounts

**Gaps:**
- Git history does not distinguish AI-assisted commits from purely human commits
- No commit convention or tag indicating AI involvement
- No provenance metadata in content files (front matter does not include `ai_assisted: true` or equivalent)
- No conversation logs or session records for AI-assisted sessions

**Conflict ID:** CONFLICT-007

### assets/style.css (HALOS design tokens)

**HALOS concept:** Artifact provenance

**Alignment:** Partial

**Notes:** The CSS includes HALOS-derived color tokens (`--nh-navy`, `--nh-blue-*`). These appear to be handcrafted but there is no annotation of their origin, whether they were AI-assisted, or which version of HALOS design language they reference.

**Conflict ID:** CONFLICT-007 (same gap: no AI attribution system)

---

## Domain 6: Infrastructure and Deployment

*Are CI/CD pipelines, deployment targets, and infrastructure changes governed?*

### `.github/workflows/pages.yml`

**HALOS concept:** Infrastructure and deployment governance

**Alignment:** Partial

**What it covers:**
- Automated Jekyll build on push to `main`
- Deploy to GitHub Pages
- Uses pinned action versions (`@v4`, `@v1`)
- Scoped permissions (`pages:write`, `id-token:write`)

**Gaps:**
- No deployment approval gate (any push to `main` triggers deploy)
- No human review requirement before deployment
- No notification or audit trail beyond GitHub Actions logs
- No rollback procedure documented
- No staging environment

**Notes:** For a public-facing site representing the HALOS org, automatic deployment on any `main` push without a required review is a governance gap. However, this may be acceptable given the repo's nature as a content site.

**Conflict ID:** CONFLICT-004 (CODEOWNERS would provide implicit deploy governance)

---

## Coverage Summary Matrix

| Domain | Artifacts Found | Alignment | Conflicts |
|--------|----------------|-----------|-----------|
| 1. Agent behavior contracts | `.claude/settings.local.json` | Partial | CONFLICT-001 |
| 2. Agent capabilities | `.claude/settings.local.json` | Partial | CONFLICT-001 |
| 3. Governance policies | `LICENSE` | Partial + Gap | CONFLICT-002, 003, 004, 005 |
| 4. Decision provenance | `README.md` | Partial + Gap | CONFLICT-006 |
| 5. Data provenance & traceability | Git history | Partial + Gap | CONFLICT-007 |
| 6. Infrastructure & deployment | `.github/workflows/pages.yml` | Partial | CONFLICT-004 |

### Overall Coverage Assessment

| Rating | Domains |
|--------|---------|
| Strong alignment | None |
| Partial alignment | Agent behavior (1, 2), Deployment (6), License/docs (3, 4, 5) |
| Gap | Contribution governance (3), Decision records (4), AI provenance (5) |

**Summary:** This is a lean content repository with minimal governance overhead — appropriate for its size and purpose. The gaps are primarily in AI-specific governance (provenance, attribution, conflict disclosure), which is notable given this is the HALOS organization's own website. All gaps are addressable additively without disrupting existing workflows.
