# hte-claude-tools

Discovery marketplace for Claude Code plugins by [HTE Switzerland](https://hendrikthurau.enterprises).

This repo is a single manifest file pointing at independent plugin repositories. Each plugin lives in its own repo and ships independently; the marketplace just aggregates them so you can install the whole toolkit with one command.

## Install

```bash
claude plugin add-marketplace github:HthSolid/hte-claude-tools
```

Then install plugins individually:

```bash
claude plugin install claude-dejavu
claude plugin install claude-chillbro
```

## Plugins

| Plugin | What it does | Repo |
|---|---|---|
| **claude-dejavu** | Memory + recovery + code grounding. Restores deleted sessions, hybrid Postgres+Weaviate recall across past conversations, tree-sitter symbol indexing, and a deterministic rewriter that catches fabricated identifiers before disk write. | [HthSolid/claude-dejavu](https://github.com/HthSolid/claude-dejavu) |
| **claude-chillbro** | Auto-approves obviously-safe Bash commands and in-project file writes so Claude Code stops asking permission for every `grep`, `cat`, `ls`, and new file. Static allow/ask lists, self-learning, context-aware probes, and a headless `claude -p` classifier as a last-resort fallback. | [HthSolid/claude-chillbro](https://github.com/HthSolid/claude-chillbro) |

## Why a marketplace instead of a monorepo?

The plugins are functionally orthogonal: dejavu is heavy (Postgres, Weaviate, tree-sitter) and serves memory/grounding use cases; chillbro is tiny and serves permission ergonomics. Bundling their source would force a coupling that does not reflect reality, and dejavu's footprint should not be implicit when someone wants a small permission helper. A pointer marketplace gives you one install URL without the coupling tax.

Each plugin retains its own repo, version, release cadence, and issue tracker.

## License

MIT, see [LICENSE](LICENSE).
