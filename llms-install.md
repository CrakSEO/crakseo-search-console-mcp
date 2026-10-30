# CrakSEO Search Console MCP: installation guide for Cline

Remote MCP server hosted by CrakSEO. Nothing to build, clone or run locally. All tools are free.

| Server name | URL |
| --- | --- |
| `crakseo-search-console` | `https://crakseo.com/mcp/search-console` |

## Steps

1. Ask the user for a CrakSEO API key. If they don't have one, tell them to sign up and create a key at https://crakseo.com/app/settings/keys. Don't proceed with a made-up key.
2. Open the Cline MCP settings file (`cline_mcp_settings.json`).
3. Add this entry inside `mcpServers`, replacing `YOUR_CRAKSEO_API_KEY` with the user's key. Keep any existing servers.

   ```json
   {
     "mcpServers": {
       "crakseo-search-console": {
         "type": "streamableHttp",
         "url": "https://crakseo.com/mcp/search-console",
         "headers": { "Authorization": "Bearer YOUR_CRAKSEO_API_KEY" },
         "disabled": false
       }
     }
   }
   ```

4. Save the file and wait for Cline to reload the servers.
5. Verify by calling `list_search_console_properties` with `{}`. If Google or Bing isn't connected yet, the lists are empty; give the user the links in `connect` from the result.

## Rules after installation

- Ask the user before calling `submit_sitemap`; it writes to Google and Bing.
- Never promise indexing or rankings.

Docs: https://docs.crakseo.com/quickstarts/cline
