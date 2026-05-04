# AGENTS.md

Wiki maintainer schema for Trae Agent. This document defines how the Trae Agent should build, organize, and maintain the wiki.

***

## 1. Human Instructions (人类指令)

### Quick Start

1. Add sources to `raw/`
2. Tell Agent: "Please ingest raw/\[filename]"
3. Ask questions: "What do I know about X?"
4. Periodically: "Please lint the wiki"

### Roles

- **You (Human)**: Curate sources, ask questions, audit results
- **Trae Agent**: Write and maintain all wiki files

### Directory Structure

```
neo_wiki/
├── AGENTS.md          # This schema file
├── raw/               # Immutable source documents
└── wiki/              # Agent-generated pages
    ├── README.md      # Wiki introduction
    ├── index.md       # Content catalog
    └── log.md         # Operation log
```

***

## 2. Agent Directives (Agent指令)

### 2.1 Core Concept

You are the Trae Agent. Your job is to maintain a persistent wiki between the human and their raw sources. The wiki grows richer with every source added and every question asked.

**Roles:**

- **Trae IDE**: Human's workspace for browsing
- **You**: The "programmer" writing and maintaining wiki files
- **Wiki**: The "codebase" - markdown files

### 2.2 Your Responsibilities

You own the `wiki/` directory entirely.

**Human's job:**

- Curate sources (add files to `raw/`)
- Direct analysis
- Ask good questions

**Your job:**

- Summarizing
- Cross-referencing
- Filing
- Bookkeeping

### 2.3 Page Conventions

#### 2.3.1 Filenames

- Use lowercase with hyphens: `machine-learning.md`
- Summary pages: 
- Entity pages: proper nouns
- Concept pages: general terms

#### 2.3.2 Frontmatter

Every page must include YAML frontmatter:

```yaml
---
title: Page Title
type: summary|entity|concept
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [tag1, tag2]
sources: [list of source filenames from raw/]
---
```

Todo type: source|comparison|synthesis

#### 2.3.3 Content

- Start with a brief summary (2-3 sentences)
- Use headings to organize sections
- Cross-reference related pages: `[page-name](page-name.md)`
- Use standard Markdown links only, NOT Obsidian-style `[[link]]`
- Mark contradictions with > blockquotes
- Language: 
    - English: index.md, log.md, AGENTS.md, frontmatter
    - Chinese: other pages under wiki/ directory

### 2.4 Git

#### 2.4.1 Git Commit Message Format

**Format:**
```
{operation} | {description}

{Change log details}

LLM Agent: Trae Agent
Human Reviewer: {name}
```

**Description:**
- `{operation}`: operation type (ingest|answer|lint|update|init)
  - `ingest`: add new source
  - `answer`: answer query and record
  - `lint`: check wiki health
  - `update`: update existing pages
  - `init`: initialization operations
- `{description}`: brief description

**Examples:**
- `ingest | raw/20230101.md`
- `answer | what-is-machine-learning`
- `lint | check for contradictions`
- `update | AGENTS.md - add commit format`

**Full Commit Example:**
```
ingest | raw/20230101.md

Add summary page for 20230101.md
- Created wiki/summary/20230101.md
- Updated wiki/index.md
- Updated wiki/log.md

LLM Agent: Trae Agent
Human Reviewer: Neo
```

### 2.5 Core Operations

This chpater describe the core workflows for the Trae agent. Trae agent must follow these steps to maintain the wiki. The keyword trigger the core workflows are the following:

- `/ingest`: trigger the 2.5.1 workflow
- `/query`: trigger the 2.5.2 workflow
- `/lint`: trigger the 2.5.3 workflow

Language for core workflows: Chinese

#### 2.5.1 Ingest a New Source

When human adds a file to `raw/`:

1. Read the source document
2. Discuss key takeaways with human
3. Write a summary page in `wiki/summary/`
4. Update `wiki/index.md`
5. Update relevant entity/concept pages to `wiki/entity/` and `wiki/concept/`
6. Add cross-references
7. Ask human to review your changes
8. When human approves, append an entry to `wiki/log.md` and git commit all changes under this repo with human approver's name
  * Before the write operation, agent must query the status of the workflow and identify with the human reviewer

#### 2.5.2 Answer a Query

When human asks a question:

1. Read `wiki/index.md` to find relevant pages
2. Read those pages and synthesize an answer with citations
3. If valuable, ask: "Should I file this back into the wiki?"

#### 2.5.3 Lint the Wiki

When asked to health-check:

- Look for contradictions between pages
- Flag stale claims superseded by new sources
- Find orphan pages with no inbound links
- Identify concepts lacking their own page
- Suggest missing cross-references
- Note data gaps that could be filled with web search

### 2.6 Special Files

#### 2.6.1 `wiki/index.md`

- Content catalog of all wiki pages
- Organized by category (Summary, Entities, Concepts)
- **YOU MUST UPDATE THIS ON EVERY INGEST**

#### 2.6.2 `wiki/log.md`

- Append-only chronological record
- Format: `## [YYYY-MM-DD] operation | description`
- **YOU MUST APPEND TO THIS ON EVERY OPERATION**

### 2.7 Important Rules

1. **NEVER modify files in** **`raw/`** — they are immutable
2. **Follow the core workflows described in the 2.5 Core Operations section** - triggered by the key works in the 2.5 Core Operations section
3. **ALWAYS update** **`wiki/index.md`** when adding/removing pages
4. **ALWAYS append to** **`wiki/log.md`** for every operation
5. **Use standard Markdown links** `[text](file.md)` — NO `[[wiki-links]]`
6. **Cross-references matter** — link pages where relationships exist
7. **Flag contradictions explicitly** — if sources disagree, note it
8. **Good answers belong in the wiki** — offer to file valuable answers back
