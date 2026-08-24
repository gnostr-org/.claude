---
name: gnostr-github-automation
description: Install and adapt reusable GitHub Actions workflows, composite actions, and CI skill docs derived from gnostr-org/gnostr.
---

# gnostr GitHub automation

Use this skill when you want to bring the reusable GitHub automation patterns from `gnostr-org/gnostr` into another repository without copying that repo's entire `.github/` tree verbatim.

## What this skill packages

- composite action templates under `templates/actions/`
- workflow templates under `templates/workflows/`
- skill-document templates under `templates/skills/`

These files are adapted from `gnostr-org/gnostr` so they fit this repo's skill-based distribution model.

## Rules

- Do not install the upstream `.github/workflows/*.yml` files wholesale into an unrelated repo.
- Copy only the templates you need and strip the `.tmpl` suffix when installing them.
- Review every trigger, secret, relay URL, and runner assumption before enabling a workflow.
- `gnostr-notify` assumes the `gnostr` CLI is already available in the job and that you pass a real private key via a GitHub Actions secret.
- `run-all-workflows` requires a dedicated repository-dispatch token secret; `GITHUB_TOKEN` is not enough.
- The `gnostr` and `gnostr-chat-ci-updates` skill templates are reference docs; adapt repo-specific commands and nested sub-skill links before publishing them.

## Procedure

1. Create the target directories under `.github/actions`, `.github/workflows`, or `.github/skills`.
2. Copy the required template files from this skill into the target repo, removing `.tmpl` from the filenames.
3. Adapt repository-specific values like workflow names, dispatch event types, secrets, relays, and install steps.
4. Validate the resulting workflows with the target repo's existing CI strategy before enabling them.

## Included templates

### Composite actions

- `templates/actions/calculate-odd-even/action.yml.tmpl`
- `templates/actions/gnostr-notify/action.yml.tmpl`

### Workflows

- `templates/workflows/get_time.yml.tmpl`
- `templates/workflows/run-all-workflows.yml.tmpl`

### Skill docs

- `templates/skills/gnostr/SKILL.md.tmpl`
- `templates/skills/gnostr-chat-ci-updates/SKILL.md.tmpl`

## Source

Adapted from `gnostr-org/gnostr` commit `00095b368dc3a09074f9259b264f419fe103f5e0`.
