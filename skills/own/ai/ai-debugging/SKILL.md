---
name: ai-debugging
description: Structured workflow for debugging with AI — reproduce, isolate context, feed the AI, iterate on root cause. Use when fixing a bug, investigating a failure, or diagnosing a regression.
---

# AI Debugging

Systematic approach to debugging with AI assistance.

## The Debug Loop

```
1. REPRODUCE    → Get a reliable way to see the bug
2. ISOLATE      → Narrow down where it happens
3. CONTEXT      → Feed AI the right information
4. HYPOTHESIS   → Let AI suggest root cause
5. VERIFY       → Test the fix
6. ITERATE      → If wrong, refine context
```

## Step 1: Build a Reliable Reproduction

Before asking AI, make sure you can reproduce the bug on demand:

```bash
# ✅ Good: one command to see the bug
curl http://localhost:3000/api/users/999
# → 500 Internal Server Error (not 404)

# ❌ Not: "sometimes it crashes"
```

**The tighter the reproduction, the faster the AI can help.**

## Step 2: Gather Context for the AI

Feed the AI a structured context block:

> **Bug**: Creating a user with a duplicate email returns 500 instead of 422
> **Repro**: `curl -X POST http://localhost:3000/api/users -H "Content-Type: application/json" -d '{"email":"existing@test.com"}'`
> **Expected**: 422 with "Email already exists"
> **Actual**: 500 with "TypeError: Cannot read properties of undefined"
> **Stack trace**: `at UserService.create (src/lib/user-service.ts:45)`
> **Relevant code**:
> ```ts
> // src/lib/user-service.ts:40-50
> const existing = await db.user.findUnique({ where: { email } })
> if (existing) throw new AppError(422, "Email already exists")
> const user = await db.user.create({ data: { email } })
> return user
> ```

## Step 3: Let AI Analyze, Then Verify

The AI will suggest hypotheses. **Don't blindly apply — verify first:**

| AI says | Verify by |
|---------|-----------|
| "Missing error handler" | Check if error is caught upstream |
| "Wrong query" | Run the query manually in DB console |
| "Race condition" | Add logging, run 10x |
| "Type mismatch" | Check types at the boundary |

## Step 4: Common Debug Patterns

| Symptom | What to tell AI |
|---------|----------------|
| 500 error | Full stack trace + request payload |
| Wrong UI | Expected vs actual screenshot description + component props |
| Performance | Which action is slow + how many items |
| Build error | Full error output + relevant config files |
| Hydration error | Which component + what's different server vs client |

## Step 5: When AI Can't Find It

If the AI goes in circles:

1. **Add logging** at key points → ask AI where to add logs
2. **Simplify** — remove parts until bug disappears (bisect)
3. **Write a test** that reproduces the bug → give the failing test to AI

## Acceptance Criteria

1. Bug is reliably reproducible before asking AI
2. AI gets structured context: repro + expected/actual + stack trace + code
3. AI suggestions are verified before applying
4. Max 3 iterations before switching approach
