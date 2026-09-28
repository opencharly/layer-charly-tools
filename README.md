# charly-tools

The `charly-tools` family — the concept candy for the CLI-utility tool skills.

The `charly-tools` candy is a **concept candy**: it ships no install content. It
is the family umbrella for the `tools` skills, but it currently carries **no
`skill:` entity** — every tool skill in the family is owned by its own
`layer-*` repo and projected from there:

- `layer-ripgrep` → `/charly-tools:ripgrep`
- `layer-blogwatcher` → `/charly-tools:blogwatcher`
- `layer-dsh` → `/charly-tools:dsh`, `/charly-tools:dsh-cli`
- … and the rest of the `marketplace/tools/skills/` family.

This repo is therefore a placeholder concept candy: it exists so the family has a
home, and it carries no projected skill of its own. The missing owning `skill:`
entity is tracked by
[opencharly/opencharly#291](https://github.com/opencharly/opencharly/issues/291)
(the batch authoring the missing `skill:` entities for the `layer-*` candies).

`candy/plugin-marketplace` regenerates the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus from
the owning repos' entities.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-tools` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 0 `skill:` entities (family skills live in their own `layer-*` repos) |
| Projected to | nothing (no entity) |
| Service / port | none |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. To reference
it directly, compose it in a box. A box is a `candy:` node carrying the box's
`base:` image and a nested `candy:` list of layer refs (the nested `candy:` is
the composition list; the outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-tools:v2026.239.1622'
```

To use an actual CLI tool, compose its own `layer-*` repo (for example
`@github.com/opencharly/layer-ripgrep:<tag>`), not this umbrella.

## Layout

- `charly.yml` — the `charly-tools:` concept candy entity (no `skill:` entity).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: none yet — tracked by [opencharly/opencharly#291](https://github.com/opencharly/opencharly/issues/291)
- Authoring reference: `/charly-image:layer`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
