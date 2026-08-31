# AGENTS.md

Hugo-based CV site, theme `almeida-cv` vendored under `themes/`.

## Tooling

- Package manager: pnpm. Hugo binary comes from `hugo-extended` (devDependency), which exposes a `hugo` CLI directly — no more `hugo-bin`/buildTags config needed.
- pnpm blocks postinstall scripts by default; `hugo-extended`'s install is allowed via `pnpm-workspace.yaml`'s `allowBuilds`. Don't remove that entry or the Hugo binary won't install.
- CI (`.github/workflows/new-cv.yml`) uses `pnpm install --frozen-lockfile` + `pnpm run build`. Keep local and CI package manager in sync.

## Content

- `data/content.yaml` — English content
- `data/de/content.yaml` — German content
- Keep both files in structural sync: same number of Experience/Position/Details entries, same meaning per bullet. Wording may differ naturally per language, but facts and bullet count must match.

## Skills sidebar

- `Skills:` in content.yaml is a standalone inventory of everything the person knows, shown in the sidebar via `_skills.html`.
- It does NOT need to trace 1:1 to what's written in Experience bullets. A CV can't list every tool ever used in the timeline text; the sidebar exists to cover the gap.
- Do not treat "mentioned in Experience but missing from Skills" as a bug to fix, and do not remove a Skills entry just because no bullet mentions it. There are more real skills than what fits in the narrative text.

## Experience badges (removed)

- Per-role `Badges:` tags used to exist on Experience entries but were removed (duplicated the Skills sidebar). Do not re-add them.

## Requirements-driven CV edits

- When adding a bullet to satisfy a specific tender/job requirement, only add it if it's true — ask the user for real facts/dates rather than inferring or padding.
- Avoid formulaic phrase reuse across multiple unrelated roles when it's a giveaway of tender-keyword insertion (e.g. don't just copy-paste "IT concept for migration strategy" into every role that touches AWS).

## Writing style

- Use the `humanizer` skill (if available) when writing or editing CV bullets — strip AI-writing tells (inflated claims, filler phrases, forced clauses).
- Keep bullets concise: short fragments over full clauses, matching the CV's existing terse style. A bullet that needs a semicolon or multiple connectors is a sign it should be split or trimmed.
