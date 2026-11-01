# SEO Data MCP: live SEO data for AI agents

A remote MCP server (Streamable HTTP) that gives Claude, Cursor, VS Code and other MCP clients live SEO data: Google keyword volume and difficulty, live SERP rank checks, domain traffic, ranked keywords, backlinks, Google Trends and YouTube stats. It runs as the [SEO Data MCP Server](https://apify.com/steady-scrape/seo-data-mcp-server) Actor on Apify, in Standby mode.

**Endpoint:**

```
https://steady-scrape-1--seo-data-mcp-server.apify.actor/mcp
```

Auth: `Authorization: Bearer <APIFY_TOKEN>` ([get a token](https://console.apify.com/settings/integrations)). Pay per successful call, billed to your Apify account; failed calls are free.

## Tools

| Tool | What it does |
|---|---|
| `keyword_metrics` | Google search volume, CPC, competition and difficulty for a list of keywords |
| `google_serp` | Live Google results for a query, with your domain's rank |
| `domain_overview` | Estimated traffic and rank for a domain |
| `ranked_keywords` | Keywords a domain ranks for |
| `backlinks` | Backlinks and referring domains |
| `google_trends` | Interest over time for terms |
| `youtube_search` | YouTube search results with stats |
| `youtube_video` | Stats for a YouTube video |

## Client setup

**Cursor / Windsurf** (`mcpServers`):

```json
{
  "mcpServers": {
    "seo-data": {
      "url": "https://steady-scrape-1--seo-data-mcp-server.apify.actor/mcp",
      "headers": { "Authorization": "Bearer <YOUR_APIFY_TOKEN>" }
    }
  }
}
```

**Claude Code:**

```bash
claude mcp add --transport http seo-data "https://steady-scrape-1--seo-data-mcp-server.apify.actor/mcp" \
  --header "Authorization: Bearer $APIFY_TOKEN"
```

## Registry files

- [`server.json`](server.json): official MCP Registry entry (`io.github.steadyscrape/seo-data-mcp`), published by the GitHub Actions workflow in `.github/workflows/`
- [`glama.json`](glama.json): Glama maintainer claim

More SteadyScrape examples: [steadyscrape-examples](https://github.com/steadyscrape/steadyscrape-examples).

## Acceptable use

You may not use results from this service to build or operate a search engine, or any product or service that competes with or harms the business of search engine providers.

— SteadyScrape

## License

MIT. This repo contains configuration and docs only; the tools are paid services on Apify.
