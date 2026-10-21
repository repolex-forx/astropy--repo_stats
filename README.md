# Repolex Knowledge Graph of astropy/repo_stats

RDF knowledge graph data for [astropy/repo_stats](https://github.com/astropy/repo_stats), parsed by [repolex](https://repolex.ai).

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
rlex download astropy/repo_stats
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1fdecce1538bf22e508df40cefc5e00993d5b75b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1fdecce1538bf22e508df40cefc5e00993d5b75b
│           └── chunk-001.nq.gz
├── blob
│   ├── 146eef63d0b2f77078753fe3240f3de4e668c692.nq.gz
│   ├── 191ca52585afbaff0c2b1281cf867d9b6ba3dac5.nq.gz
│   ├── 1ac406bfca526cd2058da63efce7941c7ce33720.nq.gz
│   ├── 1ae3f8f644a24077ac3a4d3c77344974475e6d17.nq.gz
│   ├── 2119f51099bf37e4fdb6071dce9f451ea44c62dd.nq.gz
│   ├── 237effdb9d20e90715154cb9b15ffdd4fb38df58.nq.gz
│   ├── 2a57d6241a33d7f9549aa786500edef587c1b18b.nq.gz
│   ├── 31192354b7f3c3abfe5fe3cf6ce2ece48deec54e.nq.gz
│   ├── 3124e924a30a84c4caa4d516ba6791adb5bdea97.nq.gz
│   ├── 3c61a29c29cd5f4e29d291e902a4fdb274efe436.nq.gz
│   ├── 42ce49c9cf0adc3196b09d7673cf4b23ff93fa88.nq.gz
│   ├── 45bf8ff6ca5bc86d2c0bb95ca7f34aea6690c641.nq.gz
│   ├── 64f66321fc0816258ac85e0d8a3fde5a6c868b23.nq.gz
│   ├── 782fa0ce88f92753d41d730d0313a34f35514f93.nq.gz
│   ├── 79d4aabc1c508577eba052c8f83150d68a808cdd.nq.gz
│   ├── 7fd6e1935e1e07db7f66d81f4e0e9cd121816849.nq.gz
│   ├── 851940cb136b9c9d81e0df9e3cbbfbfaf46abdfe.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── 8e2b95d960f52c01d29a5f59c0847a08908bcef6.nq.gz
│   ├── 8f2bfc2e6c14bae5ba8196d17183810bf4df0d34.nq.gz
│   ├── 9b29ebbd64e4e9e97721f39c0bb4d241c11b669e.nq.gz
│   ├── 9d5122fee08565ce1d372dba03c01ec6bd5eee54.nq.gz
│   ├── 9e66ffa20a57312ab005ed61fe19ab925d0735a5.nq.gz
│   ├── a29bce7cdcad14949e33dce9c66aa07d510b6010.nq.gz
│   ├── a30c636d1d937fb7e4064dbda1f5b20b8c8696ce.nq.gz
│   ├── b79c03db85bda299fa828ade167874bb340c8d2c.nq.gz
│   ├── ba5076ba7b64cf93b6854421da9e0892cc667e41.nq.gz
│   ├── bad7a41d3bd1b1281f01e13b4a412d6e7ec51483.nq.gz
│   ├── bc27d0ed95f9110ecaea7debed375c5c5f7505d5.nq.gz
│   ├── c90a8a2a6bc1971e7a513adfe8478ca63b979963.nq.gz
│   ├── cdf8630280e37a7e8040dd5a32e3c13a9794e6d4.nq.gz
│   ├── d4bb2cbb9eddb1bb1b4f366623044af8e4830919.nq.gz
│   ├── e0f6ff90a4b056128c6ec94068a1c549459dc5ef.nq.gz
│   ├── ee186fb66743434634d1805b1dca61ad7971fe1d.nq.gz
│   ├── f102a9cadfa89ce554b3b26d2b90bfba2e05273c.nq.gz
│   └── f2008a2181eb83d7c87ab76fe72fc8006cb1edaf.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1fdecce1538bf22e508df40cefc5e00993d5b75b.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[astropy/repo_stats](https://github.com/astropy/repo_stats)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
