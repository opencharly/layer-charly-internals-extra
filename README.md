# charly-internals-extra

The `charly-internals-extra` family — overflow internals skills and agent specs.

The `charly-internals-extra` candy is a **concept candy**: it ships no install
content and owns the overflow entities of the `internals` family — split out of
`layer-charly-internals` to stay under GitHub's 1 MiB contents-API cap. The
`owner:` field of every entity stays `charly-internals`, so the runtime
association is unchanged. It currently carries eight entities:

- Two `skill:` entities: `strict-policy` (the R1–R5 + RDD/ADE operationalization)
  and `vm-spec` (the `VmSpec` Go type reference).
- Six `skill:`-kind agent entities (`type: agent`): `check-bed-runner`,
  `deploy-verifier`, `layer-validator`, `pr-validator`, `root-cause-analyzer`,
  and `testing-validator` — projected as the `internals/agents/` roster.

`candy/plugin-marketplace` regenerates the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus from
these entities, so the skills and agents are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-internals-extra` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 8 entities: 2 `skill:` + 6 agent (`type: agent`) |
| Projected to | `marketplace/internals/skills/` and `marketplace/internals/agents/` |
| Service / port | none |

## How to use it

This repo is consumed as a **skill and agent source**, not as an image layer.
Edit the entities in `charly.yml`; the marketplace regeneration projects the two
skills into `/charly-internals:*` pages and the six agents into the internals
roster. To reference the repo directly, compose it in a box. A box is a `candy:`
node that carries the box's `base:` image and a nested `candy:` list of layer
refs (the nested `candy:` is the composition list; the outer `candy:` is the box
body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-internals-extra:v2026.268.1547'
```

## Layout

- `charly.yml` — the `charly-internals-extra:` concept candy entity plus eight
  entities: `strict-policy-skill`, `vm-spec-skill`, and the six
  `*-agent` entities.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skills: `/charly-internals:strict-policy`, `/charly-internals:vm-spec`
- Agent roster: `/charly-internals:agents`
- Authoring reference: `/charly-image:layer`
- Sibling: `opencharly/layer-charly-internals`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
