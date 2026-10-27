# charly-internals-extra

**RETIRED — this repo authors no skill any more.** It was the `charly-internals-extra`
concept candy, the `internals` family's overflow (split out of `layer-charly-internals` to
stay under GitHub's 1 MiB contents-API cap). All eight of its entities — two skills and six
`type: agent` definitions — have moved beside the code, plugin, contract or rulebook each one
documents (opencharly/opencharly#600, #611), byte-identical at every destination. It is
archived once its drain has merged and been tagged.

## Where the prose went

| entity | now authored in |
|---|---|
| `strict-policy` | the umbrella, `opencharly/opencharly` — `.agents/skills/strict-policy/SKILL.md` |
| `vm-spec` | [`opencharly/spec`](https://github.com/opencharly/spec) — `.agents/skills/vm-spec/SKILL.md` |
| `check-bed-runner` | the umbrella — `.agents/agents/check-bed-runner.md` |
| `deploy-verifier` | the umbrella — `.agents/agents/deploy-verifier.md` |
| `layer-validator` | the umbrella — `.agents/agents/layer-validator.md` |
| `pr-validator` | the umbrella — `.agents/agents/pr-validator.md` |
| `root-cause-analyzer` | the umbrella — `.agents/agents/root-cause-analyzer.md` |
| `testing-validator` | the umbrella — `.agents/agents/testing-validator.md` |

`strict-policy` and the six agent definitions are **general guidance** — they operationalize
R1–R5 + RDD + ADE and describe a role in the org's development workflow, with no code, plugin
or config behind them — so Part II #5's first clause places them in the one repo every
consumer shares. `vm-spec` is the exception: its Source table names
`spec/spec/cue_types_gen.go` and `schema/vm.cue`, so it goes to the repo those files live in.
The full per-entity derivation is in `AGENTS.md`.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-internals-extra` (retired concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | nothing: no `skill:` or `agent` node |
| Projected to | nowhere — the corpus publishes these bodies from the repos above |
| Service / port | none |

## How to use it

Do not. Read a skill from the repo that authors it (the table above), or the agent roster
from the umbrella's `.agents/agents/`, or the projected
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus.

## Layout

- `charly.yml` — the `charly-internals-extra:` candy node only, with a `true` no-op `run:`
  step and a `true` no-op `check:` step. Neither is an assertion: there is no body left here
  to resolve.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — this user overview.

## Related

- Owning skills now: `/charly-internals:strict-policy` (umbrella),
  `/charly-internals:vm-spec` (spec)
- Agent roster: `/charly-internals:agents`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
