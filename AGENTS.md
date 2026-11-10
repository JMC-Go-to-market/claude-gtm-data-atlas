# Contributing

This repository holds the `gtm-data-atlas` skill and its Claude Code plugin manifest.

## Layout

- `skills/gtm-data-atlas/SKILL.md`: the skill. `skills/gtm-data-atlas/references/` holds the files it reads.
- `plugin.json`: the plugin manifest (name, version, description, MCP server configuration).
- `README.md`: install and usage.

## Changing the skill

- Keep the skill self-contained: everything it needs lives under `skills/gtm-data-atlas/`.
- When behavior changes, bump `version` in `plugin.json`, and keep `description` valid for strict YAML and JSON parsers.
- Never commit credentials, API keys or customer data. The Atlas MCP needs no key.

## Pull requests

Open an issue first. In the pull request body, link it (`Closes #N`) and add an `Agent:` line naming who wrote the change (`Agent: human / <name>` for a person). The pull request template has both lines.
