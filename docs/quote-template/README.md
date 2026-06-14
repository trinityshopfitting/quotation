# Quote Template

Reusable quotation PDF template rules from the Codex thread `读取这个规则`.

## Files

- `quotation_pdf_versions_FINAL_reusable_rule.md`: final reusable PDF layout and content rules.
- `quotation_pdf_skill_SKILL.md`: Codex/AI skill instructions for generating quote PDFs.
- `quotation_pdf_generation_PIPELINE.md`: execution and QA pipeline for turning Excel quotation data into customer PDF output.

## How To Use

Ask Codex to read all three files before generating a quotation PDF.

```text
Please read these three files and strictly follow them to generate a quotation PDF:
1. docs/quote-template/quotation_pdf_versions_FINAL_reusable_rule.md
2. docs/quote-template/quotation_pdf_skill_SKILL.md
3. docs/quote-template/quotation_pdf_generation_PIPELINE.md

Ask me whether to use version 1 or version 2 unless I already specified it.
After generating the PDF, run reconciliation checks and visual QA.
Do not omit Equipment Sub Total, Builder Margin, or Construction Sub Total when they exist in the Excel source.
```

