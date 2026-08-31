<p align="center">
  <img src="https://cdn.guthmann.estate/branding/logo/png/circle/standard.png" width="96" alt="GUTHMANN® logo" />
</p>

# GUTHMANN® Market Intelligence MCP Server

The Berlin real estate market, machine-readable: a free remote [MCP](https://modelcontextprotocol.io) server for AI agents by [GUTHMANN®](https://guthmann.estate/en/market-intelligence/).

No API key, no registration. Connect and query.

```
https://mcp.guthmann.estate/mcp
```

- **Transport:** Streamable HTTP
- **Auth:** none (public)
- **Rate limit:** 20 requests per minute per IP
- **Registry:** [`estate.guthmann/market-intelligence`](https://registry.modelcontextprotocol.io/v0/servers?search=guthmann) in the official MCP Registry

## Connect

**Claude Code**

```bash
claude mcp add --transport http guthmann https://mcp.guthmann.estate/mcp
```

**Claude.ai / Claude Desktop** — add a custom connector with the URL above.

**Cursor, VS Code and other MCP clients**

```json
{
  "mcpServers": {
    "guthmann-market-intelligence": {
      "url": "https://mcp.guthmann.estate/mcp"
    }
  }
}
```

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
