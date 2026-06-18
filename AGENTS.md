# AGENTS.md

## Repository Startup Rule

Before working in this repository, Codex must first read the global rules from:

https://github.com/trinityshopfitting/codex-workspace-rules

Read these files in order:

1. `AGENTS.md`
2. `00_全局工作台.md`
3. `02_当前执行规则摘要.md`

Only after reading this startup rule and the global rules may Codex continue with the rest of this repository's own Markdown files, including this `AGENTS.md`, `README.md`, docs, package files, source code, and project-specific instructions.

## Repository Purpose

This repository stores quotation-related documentation, templates, workflows,
and reusable Codex guidance.

## Working Rules

- Reply in Chinese by default unless the work requires English.
- Keep quote-template rules under `docs/quote-template/`.
- Put pricing, margin, GST, and calculation rules under `docs/pricing-rules/`.
- Put customer-facing wording and format notes under `docs/customer-templates/`.
- Before generating quotation PDFs, read the three quote-template documents under `docs/quote-template/`.
- Preserve the difference between version 1 and version 2 output.
- Always run reconciliation checks against the source Excel data.
- Always perform visual QA on generated PDFs before considering the task complete.
- Never omit Equipment Sub Total, Builder Margin, or Construction Sub Total when present in the source Excel.
- Keep credentials, private customer data, and raw local Codex state out of Git.
