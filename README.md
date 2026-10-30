<img src="assets/logo.png" alt="" width="72" align="right">

# OpenCityRecord MCP server

OpenCityRecord gives your AI assistant the public record of local government: what was said at city council, planning
commission, and county meetings, how each body voted, and what the city put in writing. Every answer links back to the
source: the meeting page, the exact video timestamp, or the motion in the approved minutes.

This repository holds connection configuration only. The server itself is a hosted service; there is nothing to install
or run.

| | |
|---|---|
| Endpoint | `https://mcp.opencityrecord.org/mcp` (Streamable HTTP) |
| Auth | OAuth 2.1 with Dynamic Client Registration: sign in with an OpenCityRecord account, no API key |
| Registry | [`org.opencityrecord/opencity`](https://registry.modelcontextprotocol.io/v0.1/servers?search=org.opencityrecord) in the official MCP Registry |
| Docs and sign-up | https://opencityrecord.org/mcp (the free account covers one city) |
| Support | support@opencityrecord.org |

## What it covers

- Meeting transcripts with jump-to-timestamp video links
- Motions and roll-call votes from approved minutes, with dollar amounts
- Agendas, minutes, staff reports, packets, ordinances, and resolutions
- Current and former elected officials, with voting records
- Issue and development-application timelines across meetings

Coverage today is 340+ cities and counties in 14 states, mostly in Texas, Utah, California, Florida, Arizona, and New
York, updated within hours of meetings being published.

Elected officials are identified; members of the public, applicants, and city staff speaking at the mic are never named.
All tools are read-only.

## Connect

**Claude, ChatGPT, and other chat apps:** step-by-step instructions are at https://opencityrecord.org/mcp.

**Claude Code**

```bash
claude mcp add --transport http opencityrecord https://mcp.opencityrecord.org/mcp
```

Then run `/mcp` in Claude Code to sign in.

**Cursor**

This repository is a Cursor plugin (`.cursor-plugin/plugin.json` + `mcp.json`). To try it before it is in the Cursor
Marketplace, clone it and add the folder under Cursor Settings → Plugins. Or add the server to `~/.cursor/mcp.json`
yourself:

```json
{
  "mcpServers": {
    "opencityrecord": { "url": "https://mcp.opencityrecord.org/mcp" }
  }
}
```

**Google Antigravity**

This repository is an Antigravity plugin. Install it with the Antigravity CLI:

```bash
agy plugin install https://github.com/OpenCityUSA/opencityrecord-mcp
```

Or add the server to `~/.gemini/config/mcp_config.json` yourself:

```json
{
  "mcpServers": {
    "opencityrecord": { "serverUrl": "https://mcp.opencityrecord.org/mcp" }
  }
}
```

Antigravity handles the OAuth sign-in on first use.

**Gemini CLI**

This repository is also a Gemini CLI extension (`gemini-extension.json` + `GEMINI.md`):

```bash
gemini extensions install https://github.com/OpenCityUSA/opencityrecord-mcp
```

Then run `/mcp auth opencityrecord` once to sign in. Or add the server to `~/.gemini/settings.json` yourself:

```json
{
  "mcpServers": {
    "opencityrecord": {
      "httpUrl": "https://mcp.opencityrecord.org/mcp",
      "oauth": { "enabled": true }
    }
  }
}
```

**Gemini app**

Once the OpenCityRecord connected app is published, type `@OpenCityRecord` followed by your question. Until then you can
connect it yourself: open https://gemini.google.com/devmode, choose **+ Create new**, paste
`https://mcp.opencityrecord.org/mcp` as the MCP Server URL, and pick **Dynamic Client Registration** under
**Authentication**.

## Example questions

- "What did the Lehi City Council decide in September?"
- "Who is on the Salt Lake City council?"
- "Which cities have voted on Flock Safety license-plate cameras, and what did they decide?"
- "How did the short-term rental issue play out in Lehi?"
- "How has Lehi council member Emily Lockhart voted since July?"

## Files

| File | Used by |
|---|---|
| `.cursor-plugin/plugin.json`, `mcp.json` | Cursor plugin |
| `plugin.json`, `mcp_config.json` | Google Antigravity plugin |
| `gemini-extension.json`, `GEMINI.md` | Gemini CLI extension (geminicli.com extensions gallery) |
| `lhm.plugin.json` | LobeHub MCP Marketplace listing |

## License

MIT. See [LICENSE](LICENSE). The license covers the configuration in this repository, not the hosted service or its data.
