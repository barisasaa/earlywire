# Earlywire — Marketing & Growth Intelligence (MCP)

**Your AI assistant's web search reads whatever ranks. Earlywire reads what practitioners actually say.**

A free [MCP](https://modelcontextprotocol.io) server that gives Claude (and other AI assistants)
current **marketing, growth, SEO, paid-media & measurement** intelligence from **120+ curated
practitioner sources** — read daily, judged & scored 0–10 by an editor model, each item with a
**citable own-words summary**, always linked to source.

- **Endpoint:** `https://earlywire.barisasa.com/mcp` · free, no key, 30 req/min
- **Site / one-page setup:** https://earlywire.barisasa.com/setup
- In the official [MCP Registry](https://registry.modelcontextprotocol.io) as `com.barisasa.earlywire/wire`

## Why

Generic web search amplifies whatever is SEO-optimized — content farms, vendor fluff. Earlywire
subscribes to trusted practitioner sources (newsletters, vendor changelogs, practitioner feeds),
reads them every morning, drops the noise (only score ≥7 is served), and hands your assistant the
keepers with an own-words summary it can cite — alongside web search, not instead of it.

## Tools

| Tool | What it does |
|---|---|
| `earlywire_search` | Full-text search of the wire — your first stop for any marketing question |
| `earlywire_topic_pulse` | What practitioners are saying about a topic: volume, sources, score spread, top takes |
| `earlywire_whats_new` | Newest items (optionally by category) |
| `earlywire_trending` | Topics rising this window vs the last |
| `earlywire_get_item` | One item's summary + excerpt + source link |
| `earlywire_coverage` | What the wire does and doesn't cover |

## Install

### 1. The connector (the data)

**claude.ai / Claude Desktop:** Settings → **Connectors → Add custom connector** → paste
`https://earlywire.barisasa.com/mcp`

**Claude Code:**
```bash
claude mcp add --transport http earlywire https://earlywire.barisasa.com/mcp
```

### 2. The skill (so it actually fires)

The skill tells Claude to consult Earlywire — alongside web search — for marketing questions, so it
gets used instead of defaulting straight to the open web.

**claude.ai / Claude Desktop (web is upload-only):** download
[`earlywire-marketing.zip`](https://earlywire.barisasa.com/skill) → Settings → **Skills → Create
skill** → upload it. (Requires code execution enabled.)

**Claude Code — pick one:**
```bash
# plugin marketplace — installs the skill AND the connector in one step
/plugin marketplace add barisasaa/earlywire
/plugin install earlywire-marketing

# or clone / curl the skill into place
curl -L https://earlywire.barisasa.com/skill -o ew.zip \
  && unzip -o ew.zip -d ~/.claude/skills/ && rm ew.zip
```

> **Tip:** On a busy account Claude defers connector tools by default. The skill fixes that — or set
> **Settings → Tool access → Always available** so Earlywire is always loaded.

## Notes

- **Free**, no API key, 30 requests/minute per IP.
- **Snippet posture:** the wire serves an own-words summary + a short excerpt, **always linked to the
  source**. Full article text never leaves the publisher; copyright stays with each publisher.
- Items are scored by an editor model and can be wrong — verify anything that matters at the linked source.

## Author

[Baris Asa](https://www.linkedin.com/in/barisasa/) · marketing analytics & tracking.
Source removal requests / questions: see https://earlywire.barisasa.com/privacy

## License

MIT — see [LICENSE](LICENSE).
