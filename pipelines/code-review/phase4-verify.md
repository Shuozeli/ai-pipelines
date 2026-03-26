# Verify and Ship

Run the formatter, full test suite, commit, push, and confirm CI passes.

## Steps

1. Run the formatter (`cargo fmt`, `prettier --write .`, `ruff format .`, etc.)
2. Run the linter (`cargo clippy`, `eslint`, `ruff check`, etc.) and fix any new warnings
3. Run the full test suite
4. Review the diff one final time — make sure no unrelated changes slipped in
5. Commit with a clear message describing what was fixed and why
6. Push and confirm CI passes
7. If CI fails, fix the issue, commit, push, and re-verify
