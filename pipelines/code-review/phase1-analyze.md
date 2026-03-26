# Code Quality Audit

Perform a thorough quality audit of this codebase. Produce concrete evidence:
exact file paths, line numbers, and descriptions of every issue you find.
The output must be specific enough to present in a code review.

## What to Look For

| Category | Examples |
|----------|---------|
| **Duplication** | Identical or near-identical functions, copy-pasted logic across files |
| **Dead code** | Unused functions, unreachable branches, imports with no callers |
| **Placeholder modules** | Empty files, stubs with only TODO comments, declared but unpopulated crates |
| **Missing abstractions** | Three similar blocks that should be one generic helper, hand-written conversions that should be macros or derives |
| **Silent failures** | Swallowed errors, functions returning empty defaults instead of propagating errors, bare catch-all handlers |
| **No-op code** | Bitwise OR with zero, redundant conditions, assignments that are immediately overwritten |
| **Over-architecture** | Too many modules for the problem size, abstractions with a single implementation, unnecessary indirection |
| **Unsafe patterns** | `unwrap()` in non-test code, unchecked casts, missing input validation at system boundaries |
| **Noise** | Comments that restate the code, excessive section dividers, documentation that adds no information |

## Language-Specific Checks

### Rust

- `.clone()` where ownership transfer or borrowing would work
- Hand-written `From`/`Into` impls that should be `derive` or a macro
- Copy-pasted match arms with minor variations
- `#[allow(...)]` suppressing real warnings instead of fixing them
- Stringly-typed APIs that should use enums
- `unwrap()` / `expect()` in non-test code paths
- Unused crates in the workspace `Cargo.toml`

### TypeScript / JavaScript

- `any` types (use `unknown` with type guards instead)
- Unused exports
- Copy-pasted route handlers or middleware
- Placeholder error handling (`catch (e) {}`)
- Inconsistent patterns across similar files

### Python

- Bare `except:` clauses
- Unused imports
- Duplicate helper functions
- Over-engineered class hierarchies for simple operations
- Missing type annotations on public functions

### Go

- Error handling that discards context (bare `return err` without wrapping)
- Duplicate struct definitions
- Interfaces with a single implementation
- Empty test files
- Copy-pasted handler functions
