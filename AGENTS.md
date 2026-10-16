# AGENTS.md — layer-charly-internals-extra

Standalone candy repo for the `charly-internals-extra` concept candy — it ships
no install content and owns the overflow entities of the `internals` family,
split out of `layer-charly-internals` to stay under GitHub's 1 MiB
contents-API cap. The `owner:` field stays `charly-internals`. Each entity's
prose is authored with the entity itself, under this repo's own `.agents/` trees;
`charly.yml` at the repo root keeps only the routing metadata its consumers read,
and `candy/plugin-marketplace` regenerates the standalone opencharly/marketplace
corpus from the two together.

Canonical files:

- `charly.yml` — the `charly-internals-extra:` concept candy entity plus the
  routing metadata for its eight entities: the two skills `strict-policy` and
  `vm-spec`, and the six agent definitions `check-bed-runner`,
  `deploy-verifier`, `layer-validator`, `pr-validator`, `root-cause-analyzer`,
  `testing-validator`.
- `.agents/` — the authored prose those entities route to: each skill's
  `SKILL.md` and each agent definition's markdown file. The marketplace corpus
  holds the projection of these; edit that copy never.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-internals:strict-policy` — the R1–R5 + RDD/ADE operationalization.
  Load before editing the `strict-policy` skill's prose.
- `/charly-internals:vm-spec` — the `VmSpec` Go type reference. Load before
  editing the `vm-spec` skill's prose.
- `/charly-internals:agents` — the agent/roster contract (how agent definitions
  are authored and projected, the enforcer/executor split). Load before editing
  any agent definition.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, package sections, service declarations).
  Load before editing any entity field or plan step.

## Build / validate / test

- `charly box validate` at the repo root — the structural check: the manifest
  must parse and validate. The routing-only `skill:` shape these entities use is
  younger than some binaries: a charly built from an older source rejects it with
  `#SkillInput.description: incomplete value !=""`. Run it with a worktree-local
  build (`./scripts/bootstrap-charly.sh`, then `CHARLY_PLUGIN_ONLY=1` so a
  worktree build does not scan the packaged plugins from `/usr/lib/charly/plugins`),
  never with the shared host install.
- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has no
  per-repo candy gate.
- The candy is documentation-only: its `plan:` is a `true` no-op plus a `true`
  `check:` that the overflow skill/agent entities are present and generated into
  the marketplace. There is no live bed.

## Modify this repo

- A skill's or an agent's prose is the projected usage source. Edit it with the
  entity, never the generated file in the marketplace corpus; a corpus
  regeneration (`charly marketplace generate`) projects the prose and the
  routing metadata together.
- When a rule's operationalization or an agent's contract changes, update the
  matching prose in the same change so the corpus does not drift.
- Keep the concept candy's `plan:` no-op; it exists only to carry the routing
  metadata.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
