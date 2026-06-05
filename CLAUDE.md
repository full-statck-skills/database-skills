# CLAUDE.md

## Overview

Database skills plugin for Claude Code — 5 database reference skills covering PostgreSQL, MySQL, Oracle, Redis, and Elasticsearch. Part of the [full-stack-skills](https://github.com/full-statck-skills) ecosystem maintained by PartMeAI. Compatible with the [Agent Skills spec](https://agentskills.io).

## Skills

| Skill | Directory | Focus |
|-------|-----------|-------|
| PostgreSQL | `skills/postgresql/` | JSONB, CTE, window functions, replication, full-text search, partitioning |
| MySQL | `skills/mysql/` | Connection pooling, slow query optimization, replication, backup, JSON/DDL |
| Oracle | `skills/oracle/` | PL/SQL, AWR tuning, RMAN backup, Data Guard, RAC, analytic functions |
| Redis | `skills/redis/` | All data types, clustering, streams, caching, pub/sub, memory optimization |
| Elasticsearch | `skills/elasticsearch/` | Full-text search, aggregations, reindexing, cluster ops, ELK integration |

## Directory Structure

```
skills/<name>/
├── SKILL.md            # Main skill file with YAML frontmatter (entry point)
├── examples/           # 4-5 real-world usage examples (01-*.md to 05-*.md)
└── references/         # 6-10 deep-dive reference guides (01-*.md to 10-*.md)
```

Root-level: `.claude-plugin/plugin.json` (plugin manifest), `README.md` + `README.zh-CN.md` (bilingual docs), `LICENSE` (Apache 2.0).

## SKILL.md Authoring Conventions

**YAML frontmatter** (required):
```yaml
---
name: <lowercase-name>
description: <one-line summary, ~150 chars, starts with "Provides comprehensive guidance for...">
license: Complete terms in LICENSE.txt
---
```

**Body structure** (use this order):
1. `# Name -- Short Description` (title)
2. ASCII workflow diagram showing decision flow
3. When to Use / When NOT to table
4. Boundary table (fully applicable / conditional / not applicable + alternatives)
5. Syntax/feature quick-reference tables (cross-reference `references/` files)
6. Advanced features index
7. Gotchas — numbered table of common pitfalls (~15 items)
8. FAQ — numbered Q&A (~10-15 items)
9. Keywords — comma-separated list
10. References — official docs URLs + links to local `references/` and `examples/` files

**Conventions**:
- SKILL.md is the entry point; keep it ~200 lines (cheat-sheet style). Delegate depth to `references/`.
- Files in `examples/` and `references/` use zero-padded numeric prefixes (`01-`, `02-`, etc.).
- Reference files have **no** YAML frontmatter — plain Markdown only.
- Titles and descriptions are in Chinese; code, commands, and keywords are in English.
- When adding a new skill, register it in `.claude-plugin/plugin.json` under `skills`.

## Key Files

- `.claude-plugin/plugin.json` — plugin manifest listing all 5 skill paths
- `README.md` / `README.zh-CN.md` — installation and usage docs (install via `npx skills add`)
- `LICENSE` — Apache 2.0 with third-party notices
