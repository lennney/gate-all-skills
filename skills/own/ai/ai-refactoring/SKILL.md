---
name: ai-refactoring
description: Use AI to refactor code safely — define scope, set invariants, let AI transform, verify nothing broke. Use when migrating patterns, extracting components, or upgrading dependencies.
---

# AI Refactoring

Safe, verifiable refactoring workflow with AI assistance.

## The Refactor Loop

```
1. DEFINE SCOPE   → What's changing, what's NOT changing
2. SET INVARIANTS → Tests, types, or build must still pass
3. AI EXECUTES    → Let AI do the mechanical transformation
4. VERIFY         → Run invariants, review diff
5. ITERATE        → Fix until clean
```

## Step 1: Define Scope Clearly

Tell the AI exactly what to change and what NOT to change:

> **Refactor**: Extract the user profile section from `src/app/settings/page.tsx` into a new component at `src/components/profile-section.tsx`
> **Keep**: All props, all behavior, all styles
> **Don't change**: Other sections on the settings page
> **Pattern**: Use the same prop patterns as `src/components/notification-section.tsx`

## Step 2: Set Invariants (Safety Net)

Before the AI changes anything, make sure you can verify correctness:

```bash
# TypeScript check
npm run typecheck

# Tests pass
npm test

# Build succeeds
npm run build
```

**After AI's changes, run these again.** If they still pass, the refactor is safe.

## Step 3: Let AI Execute the Mechanical Part

Refactoring is what AI does best — repetitive, pattern-based transformations.

**Good for AI:**
- Extract component from large file
- Migrate from one API to another
- Rename/move files and update imports
- Convert class component to function component
- Split one function into several smaller ones
- Add TypeScript types

**Bad for AI (do yourself):**
- Design decisions (what the new API should look like)
- Architecture changes (module boundaries)
- Performance-critical sections

## Step 4: Verify the Refactor

After AI finishes:

```bash
git diff --stat              # Which files changed?
npm run typecheck            # No type errors
npm test                     # All tests pass
npm run build                # Build succeeds

# For UI refactors: visually check the page
npm run dev                  # Open browser, spot check
```

## Step 5: Commit in Stages

For large refactors, commit after each logical step:

```bash
git add -A
git commit -m "refactor: extract ProfileSection component"
# Then next refactor...
git commit -m "refactor: migrate SettingsPage to use ProfileSection"
```

## Common Refactor Patterns

| Task | Prompt |
|------|--------|
| Extract component | "Move the user list from page.tsx to components/user-list.tsx. Keep the same props interface." |
| Add types | "Add TypeScript interfaces for all props in this file. Infer types from usage." |
| Split function | "Split fetchAndProcessUsers into fetchUsers and processUsers. Keep the same return type." |
| Rename | "Rename UserService to UserRepository across the project. Update imports." |

## Acceptance Criteria

1. Scope is explicitly defined before AI starts (what changes, what doesn't)
2. Invariants (typecheck + test + build) run before and after
3. Each refactor step is committed separately
4. Final result is visually verified for UI components
