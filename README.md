# Free Google Search Console (GSC) & Bing Webmaster Tools by CrakSEO

Free Google Search Console (GSC) for SEO: your own Search Console search analytics, keywords, search rankings, clicks, impressions, URL inspection and Bing Webmaster Tools, as a remote MCP server. Ask your AI agent which queries bring clicks, why a page isn't indexed, or to resubmit a sitemap, and it answers from your verified properties.

This repository holds the client configuration, a Cursor plugin and an agent skill. The server is hosted by CrakSEO at `https://crakseo.com/mcp/search-console`; nothing runs locally and there is no server source here.

| | |
| --- | --- |
| Endpoint | `https://crakseo.com/mcp/search-console` |
| Transport | Streamable HTTP |
| Sign-in | OAuth (recommended), or a CrakSEO API key as a bearer token |
| Scopes | `console:read`, `console:write` |
| Price | Free. Google and Bing quotas apply |
| Registry name | `com.crakseo/search-console` |

## Tools

| Tool | What it does |
| --- | --- |
| `list_search_console_properties` | List your connected Search Console properties and Bing sites, with links to connect either one |
| `get_search_console_performance` | Clicks, impressions, CTR and position, grouped by query, page and/or date |
| `inspect_url_in_google` | Search Console URL inspection: whether the page is indexed, coverage state, robots.txt and fetch status, last crawl time (Google allows 2,000 a day per property) |
| `list_sitemaps` | Sitemaps submitted for a property |
| `submit_sitemap` | Submit a sitemap to Google and Bing (a write; agents should confirm first) |
| `get_bing_webmaster_stats` | Bing query, page and traffic stats |
| `get_bing_crawl_issues` | Bing crawl issues |
| `get_bing_url_submission_quota` | Bing URL submission quota |

## Questions it answers

- Which Google search queries bring clicks to my website?
- Why is my page not indexed in Google?
- How do I check Bing search traffic, crawl issues and sitemap submissions?

## Setup

1. Add the server to your client (below). On first use, sign in to CrakSEO through OAuth; a free account is created if you don't have one.
2. In the CrakSEO dashboard, connect Google Search Console and, optionally, Bing Webmaster Tools with an account that has access to your sites. OAuth to CrakSEO alone does not connect a property.
3. Run a free check: "Use list_search_console_properties to show my connected properties. Do not submit anything."

### Cursor

Install this plugin from the Cursor Marketplace, or add the server to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "crakseo-search-console": { "url": "https://crakseo.com/mcp/search-console" }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http crakseo-search-console https://crakseo.com/mcp/search-console
```

Run `/mcp` to authenticate.

### VS Code

```json
{
  "servers": {
    "crakseo-search-console": { "type": "http", "url": "https://crakseo.com/mcp/search-console" }
  }
}
```

### Codex

```toml
[mcp_servers.crakseo-search-console]
url = "https://crakseo.com/mcp/search-console"
```

Then `codex mcp login crakseo-search-console`.

### Cline

See [`llms-install.md`](llms-install.md).

More clients, including Grok and Gemini CLI: https://docs.crakseo.com/mcp-servers/search-console

## What to expect

- Every tool is free. Once a day per connection, a successful result may include an optional `nextStep` link to CrakSEO's paid Link Network; it never blocks a result and nothing is charged.
- Data comes from Google and Bing for properties you own. Numbers are sampled and delayed by the provider.
- Submitting a sitemap or inspecting a URL does not guarantee indexing or rankings.

## Plugin contents

| Path | Purpose |
| --- | --- |
| `.cursor-plugin/plugin.json` | Cursor plugin manifest |
| `mcp.json` | The one remote server above; no credentials |
| `skills/search-console/SKILL.md` | When and how agents should use the tools |
| `assets/logo.png` | 512x512 CrakSEO logo |
| `llms-install.md` | Install guide for Cline |

## Privacy and support

Tool arguments go to CrakSEO and to Google or Bing to answer the request. Google and Bing access requires your authorization and can be revoked in the dashboard.

- Privacy: https://crakseo.com/privacy
- Terms: https://crakseo.com/terms
- Docs: https://docs.crakseo.com/mcp-servers/search-console
- Support: support@crakseo.com
- Issues: https://github.com/LoganOneal/crakseo-search-console-mcp/issues (never include keys, tokens or private property data)

## License

The files in this repository are MIT-licensed ([LICENSE](LICENSE)). That does not license the hosted CrakSEO service, which is covered by the [CrakSEO terms](https://crakseo.com/terms).
