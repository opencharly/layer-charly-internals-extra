# AGENTS.md — layer-charly-internals-extra

**This repo is RETIRED.** It authors no skill and no agent definition any more: all eight
bodies it carried have moved beside the code, plugin, contract or rulebook each of them
documents (opencharly/opencharly#600, #611), and every one is byte-identical at its
destination. It is archived once its drain has merged and been tagged.

Canonical files:

- `charly.yml` — the `charly-internals-extra:` candy node and nothing else. It is a real
  `candy:` because a project needs one; its `plan:` is a `true` no-op `run:` step plus a
  `true` no-op `check:` step, and **neither is an assertion** — there is no body left here
  for the body-existence gate to resolve.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — user overview only; never agent guidance.

## Where the prose went (the destination map)

Measured as git blobs: this repo's pre-drain `main` versus each destination's `origin/main`.
Every row compares equal — the move relocated the AUTHORITY over a body, it did not rewrite
one.

| entity | destination | path there | blob (carrier / destination) |
|---|---|---|---|
| `strict-policy` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/skills/strict-policy/SKILL.md` | `f9b386e0eb22` == `f9b386e0eb22` |
| `vm-spec` | `opencharly/spec` @ `origin/main` | `.agents/skills/vm-spec/SKILL.md` | `58bace23d6ec` == `58bace23d6ec` |
| `check-bed-runner` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/agents/check-bed-runner.md` | `dde2044b47dd` == `dde2044b47dd` |
| `deploy-verifier` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/agents/deploy-verifier.md` | `31b3a4ed3c86` == `31b3a4ed3c86` |
| `layer-validator` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/agents/layer-validator.md` | `367c500d299b` == `367c500d299b` |
| `pr-validator` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/agents/pr-validator.md` | `82ec3502decc` == `82ec3502decc` |
| `root-cause-analyzer` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/agents/root-cause-analyzer.md` | `a31f05843acc` == `a31f05843acc` |
| `testing-validator` | `opencharly/opencharly` @ `v2026.300.1151` | `.agents/agents/testing-validator.md` | `968a7eb89430` == `968a7eb89430` |

`strict-policy` is the **general-guidance** class: it operationalizes `AGENTS.md` R1–R5 plus
RDD and ADE, names no code, plugin or config, and its own text defers its forbidden-excuse
catalog to `/charly-internals:cutover-policy` and its placement law to
`/charly-internals:plugin` — both already umbrella skills. The umbrella is therefore its home
on Part II #5's FIRST clause, and the `#611` exception (a home repo that cannot AUTHOR skills)
is not what places it: that exception covers `git-workflow` and `repo-setup`, whose config
home is `opencharly/.github`. `opencharly/opencharly#627` concluded exactly this and landed
the body; this drain is the REMOVE half of that pair.

The six agent definitions describe a ROLE in the org's development workflow — an evaluator, a
bed executor, the R1 analyzer, the R10 tester — and no code implements one; the umbrella's
`agents` skill is the roster that DESCRIBES them, so the roster and its members now live and
are tagged together.

## What still lives here

Only the candy node, the tag workflow and history. Nothing in this repo is a source of
guidance any more. The dangling `owner: charly-internals` this repo carried on all eight nodes
— opencharly/layer-charly-internals-extra#30 — is gone with the nodes: the issue gives two
legal fixes and forbids applying both, and the drain is the one that removed them rather than
rewriting a field.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
