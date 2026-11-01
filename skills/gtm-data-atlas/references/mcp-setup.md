# Connect the GTM Data Atlas MCP server

Endpoint: `https://api.jaymountconsulting.com/mcp/free`. It uses Streamable HTTP, has one read-only tool (`atlas-find`), and needs no key or account. Each caller gets 30 calls an hour.

## Claude Code

If you installed this repository's `gtm-data-atlas` plugin, the server is already configured. To add it by hand, run:

```
claude mcp add --transport http gtm-data-atlas https://api.jaymountconsulting.com/mcp/free
```

To share it with a project, use `.mcp.json` at the project root:

```json
{
  "mcpServers": {
    "gtm-data-atlas": {
      "type": "http",
      "url": "https://api.jaymountconsulting.com/mcp/free"
    }
  }
}
```

## Claude Desktop and claude.ai

1. Open Settings, then Connectors.
2. Add a custom connector.
3. Paste the endpoint URL above. No authentication is needed.

If your build only takes local servers in `claude_desktop_config.json`, bridge the remote server over stdio:

```json
{
  "mcpServers": {
    "gtm-data-atlas": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://api.jaymountconsulting.com/mcp/free"]
    }
  }
}
```

Restart the app fully after editing the file.

## Cursor

Use `.cursor/mcp.json` in the project, or `~/.cursor/mcp.json` for every project:

```json
{
  "mcpServers": {
    "gtm-data-atlas": {
      "url": "https://api.jaymountconsulting.com/mcp/free"
    }
  }
}
```

## ChatGPT

1. Turn on developer mode in Settings, then Connectors.
2. Create a connector with the endpoint URL above.
3. Choose no authentication.

## Any other MCP client

- Transport: Streamable HTTP
- URL: `https://api.jaymountconsulting.com/mcp/free`
- Authentication: none
