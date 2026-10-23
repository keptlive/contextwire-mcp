# ContextWire MCP Server

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![MCP](https://img.shields.io/badge/MCP-Compatible-green.svg)](https://modelcontextprotocol.io/)
[![SimpleQA](https://img.shields.io/badge/SimpleQA-94.3%25-brightgreen.svg)](https://contextwire.dev/compare.html)
[![Free Tier](https://img.shields.io/badge/Free_Tier-1000_queries%2Fmo-blue.svg)](https://contextwire.dev)

A [Model Context Protocol](https://modelcontextprotocol.io/) server that gives AI agents access to web search across **105 engines**, academic research, content extraction, and more.

**94.3% accuracy on [SimpleQA](https://openai.com/index/introducing-simpleqa/) benchmark.**

## Quick Setup

Add to your MCP client config (Claude Desktop, Claude Code, Cursor, etc.):

```json
{
  "mcpServers": {
    "contextwire": {
      "url": "https://contextwire.dev/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

No local server needed — it's a hosted MCP endpoint.

## Tools

| Tool | Description |
|------|-------------|
| `ask` | Ask a factual question → synthesized answer with sources |
| `search` | Web search with selectable search profiles |
| `extract` | Extract clean text/markdown from a URL |
| `research` | Search academic papers (arXiv, PubMed, Semantic Scholar, etc.) |
| `batch_search` | Run multiple searches in parallel |

## Search Profiles

| Profile | Engines | Best for |
|---------|---------|----------|
| `web` | Google, Bing, DDG, Wikipedia | General search |
| `news` | Google News, Bing News | Current events |
| `academic` | arXiv, PubMed, Semantic Scholar | Research papers |
| `code` | GitHub, StackOverflow | Programming |
| `devnews` | Hacker News, Lobsters, Reddit | Developer news |
| `finance` | Yahoo Finance, market data | Financial data |
| `repos` | GitHub, GitLab | Code repositories |
| `packages` | npm, PyPI, crates.io | Package search |
| `security` | CVE databases | Security advisories |
| `social` | Reddit, Twitter | Social media |
| `reference` | Wikipedia, Wiktionary | Reference material |
| `images` | Google Images, Bing Images | Image search |
| `videos` | YouTube, Vimeo | Video search |
| `all` | All configured engines | Maximum coverage |

These names come from the API reference and are not an exhaustive live inventory.
Use authenticated `GET /api/profiles` for current profiles and engine configurations.

## API Examples

### Ask a question
```bash
curl --get "https://contextwire.dev/api/ask" \
  -H "Authorization: Bearer YOUR_KEY" \
  --data-urlencode "q=Who invented the transistor?"
```

### Search with profiles
```bash
curl "https://contextwire.dev/api/search?q=rust+async+tutorial&profile=code" \
  -H "Authorization: Bearer YOUR_KEY"
```

### Extract a page
```bash
curl "https://contextwire.dev/api/extract?url=https://example.com&format=markdown" \
  -H "Authorization: Bearer YOUR_KEY"
```

## Free Tier

- **1,000 queries/month** — no credit card required
- **BYOK supported** — bring your own LLM key to save credits
- LLM availability and charges depend on the selected model and provider.

Get your API key at **[contextwire.dev](https://contextwire.dev)**.

## Node.js usage

The advertised `@contextwire/sdk` package is not currently available on the public npm
registry, and its repository is private. Use the HTTP API directly:

```js
const url = new URL('https://contextwire.dev/api/ask');
url.searchParams.set('q', 'Who invented the transistor?');
const response = await fetch(url, {
  headers: { Authorization: `Bearer ${process.env.CONTEXTWIRE_API_KEY}` }
});
if (!response.ok) throw new Error(`ContextWire HTTP ${response.status}`);
console.log(await response.json());
```

Requires Node.js with built-in `fetch` and a ContextWire API key.

## Links

- **Website**: [contextwire.dev](https://contextwire.dev)
- **API Docs**: [contextwire.dev/docs](https://contextwire.dev/docs.html)
- **Quickstart**: [contextwire.dev/quickstart](https://contextwire.dev/quickstart.html)
- **Playground**: [contextwire.dev/playground](https://contextwire.dev/playground.html)
- **Compare**: [contextwire.dev/compare](https://contextwire.dev/compare.html)
- **Status**: [contextwire.dev/status](https://contextwire.dev/status.html)

## License

MIT
