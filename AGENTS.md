# Documentation project instructions

## About this project

- This is the documentation site for [HexxlaDB](https://github.com/hexxla/hexxladb) — an embedded Go database for persistent, structured, contradiction-aware storage with spatial indexing. Primary use case: LLM memory and context assembly, but also suitable for knowledge graphs, versioned document management, conflict resolution systems, audit trails, semantic search applications, decision support systems, spatial-temporal data, and research and fact-checking.
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Run `mint dev` to preview locally
- Run `mint broken-links` to check links

## Terminology

- **Cell** — A data unit at a hex coordinate with content, tags, provenance, confidence, and validity window
- **Seam** — A visible marker linking two cells that contradict each other, with reason, confidence delta, and resolution status
- **Edge** — A directed relationship between cells ("see also", "follow-up", "derived from")
- **Facet** — A summary or annotation cryptographically bound to a cell (6 facet IDs: 0-5)
- **Coord** — Axial hex coordinate (q, r) used for spatial addressing
- **PackedCoord** — Morton-encoded 128-bit coordinate used as primary key in storage
- **HNSW** — Hierarchical Navigable Small World graph for approximate nearest-neighbor vector search
- **MVCC** — Multi-Version Concurrency Control for snapshot isolation and time-travel queries
- **Ring walk** — Deterministic traversal of cells at a fixed hex distance from a center
- **Context pack** — Budgeted neighborhood assembly for context construction
- **Supersession** — A directional seam indicating that one cell replaces another (preference evolution)
- Use "database" not "DB" when referring to HexxlaDB in prose
- Use "transaction" not "tx" in prose (tx is acceptable in code blocks)
- Use "coordinate" not "coord" in prose (Coord is acceptable in code blocks)

## Style preferences

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references
- When referring to Go package paths, use backticks: `github.com/hexxla/hexxladb`
- When referring to documentation files, use backticks: `HEXXLA_DB.md`, `API_REFERENCE.md`
- Use "hexagonal lattice" not "hex grid" when describing the spatial model
- Use "Morton encoding" or "Morton packing" when referring to coordinate encoding
- Use "vector embedding" or just "embedding" — avoid "vector search" when describing the feature

## Content boundaries

**Document:**

- Public API surface (all exported symbols from `package hexxladb`)
- Core concepts: cells, seams, edges, facets, coordinates, embeddings, MVCC
- Storage layout and key encoding (from HEXXLA_DB.md)
- Memory model and retrieval patterns (from HEXXLA.md)
- Usage examples and quick start guides
- Production operations: backups, encryption, changefeed, retention
- Query engine behavior and predicate semantics

**Do not document:**

- Internal implementation details under `internal/` (engine, record, index, lattice, hnsw)
- Package-level internals unless they are relevant to understanding the public API
- Development workflows or CI/CD processes (those belong in CONTRIBUTING.md in the repo)
- Benchmark results unless they are illustrative of performance characteristics
- Roadmap items that are speculative or not yet implemented

**Source of truth:**

- The canonical documentation lives in the hexxladb GitHub repo under `docs/`
- This Mintlify site should mirror and present that content in a web-friendly format
- When in doubt, reference the source files in the hexxladb repository
