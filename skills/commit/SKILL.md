---
name: commit
description: >-
  This skill should be used when the user asks to "commit", "commit changes",
  "create a commit", "git commit", "save my changes", "make a commit",
  or invokes /commit. Generates terse, precise conventional commit messages
  from staged or unstaged git changes.
argument-hint: [extra instructions]
allowed-tools: Bash(git status:*) Bash(git diff:*) Bash(git add:*) Bash(git commit:*)
---

# Commit

Generate a terse, precise conventional commit message and commit current git changes.

## Workflow

1. Run `git status` and `git diff --staged` to inspect staged changes
2. If nothing is staged, run `git diff` to review unstaged changes and stage relevant files with `git add`
3. Analyze the diff to understand what was modified
4. Compose a commit message following the format guidelines below
5. Commit using the heredoc format (see below)
6. Do NOT push to remote unless explicitly requested

## Commit Message Format

Start with a type prefix in imperative mood, keeping the subject line under 50 characters:

```
type(scope): concise description
```

**Type prefixes**: `feat`, `fix`, `refactor`, `docs`, `style`, `test`, `chore`

Be specific about *what* changed, not *how* or *why*. Example: `feat(chat): add message streaming support`

### Long Bodies (non-fix commits)

When a commit affects multiple distinct areas and a body helps, use a bullet list — one item per area, one sentence each:

```
feat(chat): add message streaming and retry support

- Streaming: open an SSE connection and flush tokens as they arrive
- Retry: re-send on transient network errors with exponential backoff
```

### Fix Commits

For fix commits, always include a body. Follow the format in [fix-commit-formats.md](./references/fix-commit-formats.md) for single-issue and multi-issue examples.

### Extra Instructions

When the user provides extra instructions via `$ARGUMENTS`, incorporate that guidance into the commit message while maintaining terseness.

## Commit Execution

Always use the heredoc format to avoid shell escaping issues:

```bash
git commit -m "$(cat <<'EOF'
type(scope): subject line

Optional body here.
EOF
)"
```

## Constraints

- Do NOT use the TodoWrite tool
- Do NOT run exploration commands beyond git commands
- Do NOT push unless explicitly requested
- Follow the git commit safety protocol from project CLAUDE.md if present
