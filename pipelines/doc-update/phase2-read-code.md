# Read Code and Collect Facts

Read all source code to build a ground-truth understanding of the codebase.
Do NOT write any docs yet. The goal is to collect facts that will be compared
against the inventory from Phase 1.

## Steps

1. Read all config files (Cargo.toml, package.json, pyproject.toml, etc.)
   to understand the project structure, dependencies, and crate/package layout
2. Read all source files systematically (entry points first, then dependencies)
3. Read all test files to understand test coverage and testing patterns
4. Read CI config to understand the build/test pipeline

## Output

Write to `docs/_code-facts.md` using this structure:

```markdown
# Code Facts

## Project Structure
- Workspace has N crates: list them
- Binary entry point: path
- Key dependencies: list

## Per-Module Summary
### module-name (crate-name)
- Purpose: one line
- Public API: key functions/types
- Internal structure: key files and what they do

## Feature Inventory
- Feature X: implemented in path/to/file.rs
- Feature Y: implemented, gated behind feature flag "z"
- Feature W: stub only, not functional

## Test Summary
- N tests across M files
- Testing patterns: golden tests, unit tests, integration tests, fuzz
- CI: what runs, what doesn't
```

## Rules

- Do NOT read .md files (those are docs, covered by Phase 1)
- Record only what the code actually does, not what docs say it does
- Note any discrepancies you already spot (e.g., a function exists but
  the doc says it's "TODO")
