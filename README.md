# Repolex Knowledge Graph of pydantic/logfire-lsp

RDF knowledge graph data for [pydantic/logfire-lsp](https://github.com/pydantic/logfire-lsp), parsed by [repolex](https://repolex.ai).

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
rlex download pydantic/logfire-lsp
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c6564bd4e6a3f5d616957f2d549cb1c591160a52
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c6564bd4e6a3f5d616957f2d549cb1c591160a52
│           └── chunk-001.nq.gz
├── blob
│   ├── 013c9d836fc567b5410d75f765f6559c5c359cbc.nq.gz
│   ├── 0ac860dff27d7bdaa04741fc5134c1587b6f8ebe.nq.gz
│   ├── 0c64d0e55c1a56a095481f014a84d44a429511bd.nq.gz
│   ├── 0da3600d61a1df7aa2c4b2bb682880f50db83e57.nq.gz
│   ├── 102a47308863bb64db8a6780d6d3c08984081f5a.nq.gz
│   ├── 13d1f14e22330517ef4f27b04d7ba974ade0508e.nq.gz
│   ├── 81f0fdeccf66f1b74184b96bd53b64be1b903aae.nq.gz
│   ├── 96f2bbb3b547e68c7ef14ead4c553d453b5a3a25.nq.gz
│   ├── 9c647868046850545f7d9b4ad8acbe4e47e030c8.nq.gz
│   ├── cc54aafd530f641bbb09d5a6859f3666251882af.nq.gz
│   ├── d342fc8cb9a5494b9f56726dcdafb14b69e7fe90.nq.gz
│   ├── db195fcbb9524f3710ae99a2e388e48877dc17e5.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e825ad51621c5e34d370ba64f13f6854d89456a6.nq.gz
│   └── fe14e107269215b91e6d2a783d76616e34d82b3d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c6564bd4e6a3f5d616957f2d549cb1c591160a52.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 22 files
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

[pydantic/logfire-lsp](https://github.com/pydantic/logfire-lsp)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
