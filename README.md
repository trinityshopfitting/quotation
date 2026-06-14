# Quotation

Quotation-related rules, templates, workflows, and reusable Codex guidance.

This repository is the central place for quotation work. The first module is
the quotation PDF template rule set.

## Contents

- `docs/quote-template/`: reusable quotation PDF template rules and workflow.
- `docs/pricing-rules/`: future pricing, margin, GST, and calculation rules.
- `docs/customer-templates/`: future customer-facing wording and format notes.
- `templates/`: source Excel, PDF, or design templates.
- `examples/`: sample inputs and outputs.
- `scripts/`: future automation scripts.

## Current Quote Template Module

In a new Codex thread, ask Codex to read all three quote-template docs before
generating a quote PDF:

```text
Please read:
1. docs/quote-template/quotation_pdf_versions_FINAL_reusable_rule.md
2. docs/quote-template/quotation_pdf_skill_SKILL.md
3. docs/quote-template/quotation_pdf_generation_PIPELINE.md

Then generate the quotation PDF from the provided Excel file.
Ask whether to use version 1 or version 2 unless already specified.
Run reconciliation checks and visual QA before returning the final PDF.
```

Important checks:

- Do not omit Equipment Sub Total when it exists in Excel.
- Do not omit Builder Margin when it exists in Excel.
- Do not omit Construction Sub Total when it exists in Excel.
- Keep customer-facing PDF output polished and consistent with the selected version.
