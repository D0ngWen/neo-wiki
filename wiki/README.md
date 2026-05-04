# Neo Wiki

A personal knowledge base built with the LLM Wiki pattern, using Trae IDE and Trae Agent.

## Quick Start

1. **Add sources**: Drop articles, papers, or notes into `../raw/`
2. **Ask Trae Agent to ingest**: "Please process the new source in raw/[filename]"
3. **Ask questions**: "What do I know about X?"
4. **Periodically lint**: "Please health-check the wiki"

## Directory Structure

```
neo_wiki/
├── AGENTS.md          # Schema for Trae Agent (primary config)
├── raw/               # Your source documents (immutable)
│   └── llm-wiki.md    # Original pattern description
└── wiki/              # LLM-generated wiki pages
    ├── README.md      # This file
    ├── index.md       # Content catalog
    └── log.md         # Operation history
```

## How It Works

- **Trae IDE**: Your workspace for exploring the wiki, following links, reading pages
- **Trae Agent**: The "programmer" that writes and maintains all wiki files
- **Wiki**: The "codebase" - the persistent, compounding knowledge artifact

Trae Agent reads your sources and builds a persistent, interlinked wiki. Knowledge compounds over time — no need to re-derive answers. Good answers can be filed back into the wiki for future reference.

## Key Files

- **[AGENTS.md](../AGENTS.md)**: The primary schema that tells Trae Agent how to maintain the wiki
- **[index.md](./index.md)**: Catalog of all wiki pages — start here to explore
- **[log.md](./log.md)**: Chronological record of all operations

## Roles

- **You**: Curate sources, direct analysis, ask good questions
- **Trae Agent**: Summarizing, cross-referencing, filing, bookkeeping
