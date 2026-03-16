# Design: Obsidian Vault Search MCP Server

## Architecture
```
Obsidian Vault (.md files)
    ↓
vault_scanner → note_parser → indexer (SQLite + FTS5)
    ↓                              ↓
search_engine ← query_parser    graph (backlinks, authority)
    ↓                              ↓
ranker (6-stage pipeline)
    ↓
MCP server → tools → handlers → JSON-RPC responses
```

## Module Breakdown

### Core Layer
- **vault_scanner**: Walks vault directory, filters .md files, excludes .obsidian/, .trash/
- **note_parser**: Extracts frontmatter, wikilinks, tags, tasks, heading chunks
- **indexer**: SQLite schema, FTS5 virtual tables, CRUD operations
- **search_engine**: FTS5 retrieval, LIKE fallback, operator filtering
- **graph**: Link graph, backlinks, forward links, authority scoring, BFS traversal
- **ranker**: 6-stage ranking pipeline (BM25 → operators → graph → authority → recency → semantic)

### MCP Layer
- **server**: Stdio protocol, initialize/tools-list/tools-call dispatch
- **tools**: Tool schema definitions for all 11 tools
- **handlers**: Per-tool handler functions routing to core modules

### Utility Layer
- **json_helpers**: JSON construction without external library
- **query_parser**: Operator extraction from search queries

## Data Model
5 tables: notes, chunks, links, tasks + 2 FTS5 virtual tables (note_fts, chunk_fts)

## Ranking Pipeline
1. Lexical retrieval (FTS5 BM25)
2. Operator filtering (tag:, path:, title:, etc.)
3. Graph reranking (backlink count boost)
4. Authority score (iterative backlink-weighted)
5. Recency boost (linear decay over 90 days)
6. Semantic rerank (deferred to future version)

## Error Handling
- FTS5 unavailable: fallback to LIKE queries with warning
- Missing vault path: server starts but returns empty results
- Malformed frontmatter: skip fields, use heading as title fallback
