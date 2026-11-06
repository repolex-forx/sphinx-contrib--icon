# Repolex Knowledge Graph of sphinx-contrib/icon

RDF knowledge graph data for [sphinx-contrib/icon](https://github.com/sphinx-contrib/icon), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/icon
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 02dca689ed7edbeffcf953747d6fff03b4c34f56
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 02dca689ed7edbeffcf953747d6fff03b4c34f56
│           └── chunk-001.nq.gz
├── blob
│   ├── 07aff847131c1989e0ce22b146c7aee9164c68b6.nq.gz
│   ├── 0ba6078ffcf6d8fb9bf816e06e0efea405a9df83.nq.gz
│   ├── 0c2d3acd2db82bb24475ca01777c7e62782ef4a2.nq.gz
│   ├── 11035bea18367df1a533cbe28fdd9281e2cf3aed.nq.gz
│   ├── 14ca3f16a3eb47580ee7ed14aa42d854842fcd10.nq.gz
│   ├── 17499cb4a5b29b93aa01b7c3818e8152071cdba1.nq.gz
│   ├── 26ff9e8a345257c792e218e5860f106c277a6e1a.nq.gz
│   ├── 2bc5d5f7118646c11eac4472d076e00ffdd1a944.nq.gz
│   ├── 2f6c1c8641261f228016a53160f8e99f889404bf.nq.gz
│   ├── 37da6e13de11f524014bb759ef76d578c786216f.nq.gz
│   ├── 3bb3189820f05744c8f286b78bda0636ef4e2147.nq.gz
│   ├── 3f0c56b17c4f9661f455f0717a11b6b43e9bc9fe.nq.gz
│   ├── 55d6ca1397761f4222fab6df6fa5cbc0c4fd419c.nq.gz
│   ├── 5d1a3fd3aa8827cd3f86d06deb8892b7ac4c4847.nq.gz
│   ├── 6457a86b7388767962a70da9355d1c36d87c6c9b.nq.gz
│   ├── 751122e07b2b1c828bbc7fc6f59875919aedb18b.nq.gz
│   ├── 87b706dfcf64dc9156e45b9ed9bd0642967fffbf.nq.gz
│   ├── 9b77ea713f9805f941350851fb4f79c0f70a0f4b.nq.gz
│   ├── a0332d0505dd4c96ff654829e9a698ab42be4e59.nq.gz
│   ├── b17ba329bee44a77f4a0ce74d18d118a0fd7f86d.nq.gz
│   ├── b911cff0f19d0500ca06099598df217be9d11e84.nq.gz
│   ├── babf9b2c03bd48b7086b64f1da9249278f3d8c3a.nq.gz
│   ├── bc6879708ecc9435e218e2abb0f953be1ea5e16f.nq.gz
│   ├── c2fdb308ff65d071a05285af61b31d853713e70a.nq.gz
│   ├── cade29e6446c87d7c9129331ae47dc3eb24a6c29.nq.gz
│   ├── d3f2e6ce02e011471a92e2c57e8591b67874a6f2.nq.gz
│   ├── d4b9eaa42769065f937246612223143853487154.nq.gz
│   ├── d5a4394dd4355bd5299e59ed8d20039c34536d2c.nq.gz
│   ├── d761b69ec83570344c8a22b732c647e66be57f58.nq.gz
│   ├── d98a14315495fd2d63430413d606bbff529d01b8.nq.gz
│   ├── db50b2601c7f7bf2fc664000ac1df5ac7cd43167.nq.gz
│   ├── e3015fb92acb8c479091f66a7b97f744b5119d20.nq.gz
│   ├── ebba1c022f842429aea255ed8b6be30114d557ac.nq.gz
│   ├── f9c309e0b4fcd39242dabd1d593cd7877b7493fb.nq.gz
│   └── ffcd00cf3443e52f8030506e12ba7c03baa31999.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 02dca689ed7edbeffcf953747d6fff03b4c34f56.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 43 files
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

[sphinx-contrib/icon](https://github.com/sphinx-contrib/icon)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
