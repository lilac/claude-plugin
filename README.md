# claude-plugin

Developer workflow skills for Claude Code.

## Skills

### /commit

Generate terse, precise conventional commit messages from staged or unstaged git changes.

```
/commit                    # auto-generate commit message
/commit fix the typo       # incorporate extra instructions
```

### /fix

Investigate and fix reported issues with minimal, targeted changes. Follows a phased approach: investigate root cause, design an elegant solution, implement minimal changes, verify with typechecks.

```
/fix button click handler not firing on mobile
/fix TypeScript error in auth middleware
```

## Installation

Add the marketplace and install the plugin:

```bash
/plugin marketplace add lilac/claude-plugin
/plugin install dev@claude-plugin
```

Or for local development:

```bash
claude --plugin-dir /path/to/claude-plugin
```
