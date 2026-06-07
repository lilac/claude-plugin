# Fix Commit Message Formats

## Single Issue

Use plain prose for the description, indent root cause and fix:

```
fix(chat): sandbox tool result not updating during streaming

Tool result stuck showing "Created sandbox" instead of final message
- Root cause: memo comparison `() => true` blocked all re-renders
- Fix: Compare actual props to allow updates when result changes
```

## Multiple Issues

Use a numbered list for each issue:

```
fix(chat): document tool type and message gaps

1. Document tools rendered identically regardless of create/update type
   - Root cause: DocumentPreview hardcoded type instead of checking isUpdate flag
   - Fix: Determine type dynamically from args?.isUpdate to show correct icon and text

2. Inconsistent gaps between message parts during streaming
   - Root cause: Gap applied conditionally based on text content presence
   - Fix: Apply gap based on part count (>1) for consistent spacing
```

## Guidelines

- Keep each line concise — one short sentence, ~12 words
- Always include root cause and fix lines
- Describe the change at the level of intent: enough to understand the bug and the remedy, not a line-by-line account
- Never collapse the body into a prose paragraph — keep the bullet/numbered structure
- The subject line states the symptom; the body explains the cause
