# Document Findings

Write all findings to a local markdown file. Each issue must include exact
code locations, a description of the problem, and a concrete fix. This file
becomes the work queue for Phase 3.

## Output

Write to `docs/code-quality-findings.md` using this structure:

```markdown
# Code Quality Findings

## 1. Category Name (e.g., Duplication, Dead Code)

### Issue Title
- **Location:** `path/to/file.rs:42-58` (function_name)
- **Also at:** `path/to/other.rs:100` (if duplicated)
- **Problem:** What is wrong and why it matters.
- **Fix:** Concrete action to resolve it.
```

## Requirements

- Every issue must have exact file paths and line numbers
- Group related issues under category headings
- Order categories by severity (most impactful first)
- Each fix must be actionable ("extract into a shared helper in `module::util`"),
  not vague ("refactor this")
- If an issue is cosmetic or low-priority, mark it as such so Phase 3 can
  triage effectively
