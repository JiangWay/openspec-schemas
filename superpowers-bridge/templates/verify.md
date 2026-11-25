# Verification Report

> This file is produced by the `openspec-verify-change` skill after apply
> completes, to confirm the implementation is consistent with specs / design /
> tasks. Failed checks must return to the corresponding artifact for fixing,
> then re-run verify.

**Change**: `<change-name>`
**Verified at**: `YYYY-MM-DD HH:mm`
**Verifier**: `<who / which agent>`

---

## 1. Structural Validation (`openspec validate --all --json`)

- [ ] All items report `"valid": true`

**Result**:

```text
<paste a summary of the openspec validate --all output>
```

If any items fail, list id + issues:

| Item | Type | Issues |
|---|---|---|
| — | — | — |

---

## 2. Task Completion (`tasks.md`)

- [ ] All `- [ ]` have become `- [x]`

**Incomplete tasks** (if any):

| Task | Reason incomplete | Blocks archive? |
|---|---|---|
| — | — | — |

---

## 3. Delta Spec Sync State

For each capability directory under `openspec/changes/<name>/specs/`, compare
against `openspec/specs/<capability>/spec.md`:

| Capability | Sync status | Notes |
|---|---|---|
| — | ✓ synced / ✗ needs sync / N/A | — |

---

## 4. Design / Specs Coherence Spot Check

Spot-check whether `design.md`'s decisions are reflected in the Requirements
and Scenarios of `specs/*.md`:

| Sample | design description | specs counterpart | Gap |
|---|---|---|---|
| — | — | — | — |

**Drift warnings** (non-blocking):

- <list if any; otherwise write "none">

---

## 5. Implementation Signal

- [ ] No unstaged files in the worktree
- [ ] All relevant commits pushed

**Commit range** (if known): `<from-sha>..<to-sha>`

---

## 6. Front-Door Routing Leak Detector (warning, non-blocking)

Design output should not land in `docs/superpowers/specs/` (the brainstorm
artifact's output redirection routes it to
`openspec/changes/<name>/brainstorm.md`).

Detection:

```bash
ls docs/superpowers/specs/*.md 2>/dev/null
```

- [ ] No files, or any present are legitimate pre-schema-install holdovers

**Leak list** (if any):

| File | Content captured into change? | Suggested action |
|---|---|---|
| — | — | — |

> Does not block archive. Leaks produced by a new schema-installed cycle
> should be moved into `openspec/changes/<name>/brainstorm.md` or `design.md`,
> then the originals deleted.

---

## 7. Deferred Manual Dogfood vs Automated Test Equivalence

For each manual dogfood / smoke task marked `[~]` deferred in plan.md, list the
equivalent automated-test coverage. If no equivalent automated test exists,
treat that item as a **real gap** rather than a legitimate deferral, and record
it in the retrospective's Misses.

| Deferred dogfood (plan §) | Equivalent automated test | Coverage assessment | Real gap? |
|---|---|---|---|
| e.g. §11.3 `compose up + curl /actuator/health` | `LinebcIntegrationApplicationTests` (Testcontainers, 24s) | Spring context boot + Flyway migrations complete + key beans injected | ❌ already equivalently covered |
| — | — | — | — |

> **Interpretation rules**:
> - "Equivalent" = the automated test's assertion set is a superset of the manual dogfood's expected assertions
> - "Coverage assessment" = list the layers actually exercised (context / DB schema / wiring / HTTP path / etc.)
> - For any row where "Real gap = ✅", the Overall Decision may still be PASS, but a follow-up item must be left in the retrospective

> **When this section may be left blank**: if plan.md has no `[~]`-marked rows at all, this section need not be filled (blank = PASS).
> As soon as plan.md contains any `[~]`, this section must enumerate each one, otherwise the Overall Decision should be downgraded to FAIL.

---

## Overall Decision

- [ ] ✅ PASS — may proceed to finishing-a-development-branch and archive
- [ ] ⚠️ PASS WITH WARNINGS — may proceed, but note: `<explanation>`
- [ ] ❌ FAIL — return to the failing artifact, fix it, and re-run verify

**Next step**:

<describe the next action>
