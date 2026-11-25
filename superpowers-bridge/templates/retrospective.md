# Retrospective: <change-name>

> Written: <YYYY-MM-DD> (after verify passed)
> Commit range: `<base-sha>..<head-sha>`
> Worktree: <path or "merged to main">

---

## 0. Evidence

> Quantitative front-matter — the Wins / Misses bullets below reference it
> directly, avoiding a repeated [evidence: ...] on every line.
> Cold-write scenario (retro written some time after the cycle ends): this
> section should be reconstructable from `git log` + `tasks.md` + commit
> messages alone.

- **Commit range**: `<base-sha>..<head-sha>` (<n> commits)
- **Diff size**: <+X / -Y lines across N files>
- **Tasks done**: <x>/<y> (`grep -cE '^\s*- \[x\]' tasks.md` → x; the regex allows sub-task indentation)
- **Active hours**: <estimate>
- **Subagent dispatches**: <count or "n/a">
- **New external dependencies**: <list, with license + version, or "none">
- **Bugs encountered post-merge**: <count, one-line each, or "none">
- **OpenSpec validate state at archive**: <pass / fail / not-run>
- **Test coverage signal**: <e.g. jacoco %, pytest count, vitest count, or "n/a">

Commit chain (chronological):

```
<base-sha> <one-line summary>
...
<head-sha> <archive commit one-line>
```

---

## 1. Wins

- [evidence: <commit/file/test>] <description>

## 2. Misses

- 🔴 [blocking | evidence: ...] <description>
- 🟡 [painful  | evidence: ...] <description>
- 📌 [nit      | evidence: ...] <description>

## 3. Plan deviations

| Plan task | What changed | Why |
|-----------|--------------|-----|
| 1.2       | ...          | ... |

## 4. Skill / workflow compliance

| Skill                                            | Used |
|--------------------------------------------------|------|
| superpowers:brainstorming                        |      |
| superpowers:writing-plans                        |      |
| superpowers:using-git-worktrees                  |      |
| superpowers:subagent-driven-development          |      |
| (transitive) superpowers:test-driven-development |      |
| (transitive) superpowers:requesting-code-review  |      |
| superpowers:finishing-a-development-branch       |      |

> **Default expectation**: all ✓. Every skill is part of the schema's design;
> skipping one is an exceptional situation. Any ✗ must be justified in the
> `### Deliberately Skipped Skills` subsection below, with cause and prevention.

### Deliberately Skipped Skills

> Skipping a skill is the design's escape hatch, not the normal path. Each ✗
> must answer the three questions below; a blank section (all green) is the
> expected state.

- **`<skill name>`**
  - **What was skipped**: <the specific skill, or a sub-step within it>
  - **Why this cycle**: <the concrete cycle condition — vague reasons like "not needed" / "too small" / "no time" / "blocked by an external dep" / "the skill's output looked off" are not acceptable; name the actual trigger (a specific commit / log line / observed behavior)>
  - **How to prevent recurrence**: how should the next cycle in the same situation avoid skipping? Pick one:
    - `schema graph fix` — name the specific part of schema.yaml to change
    - `skill description tightening` — name which skill's frontmatter / instruction to tighten
    - `CLAUDE.md trigger` — name the interpretation rule to add to the adopter's CLAUDE.md.fragment
    - `scope-judgment rule` — state how this cycle's scope should have been judged
    - `one-off — schema boundary case, no prevention possible` — but state explicitly why it's a boundary case (vague reservations not accepted)

> **Relationship to §6 Promote candidates**: if multiple cycles skip the same
> skill with the same `How to prevent` answer, that pattern should be promoted
> to §6 and trigger a schema / skill PR directly — it must not accumulate into
> a "norm".

## 5. Surprises

- <assumption that turned out wrong>

## 6. Promote candidates → long-term learning

Each candidate uses a `- [ ]` checklist:

- Title: severity emoji (🔴/🟡/📌) + a one-sentence learning
- `→ **Promote to** <destination>` (memory / CLAUDE.md / schema / skill / one-off)
- Two body lines (matching the superpowers feedback memory body schema):
  - `> **Why**: <reason; often a past incident or strong preference>`
  - `> **How to apply**: <when/where this guidance kicks in>`

An unchecked `- [ ]` means the candidate hasn't been promoted yet — it can be
carried to the next cycle's retro for re-evaluation, or kept as a cross-cycle
observation point.

> **Carry-forward mechanism**: when writing the next cycle's retro, run
> `grep -A 5 '^- \[ \]' openspec/changes/archive/*/retrospective.md` to pull
> prior unchecked candidates, and decide per item whether to carry it forward
> into this cycle's §6, promote it on the spot, or mark it stale and stop
> tracking it.

Example:

- [ ] 🔴 **<short rule>** → **Promote to memory** (type: feedback)
  > **Why**: <past incident or strong preference that motivated this rule>
  > **How to apply**: <which file / cycle phase / decision moment this kicks in>

- [ ] 🟡 **<another candidate>** → **Promote to project CLAUDE.md** (`<path/to/CLAUDE.md>` section)
  > **Why**: ...
  > **How to apply**: ...

- [ ] 📌 **<third candidate>** → **One-off** (record only, do not promote)
  > **Why**: <why it doesn't generalize>
