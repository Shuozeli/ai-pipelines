# Apply Doc Updates

Work through `docs/_doc-diff.md` and apply each update. Edit existing docs
in place. Only create new docs when the diff explicitly calls for it.

## Rules

- Fix one doc file at a time
- For stale claims: edit the specific line/section, preserve surrounding context
- For missing coverage: add to the most relevant existing doc section
- For outdated statuses: update the status field/cell, add a brief note
- Do NOT rewrite docs from scratch -- make targeted edits
- Do NOT add information that isn't backed by code facts from Phase 2
- Do NOT change doc formatting, style, or structure unless required by the fix
- After editing each file, re-read it to confirm the change is coherent in context

## When to Create a New Doc

Only create a new doc file when ALL of these are true:
1. The diff says "CREATE new doc"
2. No existing doc covers the topic (even partially)
3. The topic spans multiple modules/crates (not just a single function)

When creating, check the inventory first for naming conventions and structure
patterns used by existing docs.

## Cleanup

After all updates are applied:
1. Delete the working files: `_doc-inventory.md`, `_code-facts.md`, `_doc-diff.md`
2. Update any "last updated" dates in modified docs
3. Verify no broken cross-references between docs
