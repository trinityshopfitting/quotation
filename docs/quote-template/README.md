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

Ask me: `选哪个版本？1: 总价  2: 带 breakdown  3: 小活 breakdown`
unless I already specified it.
After generating the PDF, run reconciliation checks and visual QA.
Do not omit Equipment Sub Total or Builder Margin when they exist in the Excel source. Preserve Construction Sub Total in Version 1, but do not display it in Version 2; still use it for reconciliation.
In Version 2, hide only the exact `Construction Sub Total` row. Keep ordinary `Sub Total`, `10% Margin` / `10% Builder Margin`, and every other customer-facing Excel summary row in Excel order.
For breakdown prices, use the verified customer-facing sell-price cells, not hidden internal cost totals. Reconcile section prices to the source subtotal and final total, and never allow an empty expected-summary list to pass QA when summary labels exist in Excel.
For small jobs using version 3, only pull out customer-facing prices that exist in Excel column F.
```
