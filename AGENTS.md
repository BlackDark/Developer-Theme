# AGENTS.md

Hugo-based CV site, theme `almeida-cv` vendored under `themes/`.

## Tooling

- Package manager: pnpm. Hugo comes from the `hugo-extended` devDependency, which exposes a `hugo` CLI directly.
- pnpm blocks postinstall scripts by default. `hugo-extended`'s install is allowed via `pnpm-workspace.yaml`'s `allowBuilds` — don't remove that entry, or the Hugo binary won't install.

## Content

- `data/content.yaml` — English content
- `data/de/content.yaml` — German content
- Keep both files in structural sync: same number of Experience/Position/Details entries, same meaning per bullet. Wording may differ naturally per language, but facts and bullet count must match.

## Skills sidebar

`Skills:` in content.yaml is a standalone inventory of everything the person knows, shown in the sidebar via `_skills.html`. It does not need to trace 1:1 to the Experience bullets — a CV can't list every tool used in the timeline text, and the sidebar covers that gap. A skill missing from Experience, or an Experience tool missing from Skills, is not a bug.

## Requirements-driven CV edits

- Only add a bullet to satisfy a tender/job requirement if it's true — ask the user for real facts/dates rather than inferring or padding.
- Watch for formulaic phrase reuse across unrelated roles (e.g. the same "IT concept for migration strategy" wording copy-pasted into every AWS-touching role) — it reads as tender-keyword insertion, not genuine experience.

## Writing style

- Use the `humanizer` skill when writing or editing CV bullets, to strip AI-writing tells.
- Keep bullets as short fragments, matching the CV's existing terse style. A bullet needing a semicolon or multiple connectors should be split or trimmed.
