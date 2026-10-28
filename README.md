# Repolex Knowledge Graph of explosion/prodigy-evaluate

RDF knowledge graph data for [explosion/prodigy-evaluate](https://github.com/explosion/prodigy-evaluate), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/prodigy-evaluate
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f7408b8be97863c4bcf6245d2fbb9e3d7293c3fa
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f7408b8be97863c4bcf6245d2fbb9e3d7293c3fa
│           └── chunk-001.nq.gz
├── blob
│   ├── 176016ab7df28d24d50781a88d117e763e122904.nq.gz
│   ├── 4817ad718922b3e11a72d9db77be25c154ae4b97.nq.gz
│   ├── 5852b7a743dc4cc91efde9274a41500c117a0bf3.nq.gz
│   ├── 60722de934722d06a447633fcaa42bf269ca7ab4.nq.gz
│   ├── 8640bfdb8dd12b641e346b5bc0d0824011a8463b.nq.gz
│   ├── 9318dc888d5a5cf458a7ab97e7af92379567f85f.nq.gz
│   ├── 9398e3fcfbfa18b5356e466c67eeaebe664254c5.nq.gz
│   ├── b4ebf77f0ba40523270c8fd7f8a8121a8a29595b.nq.gz
│   ├── bf220e0700d6ba26d3ab89d87674118993ed21e8.nq.gz
│   ├── f037108b68767269598b56dce05bb8dbaaa26025.nq.gz
│   ├── f1b2847b7c532d770b67cdfca67f4c683cef8c4d.nq.gz
│   └── fad6cab758fd62e40cfc75e286af6ea46687f7ee.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f7408b8be97863c4bcf6245d2fbb9e3d7293c3fa.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 19 files
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

[explosion/prodigy-evaluate](https://github.com/explosion/prodigy-evaluate)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
