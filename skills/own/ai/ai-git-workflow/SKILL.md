---
name: ai-git-workflow
description: Git workflow with AI assistance — commit messages, PR descriptions, merge conflict resolution, changelog generation. Use when writing commits, creating PRs, or resolving merge conflicts.
---

# AI Git Workflow

Streamline git operations with AI assistance.

## 1. AI-Generated Commit Messages

After making changes, let AI write the commit message:

> "Generate a conventional commit message for these changes:
> - Added login form with email/password validation
> - Created useAuth hook with session management
> - Updated types.ts with User interface
>
> Files changed: src/app/login/page.tsx, src/hooks/use-auth.ts, src/types.ts"

The AI should output:

```
feat(auth): add login form with email/password validation

- Create login page at /app/login with react-hook-form + zod validation
- Add useAuth hook for session management with token storage
- Update User interface in types.ts

Closes #123
```

## 2. AI-Generated PR Descriptions

```bash
git log main..HEAD --oneline  # Get your commits
# Feed to AI:
```

> "Write a PR description for these commits targeting the 'main' branch.
> Use format:
> - **What**: summary of changes
> - **Why**: motivation
> - **Testing**: how to verify
> - **Screenshots**: [UI changes]"

## 3. AI-Assisted Merge Conflict Resolution

When you hit a merge conflict, feed the conflicted sections to AI:

> "Resolve this merge conflict. Keep both changes where they don't conflict.
> Our branch: uses React 19 API
> Main branch: uses React 18 API
>
> ```
> <<<<<<< HEAD (our branch)
> const result = use(promise)
> =======
> const result = await promise
> >>>>>>> main
> ```"

The AI can analyze both sides and produce the correct merged version.

## 4. Changelog Generation

```bash
git log --oneline --no-decorate v1.0.0..HEAD  # Changes since last release
```

> "Generate a changelog entry from these commits. Group by type
> (Features, Bug Fixes, Performance, Chores).
> Format: keep a human-readable changelog"

## 5. Code Review Preparation

Before submitting a PR, let AI review your own diff:

> "Review my diff against main. Check for:
> - Missing error handling
> - Type safety issues  
> - Hardcoded values that should be config
> - Console.logs left behind"

## Quick Reference

| Task | Git Command | AI Prompt |
|------|-------------|-----------|
| Commit message | `git diff --cached` | "Write conventional commit for..." |
| PR description | `git log main..HEAD` | "Write PR description..." |
| Changelog | `git log --oneline v1.0.0..HEAD` | "Generate changelog..." |
| Pre-review | `git diff main...HEAD` | "Review my diff for..." |
| Merge conflict | Paste conflict block | "Resolve this conflict..." |

## Acceptance Criteria

1. Commit messages follow conventional commits format
2. PR descriptions include what/why/testing/screenshots
3. Merge conflict resolutions preserve intent from both branches
4. No debugging artifacts (console.log, commented code) in commits
