# ai-pipelines

Reusable multi-phase prompt pipelines for AI coding agents.

Each pipeline is a sequence of phase prompts that guide an AI agent through a
structured workflow. Phases are designed to be run sequentially -- each phase
produces artifacts that the next phase consumes.

## Available Pipelines

| Pipeline | Phases | Description |
|----------|--------|-------------|
| [code-review](pipelines/code-review/) | 4 | Audit codebase quality, document findings, fix issues, verify |
| [doc-update](pipelines/doc-update/) | 4 | Inventory docs, read code, diff docs vs code, apply updates |

## Pipeline Structure

Every pipeline lives under `pipelines/<name>/` and follows the same convention:

```
pipelines/<name>/
  phase1-<verb>.md    # First phase prompt
  phase2-<verb>.md    # Second phase prompt
  ...
```

Each phase file is a self-contained prompt that can be fed to an AI agent.
Phases are numbered to enforce execution order.

## How to Use

Feed each phase prompt to your AI agent in order. Wait for the agent to
complete each phase before starting the next. Example with Claude Code:

```bash
# Run each phase sequentially
cat pipelines/code-review/phase1-analyze.md | claude --print
cat pipelines/code-review/phase2-document.md | claude --print
cat pipelines/code-review/phase3-fix.md | claude --print
cat pipelines/code-review/phase4-verify.md | claude --print
```

## Design Principles

- **Phase isolation:** Each phase has a single responsibility and clear output
- **Evidence-based:** Phases produce concrete artifacts (files, diffs, inventories) not summaries
- **Incremental:** Each phase builds on the previous phase's output
- **Language-agnostic:** Pipelines work across Rust, TypeScript, Python, Go, etc.

## Adding a New Pipeline

1. Create `pipelines/<name>/`
2. Add numbered phase files: `phase1-<verb>.md`, `phase2-<verb>.md`, ...
3. Each phase should specify: what to do, what output to produce, and rules/constraints
4. Update this README's pipeline table
