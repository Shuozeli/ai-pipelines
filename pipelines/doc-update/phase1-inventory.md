# Inventory Existing Docs

Read all existing documentation BEFORE reading any code. Build a map of what
is already documented, what claims each doc makes, and what dates/versions
they reference.

## Steps

1. Find all doc files: `docs/`, `*.md` in repo root, `llms.txt`, any `*.txt`
   in `docs/`
2. For each doc, record:
   - **File path**
   - **Purpose** (what it covers)
   - **Last-updated date** (explicit or inferred from git blame)
   - **Key claims** (counts, statuses, architecture descriptions)
   - **Cross-references** (links to other docs, mentions of specific files/features)

## Output

Write to `docs/_doc-inventory.md` using this structure:

```markdown
# Documentation Inventory

## file: path/to/doc.md
- **Purpose:** What this doc covers
- **Last updated:** date or "unknown"
- **Key claims:**
  - "Six crates in workspace" (line 24)
  - "550+ tests passing" (line 125)
  - "--annotate: TODO" (line 114)
- **Cross-references:** links to ROADMAP.md, flag-parity.md
```

## Why This Comes First

The inventory prevents the agent from creating new docs that duplicate or
contradict existing ones. Every subsequent phase references this inventory
to decide whether to update an existing doc or create a new one.
