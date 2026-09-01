<p align="center">
  <img src="https://cdn.guthmann.estate/branding/logo/png/circle/standard.png" width="88" alt="GUTHMANN® logo" />
</p>

<h1 align="center">GUTHMANN® Berlin Real Estate MCP Server</h1>

<p align="center">Berlin real estate for AI agents: granular market data and property search.<br />Free, no API key, no registration — connect and query.</p>

<p align="center">
  <a href="https://guthmann.estate/en/market-intelligence/"><img src="https://img.shields.io/badge/Website-guthmann.estate-00806C" alt="Website" /></a>
  <a href="https://registry.modelcontextprotocol.io/v0/servers?search=guthmann"><img src="https://img.shields.io/badge/MCP_Registry-estate.guthmann%2Fmcp-blue" alt="MCP Registry" /></a>
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

Streamable HTTP, stateless, rate-limited at 60 requests per minute per IP. Listed in the official [MCP Registry](https://registry.modelcontextprotocol.io) as `estate.guthmann/mcp`.

## What you can ask

```txt
Which neighbourhoods make up the Berlin district of Pankow?
```

```txt
Find the LOR planning area for Kollwitzkiez and show its details.
```

```txt
Show me apartments for sale in Prenzlauer Berg under 500k EUR.
```

```txt
List all 12 Berlin boroughs with their key facts.
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

The full public Market Intelligence scope of [guthmann.estate](https://guthmann.estate/en/market-intelligence/) plus the GUTHMANN listings — 36 tools across six groups, at the same granularity as the website. Berlin's spatial hierarchy: 12 boroughs (Bezirke), 96 districts (Ortsteile), 542 neighborhoods (LOR Planungsräume).

**Property search** — the broker's active inventory, every result with its exposé URL:

| Tool | What it returns |
|---|---|
| `listings` | Active listings, filterable by segment, borough/district, price, rooms, area |
| `listing_details` | One listing in detail: prices, costs, energy certificate, texts, images, contact |

**Berlin market data** — granular transaction and offer aggregates:

| Tool | What it returns |
|---|---|
| `market_berlin_apartments` | Flats: transaction prices, offer prices, offer rents, counts, deltas — down to neighborhood level |
| `market_berlin_apartment_buildings` | Apartment buildings: prices, multiples, transaction volumes |
| `market_germany_residential` | Germany-wide residential price and transaction indices |
| `market_germany_apartment_buildings` | Germany-wide apartment-building price index |

**Areas and zoning:**

| Tool | What it returns |
|---|---|
| `berlin_boroughs` / `berlin_borough_details` | The 12 boroughs (Bezirke) |
| `berlin_districts` / `berlin_district_details` | The 96 districts (Ortsteile) |
| `berlin_neighborhoods` / `berlin_neighborhood_search` / `berlin_neighborhood_details` | LOR neighborhoods (Planungsräume) |
| `berlin_conservation_areas` / `berlin_conservation_area_details` | Social conservation areas (Milieuschutz) |

**Socio-demographics** (12 tools, `socio_berlin_*`) — population, age groups, origin, migration, census data on buildings, households, dwellings and rents, construction activity.

**Macro indicators** (9 tools, `macro_*`) — ECB policy rates, Bund yields, mortgage lending, construction prices, inflation (HICP), GDP, labor market.

**Metadata** — `field_metadata` explains every response field: labels, units, descriptions and data sources, in German and English.

Responses are JSON with German field names (mirroring the underlying data); `field_metadata` translates them. Prose fields (listing texts, exposé URLs) follow the `locale` parameter — default `en`.

## About

[GUTHMANN®](https://guthmann.estate) is a Berlin real estate broker. Market Intelligence is our public research area — this server is its machine-readable counterpart.

The server implementation lives in a private monorepo; this repository is the public home of the service: documentation, endpoint and issue tracker.
