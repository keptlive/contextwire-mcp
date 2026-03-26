# ContextWire MCP Server

A [Model Context Protocol](https://modelcontextprotocol.io/) server that gives AI agents access to web search across 105 engines, academic research, content extraction, and more.

**94.3% accuracy on [SimpleQA](https://openai.com/index/introducing-simpleqa/) benchmark.**

## Quick Setup

Add to your MCP client config (Claude Desktop, Claude Code, etc.):

```json
{
  "mcpServers": {
    "contextwire": {
      "url": "https://contextwire.dev/mcp"
    }
  }
}
```

That's it. No local server to run — it's a hosted MCP endpoint.

## Tools

| Tool | Description |
|------|-------------|
| `ask` | Ask a factual question → synthesized answer with sources |
| `search` | Web search across 105 engines with 14 search profiles |
| `extract` | Extract clean text/markdown from any URL |
| `research` | Search academic papers (arXiv, PubMed, Semantic Scholar, etc.) |
| `batch_search` | Run multiple searches in parallel |

## Examples

### Ask a question
```
> ask("What is the current population of Tokyo?")

Tokyo's population is approximately 13.96 million (2024).
Sources: [Wikipedia, WorldPopulationReview]
```

### Search with profiles
```
> search("rust async tutorial", profile: "code")

1. Asynchronous Programming in Rust - rust-lang.org
2. Tokio Tutorial - tokio.rs
3. A practical guide to async Rust - blog.logrocket.com
...
```

### Extract a page
```
> extract("https://example.com/article", format: "markdown")

# Article Title
Article content in clean markdown...
```

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
| `all` | All 105 engines | Maximum coverage |

## Free Tier

- 1,000 queries/month
- No credit card required
- BYOK (Bring Your Own Key) supported — use your own LLM key to save credits

Get your API key at [contextwire.dev](https://contextwire.dev).

## Node.js SDK

```bash
npm install @contextwire/sdk
```

```js
import { ContextWire } from '@contextwire/sdk';

const cw = new ContextWire('YOUR_API_KEY');

const answer = await cw.ask('Who invented the transistor?');
console.log(answer.answer);
// "The transistor was invented by John Bardeen, Walter Brattain, and William Shockley at Bell Labs in 1947."
```

## Links

- **Website**: [contextwire.dev](https://contextwire.dev)
- **API Docs**: [contextwire.dev/docs](https://contextwire.dev/docs.html)
- **Quickstart**: [contextwire.dev/quickstart](https://contextwire.dev/quickstart.html)
- **Playground**: [contextwire.dev/playground](https://contextwire.dev/playground.html)
- **Status**: [contextwire.dev/status](https://contextwire.dev/status.html)

## License

MIT
