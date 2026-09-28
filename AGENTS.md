# AGENTS.md — layer-charly-tools

Standalone candy repo for the `charly-tools` concept candy — it ships no install
content. It is the `tools` family umbrella, but it carries **no `skill:` entity**
of its own: every tool skill in the family is owned by its own `layer-*` repo and
projected from there.

Canonical files:

- `charly.yml` — the `charly-tools:` concept candy entity (no `skill:` entity).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, package sections, service declarations).
  Load before editing any entity field or plan step.
- The family skills are owned elsewhere: the `tools` skills
  (`/charly-tools:ripgrep`, `/charly-tools:dsh`, `/charly-tools:yay`, …) live in
  their own `layer-*` repos. Load the specific tool's skill from its owning repo
  when a change touches it.
- **Missing owning skill:** this concept candy has no `skill:` entity, so no
  `/charly-tools:*` page is projected for it. The gap is recorded against the
  named batch
  [opencharly/opencharly#291](https://github.com/opencharly/opencharly/issues/291)
  (author the missing `skill:` entities for the `layer-*` candies).

## Build / validate / test

- `charly box validate` at the repo root — the structural check: the manifest
  must parse and validate at the installed charly.
- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has no
  per-repo candy gate. Its only workflow file is
  `.github/workflows/tag-on-merge.yml`.
- The candy is documentation-only: its `plan:` is a `true` no-op plus a `true`
  `check:` that the family's skill entities are present and generated into the
  marketplace. There is no live bed.

## Modify this repo

- There is no `skill:` entity here to edit; the family's skills are authored in
  their own `layer-*` repos and projected by `charly marketplace generate`.
- Keep the concept candy's `plan:` no-op; it exists only as the family anchor.
- If the missing owning skill is authored, add the `skill:` entity here and
  update this signpost and the README in the same change.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
