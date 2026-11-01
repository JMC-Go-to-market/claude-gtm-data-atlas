# gtm-data-atlas

Which data source for this list? The top 5 for the job from JMC's free GTM Data Atlas MCP, free sources first, with what each one misses and when it was last checked. No key. Configures the MCP server.

An [Agent Skill](https://agentskills.io) and Claude Code plugin from JMC Go-to-Market Systems. Use it when the user asks where to get a kind of GTM data (company registries, work emails, intent, hiring signals, funding, ads), or whether a free source covers it.

## What it does

The skill tells your agent when to call the free GTM Data Atlas MCP server, how to write the need, and how to answer:

- lead with the free-first route: which sources to start with, and which paid source to add only for what the free ones miss;
- name each source with what it covers and what it misses;
- leave out a result that plainly doesn't fit the job;
- cite each source with its page and the date it was last checked.

The server has one read-only tool, `atlas-find`, at `https://api.jaymountconsulting.com/mcp/free`. It needs no key or account, and each caller gets 30 calls an hour. The full write-up of each source is on its page at [jaymountconsulting.com/data-sources](https://jaymountconsulting.com/data-sources).

## Install

### Claude Code

```
/plugin marketplace add JMC-Go-to-market/claude-gtm-data-atlas
/plugin install gtm-data-atlas@gtm-data-atlas
```

The plugin also connects the MCP server. From a terminal, the same commands work as `claude plugin marketplace add JMC-Go-to-market/claude-gtm-data-atlas` and `claude plugin install gtm-data-atlas@gtm-data-atlas`.

### Cursor, Codex and other agents (skills CLI)

```
npx skills add JMC-Go-to-market/claude-gtm-data-atlas
```

### claude.ai and the Claude API

Upload `skills/gtm-data-atlas` as a custom skill, and add the MCP server as a custom connector (no authentication).

### MCP only

```
claude mcp add --transport http gtm-data-atlas https://api.jaymountconsulting.com/mcp/free
```

Setup for Claude Desktop, Cursor, ChatGPT and other clients is in [skills/gtm-data-atlas/references/mcp-setup.md](skills/gtm-data-atlas/references/mcp-setup.md).

## How well it answers

The free tool ranks sources by the words in the need. We measure it with 20 realistic needs, each labelled with the sources a GTM practitioner would accept in the top 3, plus 6 held-out needs written separately, over all 585 ready sources (measured 2026-11-01):

| | needs with an accepted source in the top 3 | top-3 slots filled by accepted sources |
|---|---|---|
| 20 eval needs | 80% | 43% |
| 6 held-out needs | 83% | 56% |

It still misses some needs whose words don't appear in the sources' descriptions: technographics, mobile numbers for decision makers, SEC filings, H-1B sponsorship and website-visitor identification. That's why the skill tells the agent to drop results that don't fit.

## Layout

```
.claude-plugin/plugin.json        the Claude Code plugin, with the MCP server
.claude-plugin/marketplace.json   a one-plugin marketplace named gtm-data-atlas
plugin.json                       the same plugin for agent-plugins.org clients
skills/gtm-data-atlas/SKILL.md    the skill
skills/gtm-data-atlas/references/ client setup, loaded only when needed
```

## License

MIT. See [LICENSE](LICENSE).
