# UPSTREAM

This is a maintained fork of [obsidianmd/obsidian-clipper](https://github.com/obsidianmd/obsidian-clipper).

## Baseline

- Tag: `upstream-base-v0.1`
- Upstream version: `<verify before development>`
- Commit: `<verify before development>`

## Maintenance Rules

- Preserve upstream behavior.
- Prefer additive changes over rewrites.
- Do not replace upstream extraction/template/preview/highlight/save pipelines when they can be extended.
- Reuse existing upstream logic and extension points whenever practical instead of implementing parallel custom versions.
- Keep EngramWeave-specific changes isolated and easy to review where possible.

## Remotes

origin   = EngramWeave fork
upstream = official Obsidian Web Clipper

## Workflow

```powershell
# Add upstream remote (run once)
git remote add upstream https://github.com/obsidianmd/obsidian-clipper.git

# Fetch latest upstream history
git fetch upstream

# Inspect our custom changes against upstream
git log upstream/main..main --oneline
git diff upstream/main...main

# Sync a new upstream version
git switch main
git pull origin main
git switch -c sync/upstream-<version>
git merge upstream/main

# Resolve conflicts, run regression tests,
# then merge sync/upstream-<version> back into main.
```

## Branches

- `main` — stable EngramWeave version
- `feat/*` — feature development
- `fix/*` — bug fixes
- `sync/upstream-*` — temporary upstream synchronization branches