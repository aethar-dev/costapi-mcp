# CostAPI MCP Server

[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-blue)](https://modelcontextprotocol.io)

Cost of living and price index data for 190+ countries. Query CPI time series, compare purchasing power parity across countries, explore US metro area prices, and analyze Eurostat HICP data. Data sourced from BLS, Eurostat, World Bank, OECD, and BEA.

## Installation

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "aethar-cost-of-living": {
      "url": "https://col.wageapi.com/api/mcp",
      "headers": {
        "X-API-Key": "your_api_key_here"
      }
    }
  }
}
```

### Claude Code

Add to `.claude/settings.json` in your project root:

```json
{
  "mcpServers": {
    "aethar-cost-of-living": {
      "url": "https://col.wageapi.com/api/mcp",
      "headers": {
        "X-API-Key": "your_api_key_here"
      }
    }
  }
}
```

### Cursor

Open Settings > MCP Servers > Add Server:

```json
{
  "aethar-cost-of-living": {
    "url": "https://col.wageapi.com/api/mcp",
    "headers": {
      "X-API-Key": "your_api_key_here"
    }
  }
}
```

### VS Code (Copilot MCP)

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "aethar-cost-of-living": {
      "url": "https://col.wageapi.com/api/mcp",
      "headers": {
        "X-API-Key": "your_api_key_here"
      }
    }
  }
}
```

## Available Tools

### CPI Tools

| Tool | Description |
|------|-------------|
| `list_countries_v1_cpi_countries_get` | List all countries with CPI data (paginated). |
| `get_country_v1_cpi_countries__country_code__get` | Get CPI data for a specific country with category breakdown. |
| `get_country_history_v1_cpi_countries__country_code__history_get` | Get CPI time series for a country with date range and category filters. |
| `list_categories_v1_cpi_categories_get` | List available CPI category codes. |
| `compare_countries_v1_cpi_compare_get` | Compare CPI across 2-20 countries. |

### PPP Tools

| Tool | Description |
|------|-------------|
| `list_countries_v1_ppp_countries_get` | List all countries with PPP data. |
| `get_country_v1_ppp_countries__country_code__get` | Get PPP conversion factors for a country. |
| `compare_countries_v1_ppp_compare_get` | Compare PPP across multiple countries. |

### Prices Tools

| Tool | Description |
|------|-------------|
| `list_metro_areas_v1_prices_us_metro_areas_get` | List US metro areas with price data. |
| `get_metro_area_v1_prices_us_metro_areas__area_code__get` | Get price data for a US metro area. |
| `get_item_v1_prices_us_items__item_code__get` | Get item prices across US metro areas. |

### Intelligence Tools (Semantic)

| Tool | Description |
|------|-------------|
| `compare_cost_of_living_v1_compare_cost_of_living_get` | Compare cost of living between two locations (natural language). |
| `cheapest_cities_v1_cheapest_cities_get` | Find cheapest countries in a region. |
| `purchasing_power_v1_purchasing_power_get` | Calculate purchasing power of a salary in another location. |
| `cost_breakdown_v1_cost_breakdown_get` | Get detailed cost breakdown for a location vs baseline. |

## Example Prompts

These prompts work directly with Claude, Cursor, or any MCP-compatible AI client:

- "Compare the cost of living between Berlin and Warsaw for someone earning EUR 75,000"
- "How much more expensive is Tokyo than Seoul?"
- "What are the 10 cheapest EU countries to live in?"
- "What salary do I need in San Francisco to match my $80K lifestyle in Austin?"
- "How far does a $100K salary go in Germany vs the US?"
- "Show me the CPI trend for the US over the last 3 years"
- "Compare grocery prices across New York, Chicago, and Los Angeles metro areas"
- "Calculate the purchasing power of JPY 8,000,000 if I move from Tokyo to Bangkok"

## Authentication

All tools require an API key. Get one at [RapidAPI](https://rapidapi.com/AETHAR/api/costapi) or [wageapi.com](https://wageapi.com).

Pass the key via the `X-API-Key` header in your MCP server configuration (see installation instructions above).

## Links

- [RapidAPI Listing](https://rapidapi.com/AETHAR/api/costapi)
- [Demo Dashboard](https://col.wageapi.com/demo)
- [Workforce Data Suite](https://wageapi.com)

## Part of Workforce Data Suite

CostAPI works alongside [WageAPI](https://github.com/aethar-dev/wageapi-mcp) (US and EU salary benchmarking for 1,400+ occupations). Both are available as MCP servers. Configure both for comprehensive salary + cost-of-living analysis.

## License

The MCP server endpoint is provided as part of CostAPI. Source code is proprietary.
