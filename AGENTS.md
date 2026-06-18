# AGENTS.md

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
