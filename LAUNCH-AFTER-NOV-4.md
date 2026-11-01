# SEO Data MCP: directory entries to do after Nov 4, 2026 (NOT done yet)

Prepared 2026-10-28. Do nothing until the Actor is public:
`curl -s https://api.apify.com/v2/acts/steady-scrape~seo-data-mcp-server | jq .data.isPublic` must print `true`.
Also re-check tool names in the README against the published Actor, and run `tools/list` against the endpoint with a token.

1. **GitHub repo:** `cd pending/seo-data-mcp && git init -b main && git config user.name SteadyScrape && git config user.email bluecoast.hq+github@mail.grokbot.com && git add -A && git commit -m "Initial commit"`, then
   `gh repo create steadyscrape/seo-data-mcp --public --source . --push --description "Remote MCP server with live SEO data for AI agents: keyword volume, SERP ranks, backlinks, domain traffic, Google Trends, YouTube." --homepage https://apify.com/steady-scrape/seo-data-mcp-server`
   Topics: `gh repo edit steadyscrape/seo-data-mcp --add-topic mcp,mcp-server,remote-mcp,model-context-protocol,seo,keyword-research,backlinks,serp,apify,ai-agents`
2. **Official MCP Registry:** `gh workflow run publish-mcp-registry.yml -R steadyscrape/seo-data-mcp` (GitHub OIDC, headless; same workflow that published jobs-data-mcp). Check: `curl "https://registry.modelcontextprotocol.io/v0.1/servers?search=seo-data-mcp"`.
3. **Glama:** `glama.json` is in the repo; Glama imports from the registry. If it's not listed after a few days, sign in at glama.ai with GitHub (steadyscrape) → Add server → repo URL.
4. **Smithery:** after `smithery auth login` (browser), run
   `npx @smithery/cli mcp publish "https://steady-scrape-1--seo-data-mcp-server.apify.actor/mcp" -n steadyscrape/seo-data`
   Note: Smithery wants OAuth for servers that need auth; this endpoint uses a Bearer token only, so Smithery may not be able to scan it. Fallback is the Apify gateway URL `https://mcp.apify.com/?tools=steady-scrape/seo-data-mcp-server` (OAuth), but don't publish that same URL to the MCP Registry under a second name.
5. **steadyscrape profile README:** add a row for SEO Data MCP Server.
6. **awesome-remote-mcp-servers:** skip (list requires OAuth 2.0 and an official server with a track record).
