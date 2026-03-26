# Diff Docs Against Code

Compare the inventory (Phase 1) against the code facts (Phase 2). Identify
every discrepancy: stale claims, missing coverage, incorrect descriptions,
and outdated statuses.

## Steps

1. For each claim in the doc inventory, check it against the code facts:
   - Is the claim still true?
   - Has it become partially true (e.g., "TODO" but now implemented)?
   - Is it completely wrong (e.g., "uses tree-sitter" but code uses hand-written parser)?
2. For each code fact, check if it's documented:
   - Is there an existing doc that covers this?
   - Is the coverage accurate and complete?
   - Is there a gap (feature exists but no doc mentions it)?

## Output

Write to `docs/_doc-diff.md` using this structure:

```markdown
# Doc vs Code Diff

## Stale Claims (doc says X, code says Y)

### claim description
- **Doc:** path/to/doc.md line N -- "exact quote"
- **Code:** path/to/file.rs -- actual behavior
- **Action:** UPDATE doc to say Y / REMOVE claim / REWRITE section

## Missing Coverage (code has X, no doc covers it)

### feature or module name
- **Code:** path/to/file.rs -- what it does
- **Action:** ADD to existing doc path/to/doc.md section Z / CREATE new doc

## Outdated Statuses (marked TODO/STUB but now done)

### feature name
- **Doc:** path/to/doc.md line N -- "TODO" or "STUB"
- **Code:** path/to/file.rs -- implemented and working
- **Action:** UPDATE status to DONE with description
```

## Rules

- Every diff entry must reference both the doc location AND the code location
- Prefer updating existing docs over creating new ones
- Only recommend creating a new doc if no existing doc covers the topic
  and the topic is substantial enough to warrant its own file
- Do NOT create docs that overlap with existing docs -- that's the context
  pollution this workflow is designed to prevent
