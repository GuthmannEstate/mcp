<p align="center">
  <img src="https://cdn.guthmann.estate/branding/logo/png/circle/standard.png" width="88" alt="GUTHMANN® logo" />
</p>

<h1 align="center">GUTHMANN® Market Intelligence MCP Server</h1>

<p align="center">The Berlin real estate market, machine-readable: free market data for AI agents.<br />No API key, no registration — connect and query.</p>

<p align="center">
  <a href="https://guthmann.estate/en/market-intelligence/"><img src="https://img.shields.io/badge/Website-guthmann.estate-00806C" alt="Website" /></a>
  <a href="https://registry.modelcontextprotocol.io/v0/servers?search=guthmann"><img src="https://img.shields.io/badge/MCP_Registry-estate.guthmann%2Fmarket--intelligence-blue" alt="MCP Registry" /></a>
  <img src="https://img.shields.io/badge/Auth-none-brightgreen" alt="No auth required" />
</p>

<p align="center">
  <a href="https://cursor.com/en/install-mcp?name=guthmann&config=eyJ1cmwiOiJodHRwczovL21jcC5ndXRobWFubi5lc3RhdGUvbWNwIn0="><img src="https://cursor.com/deeplink/mcp-install-dark.svg" alt="Install in Cursor" height="28" /></a>
  <a href="https://insiders.vscode.dev/redirect/mcp/install?name=guthmann&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//mcp.guthmann.estate/mcp%22%7D"><img src="https://img.shields.io/badge/VS_Code-Install_Server-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white" alt="Install in VS Code" height="28" /></a>
</p>

---

```
https://mcp.guthmann.estate/mcp
```

Streamable HTTP, stateless, rate-limited at 20 requests per minute per IP. Listed in the official [MCP Registry](https://registry.modelcontextprotocol.io) as `estate.guthmann/market-intelligence`.

## What you can ask

```txt
Which neighbourhoods make up the Berlin district of Pankow?
```

```txt
Find the LOR planning area for Kollwitzkiez and show its details.
```

```txt
List all 12 Berlin districts with their key facts.
```

## Connect

**Claude Code**

```bash
claude mcp add --transport http guthmann https://mcp.guthmann.estate/mcp
```

**Claude.ai / Claude Desktop** — Settings → Connectors → *Add custom connector*, then paste the server URL above.

**Cursor** — use the install button above, or add manually:

```json
{
  "mcpServers": {
    "guthmann": {
      "url": "https://mcp.guthmann.estate/mcp"
    }
  }
}
```

**VS Code** — use the install button above, or add to your MCP configuration:

```json
{
  "servers": {
    "guthmann": {
      "type": "http",
      "url": "https://mcp.guthmann.estate/mcp"
    }
  }
}
```

Any other MCP client with Streamable HTTP support works the same way — point it at the server URL, no credentials needed.

## Tools

The current scope is the Berlin area hierarchy — the geographic backbone every market query builds on: the 12 districts (Bezirke), their neighbourhoods (Ortsteile) and the LOR planning areas (Planungsräume).

| Tool | What it returns |
|---|---|
| `berlin_bezirke` | All 12 districts |
| `berlin_bezirk_details` | One district in detail |
| `berlin_ortsteile` | Neighbourhoods, filterable by district |
| `berlin_ortsteil_details` | One neighbourhood in detail |
| `berlin_planungsraeume` | LOR planning areas, filterable |
| `berlin_planungsraum_suche` | Search planning areas by name |
| `berlin_planungsraum_details` | One planning area in detail |

The server is being extended step by step towards the full [Market Intelligence](https://guthmann.estate/en/market-intelligence/) scope of the website: prices, rents, market trends and neighbourhood analytics for Berlin.

## About

[GUTHMANN®](https://guthmann.estate) is a Berlin real estate broker. Market Intelligence is our public research area — this server is its machine-readable counterpart.

The server implementation lives in a private monorepo; this repository is the public home of the service: documentation, endpoint and issue tracker.
