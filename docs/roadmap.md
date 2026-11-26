# Roadmap

[English](./roadmap.md) · [繁體中文](./roadmap.zh-TW.md)

This repository is actively maintained as a side project. The roadmap below sketches what's planned but isn't a contract — items can shift based on what real usage surfaces.

## v1 — Released

- [x] **`superpowers-bridge`** — bridges OpenSpec ↔ obra/superpowers + native `retrospective` artifact

## v1.x — In follow-up backlog

These items are tracked in `~/.claude/plans/pr-quizzical-oasis.md` (the implementation plan):

- [ ] **`workflow-retrospective` skill packaging** — currently the retrospective procedure is embedded in the schema instruction (Decision 3). If real users need to invoke `/workflow-retrospective` interactively (outside the schema flow), repackage as a Claude Code plugin
- [ ] **End-to-end CI integration test** — current CI only runs `openspec schema validate`. A round-trip test (`/openspec-new-change` through `/openspec-archive-change`, including the same steps when the OpenSpec 2.2 `/openspec` router dispatches them) would catch regressions but requires Superpowers in CI. The router does not select `superpowers-bridge` unless that schema is the project default or the request names it.
- [ ] **Verify artifact 5 polish points** — listed in v1.1 backlog A (templates clarity, design optional handling, worktree origin, pass criteria, TDD note)

## Awaiting OpenSpec core

These cannot be solved in a community schema:

- [ ] **`requires_skills:` schema field** — would replace the prompt PRECHECKs with engine-validated declarations
- [ ] **`post_apply` phase** — would let `verify` and `retrospective` be true post-apply hooks instead of artifacts with timing-mismatch (analogous to spec-kit's `after_implement`)

## Future bridge candidates

When real demand surfaces:

- [ ] **`obra-bridge`** — broader integration with other obra/* tools (if the user community grows)
- [ ] **Domain-specific schemas** — e.g., a `data-pipeline` schema variant with stronger schema-validation artifacts

Want to suggest a bridge? Open an issue at <https://github.com/JiangWay/openspec-schemas/issues>.
