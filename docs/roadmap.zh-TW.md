# Roadmap

[English](./roadmap.md) · [繁體中文](./roadmap.zh-TW.md)

本 repo 是一個持續維護中的個人 side project。下面的 roadmap 是規劃,不是承諾 —— 項目會視實際使用回饋而調整。

## v1 — 已釋出

- [x] **`superpowers-bridge`** — 串接 OpenSpec ↔ obra/superpowers,自帶 `retrospective` artifact

## v1.x — 後續 backlog

這些項目記錄在 `~/.claude/plans/pr-quizzical-oasis.md`(實作 plan):

- [ ] **`workflow-retrospective` skill 打包** — 目前 retrospective procedure 內嵌在 schema instruction 裡(Decision 3)。如果有真實使用者反映需要互動式呼叫 `/workflow-retrospective`(在 schema 流程之外),會把它升級成獨立的 Claude Code plugin
- [ ] **End-to-end CI 整合測試** — 目前 CI 只跑 `openspec schema validate`。round-trip 測試(`/openspec-new-change` 一路到 `/openspec-archive-change`)能抓更多回歸,但需要 Superpowers 進入 CI 環境
- [ ] **Verify artifact 5 處改進** — 列在 v1.1 backlog A(template 表達清晰、design 可選處理、worktree 來源、pass 標準、TDD 註記)

## 等 OpenSpec core

這幾項在社群 schema 內無法解決,要等上游:

- [ ] **`requires_skills:` schema 欄位** — 把 prompt 層的 PRECHECK 換成引擎驗證的宣告
- [ ] **`post_apply` phase** — 讓 `verify` / `retrospective` 變成真正的 post-apply hook,而非帶時序錯位的 artifact(對應 spec-kit 的 `after_implement`)

## 未來 bridge 候選

實際需求出現時才加:

- [ ] **`obra-bridge`** — 廣義對 obra/* 其他工具的整合(如果使用者社群成長)
- [ ] **領域特定 schema** — 例如 `data-pipeline` 變體,加強 schema validation artifact

想提議新 bridge?到 <https://github.com/JiangWay/openspec-schemas/issues> 開 issue。
