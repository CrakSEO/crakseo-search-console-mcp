---
name: search-console
description: Report on the user's own Google Search Console (GSC) and Bing Webmaster Tools data, such as search analytics, keywords and search rankings, with CrakSEO's free Search Console MCP. Use when the user asks which queries or pages bring clicks, why a page is not indexed in Google, to list or resubmit sitemaps, or for Bing traffic, crawl issues and URL submission quota.
---

# Search Console and Bing Webmaster Tools

## When to use

- "Which Google search queries bring clicks to my website?"
- "Why is my page not indexed in Google?"
- "Check Bing traffic, crawl issues and my sitemap."

Every tool on this server is free. It only reads sites the user has verified and connected.

## Steps

1. Call `list_search_console_properties` first. If Google or Bing is not connected, give the user the links in its `connect` field and stop until they connect.
2. Use the exact property names it returns in the other tools.
3. Clicks, impressions, CTR and position: `get_search_console_performance`. Start with the last 28 days unless the user asks for another range.
4. Indexing questions about one page: `inspect_url_in_google`. Explain the coverage state it returns, such as "Crawled - currently not indexed", and say what the user can change.
5. Sitemaps: `list_sitemaps` reads; `submit_sitemap` writes. Ask the user to confirm before calling `submit_sitemap`.
6. Bing: `get_bing_webmaster_stats`, `get_bing_crawl_issues`, `get_bing_url_submission_quota`.

## Rules

- Never promise that a page will be indexed or ranked. Google decides.
- Report numbers as Search Console or Bing returns them; they are sampled and delayed by the provider.
- Do not ask for or store passwords or API keys in chat. Authentication happens through the client's OAuth sign-in.
