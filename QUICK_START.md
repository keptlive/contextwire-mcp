# Quick Start — Add Web Search to Claude Code in 30 Seconds

## 1. Get a free API key

Visit [contextwire.dev](https://contextwire.dev) and sign up. Instant key, no credit card.

## 2. Add to your MCP config

**Claude Code** (`~/.claude/settings.json`):
```json
{
  "mcpServers": {
    "contextwire": {
      "type": "streamable-http",
      "url": "https://contextwire.dev/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

**Cursor** (`~/.cursor/mcp.json`):
```json
{
  "mcpServers": {
    "contextwire": {
      "type": "streamable-http", 
      "url": "https://contextwire.dev/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

## 3. Restart your editor

Run `/mcp` in Claude Code to verify. You should see 5 tools:

| Tool | What it does |
|------|-------------|
| `ask` | Natural-language question → sourced answer |
| `search` | Web search across 105 engines |
| `extract` | Pull full content from any URL |
| `research` | Multi-step deep research with citations |
| `batch_search` | Multiple searches in parallel |

## 4. Try it

Just ask Claude naturally:
- "Search for the latest Next.js 15 migration guide"
- "Research how to set up Postgres connection pooling"
- "Extract the README from github.com/some/repo"

## Free Tier

- 1,000 queries/month
- All 5 tools included
- No credit card required
- BYOK option: bring your own OpenRouter key for 50% savings

## Links

- [Full API Docs](https://contextwire.dev/docs.html)
- [Playground](https://contextwire.dev/playground.html)
- [Tutorial: Add Web Search to Claude Code](https://helloandy.net/claude-code-web-search/)
