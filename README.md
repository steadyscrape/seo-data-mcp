# SEO Data MCP: live SEO data for AI agents

A remote MCP server (Streamable HTTP) that gives Claude, Cursor, VS Code and other MCP clients live SEO data: Google keyword volume and difficulty, live SERP rank checks, domain traffic, ranked keywords, backlinks, Google Trends and YouTube stats. It is hosted on the [SteadyScrape MCP gateway](https://mcp.steadyscrape.dev/seo). Tools run in your own Apify account.

**Endpoint:**

```
https://mcp.steadyscrape.dev/seo/mcp
```

Auth: clients that support MCP OAuth (Claude.ai, VS Code, Cursor) open an Apify sign-in the first time, or send `Authorization: Bearer <APIFY_TOKEN>` ([get a token](https://console.apify.com/settings/integrations)). Pay per successful call, billed to your Apify account.

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
      "url": "https://mcp.steadyscrape.dev/seo/mcp"
    }
  }
}
```

**Claude Code:**

```bash
claude mcp add --transport http seo-data "https://mcp.steadyscrape.dev/seo/mcp"
```

## Registry files

- [`server.json`](server.json): official MCP Registry entry (`io.github.steadyscrape/seo-data-mcp`), published by the GitHub Actions workflow in `.github/workflows/`
- [`glama.json`](glama.json): Glama maintainer claim
- Glama listing: [glama.ai/mcp/connectors/io.github.steadyscrape/seo-data-mcp](https://glama.ai/mcp/connectors/io.github.steadyscrape/seo-data-mcp)

More SteadyScrape examples: [steadyscrape-examples](https://github.com/steadyscrape/steadyscrape-examples).

## Acceptable use

You may not use results from this service to build or operate a search engine, or any product or service that competes with or harms the business of search engine providers.

— SteadyScrape

## License

MIT. This repo contains configuration and docs only; the tools are paid services on Apify.
