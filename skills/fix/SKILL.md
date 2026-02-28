---
name: fix
description: >-
  This skill should be used when the user asks to "fix this issue",
  "investigate and fix", "debug this", "find and fix the bug",
  "resolve this error", "this isn't working", "fix the build error",
  or invokes /fix with an issue description. Investigates reported issues
  methodically and applies minimal, elegant fixes.
argument-hint: <issue description>
---

# Fix

Investigate and fix reported issues with minimal, targeted changes.

Fix the following issue: $ARGUMENTS

## Phase 1: Investigation

Think first, act second. Understand the problem before touching code.

### Understand the Issue

Parse the issue description to identify the affected component, symptoms, and expected behavior. Form hypotheses about potential root causes before searching.

### Locate Relevant Code

- Use Glob to find files related to the mentioned component or feature
- Use Grep to search for relevant keywords, class names, or function names
- Read the most likely files to understand the current implementation

### Trace the Root Cause

Follow the code flow to understand how the issue manifests. Check related files — imports, parent components, utilities. Identify the minimal set of changes required.

## Phase 2: Solution Design

Before making any changes:

- Consider multiple approaches and choose the most elegant one
- Prefer minimal changes over extensive refactoring
- Ensure the solution addresses the root cause, not just symptoms
- Evaluate edge cases and potential side effects

## Phase 3: Implementation

### Make Minimal, Targeted Changes

- Use Edit tool for precise modifications
- Avoid over-engineering or adding unnecessary features
- Do not refactor unrelated code
- Keep changes focused on the specific issue

### Verify the Fix

- Run the project's type-check, lint, or test commands as appropriate (e.g., `pnpm typecheck`, `cargo check`, `go vet`, `mypy`)
- Confirm the fix resolves the root cause

## Constraints

- **Minimal changes only** — do not add features, refactor unrelated code, or make "improvements" beyond the fix
- **No over-engineering** — solve the specific problem, not hypothetical future issues
- **Elegant solutions** — prefer simple, clear fixes over complex ones
- **Type safety** — ensure all changes pass the project's type checks or compiler
- **Root cause focus** — fix the underlying issue, not just the symptoms

## Output

Provide:

1. **Root Cause Analysis** — what caused the issue and why
2. **Solution Rationale** — why this approach is minimal and elegant
3. **Changes Made** — specific modifications with file references
4. **Verification** — confirmation the fix works and types pass
