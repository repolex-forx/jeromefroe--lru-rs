# Repolex Knowledge Graph of jeromefroe/lru-rs

RDF knowledge graph data for [jeromefroe/lru-rs](https://github.com/jeromefroe/lru-rs), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download jeromefroe/lru-rs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 13321a9f96059b2355aa3697c2a1613b16fd83e5
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 13321a9f96059b2355aa3697c2a1613b16fd83e5.nq.gz
│   └── repolex
│       └── 13321a9f96059b2355aa3697c2a1613b16fd83e5
│           └── chunk-001.nq.gz
├── blob
│   ├── 0b3d7a86b1b0ebbdad43d724a3a08b726fa6d4c8.nq.gz
│   ├── 32bce596383a0f01177cffdbb1b95952b3c97022.nq.gz
│   ├── 42497dac55c4a2111664bd1420d37022c612cac6.nq.gz
│   ├── 9cd623b8f0751394040245b079c91d93470b7d16.nq.gz
│   ├── b26e42dabfcba6bc583f1dcc8659bdba08d0de15.nq.gz
│   ├── cf1d4b963fa6ec194f07a62d87d9e513d3a4078f.nq.gz
│   └── fee5c140a18f279575c8cd979b798fcb022a7745.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 13321a9f96059b2355aa3697c2a1613b16fd83e5.nq.gz
├── filetree
│   └── 13321a9f96059b2355aa3697c2a1613b16fd83e5.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 17 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[jeromefroe/lru-rs](https://github.com/jeromefroe/lru-rs)

---
*Parsed on 2026-11-22 by [repolex](https://repolex.ai)*
