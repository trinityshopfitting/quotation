# Quotation PDF Generation Pipeline

Use this pipeline every time an Excel quotation is converted into a customer-facing PDF.

## 1. Intake

Collect:

- Excel source workbook path.
- Requested version:
  - `1` = final total only, while preserving Excel summary rows.
  - `2` = ordinary section subtotals plus final total, while preserving Excel summary rows.
- Any reference PDF or reusable rule file.

If the version is not specified, ask before generating.

## 2. Workbook Inspection

Open the workbook and identify:

- Active quotation sheet.
- Project name.
- Client name.
- Project address.
- Quotation date.
- Drawing reference.
- Final `TOTAL PRICE`.
- Final notes.
- Embedded logo if present.
- Major section headers.
- Ordinary section subtotal values.
- Excel customer-facing summary rows.

Important summary rows to detect:

- `Sub total:`
- `10 % Builder Margin:`
- `Construction Sub Total:`
- `Equipment Sub Total:`
- any other customer-facing subtotal/summary row in columns A-E

Do not assume these rows exist in every workbook.

## 3. Parse Customer Scope

For each major section:

1. Start the section at the Excel section header.
2. Read only columns A-E for visible customer-facing scope.
3. Do not expose columns F-M.
4. Skip blank-only rows.
5. Create a visible PDF row for every row with QTY or UNIT in D-E.
6. Create a visible PDF row for each separate measurable item, even if A or B is blank.
7. Combine continuation/specification notes into the previous row only when they have no QTY/UNIT and are clearly descriptive.
8. Never merge two rows that have different quantities or units.
9. Preserve highlighted rows and keyword-highlight rows.

Keyword highlight examples:

- `Allowed Supplier`
- `Allowed`
- `Allowance`
- `Not included`
- `Items Not included`
- `Client supply`
- `Supply by client`
- `Lead time`
- `Leadtime`
- `Provisional sum`

## 4. Area / Location Handling

For column B:

- Preserve useful area/location/drawing information.
- If a measurable child row has blank column B, carry forward the nearest parent area/location internally.
- Display a repeated consecutive area/location only once.
- Leave following duplicate area/location cells blank until the area changes.
- Keep drawing references in `AREA / LOCATION`.

## 5. Version Logic

### Version 1

Show:

- all detailed scope rows
- Excel customer-facing summary rows when present
- final dark `TOTAL PRICE`
- notes

Hide:

- ordinary per-section subtotal boxes

Must preserve if present:

- `SUB TOTAL`
- `10% BUILDER MARGIN`
- `CONSTRUCTION SUB TOTAL`
- `EQUIPMENT SUB TOTAL`

### Version 2

Show:

- all detailed scope rows
- ordinary section subtotal boxes after each major section when applicable
- all Excel customer-facing summary rows when present
- final dark `TOTAL PRICE`
- notes

Mandatory:

- If Excel has `Equipment Sub Total:`, show `EQUIPMENT SUB TOTAL`.
- If Excel has `Equipment Works`, `Equipment Delivery`, and `Equipment Sub Total`, show all three in Excel order.
- Do not treat `Equipment Sub Total` as a duplicate of `Equipment Works Sub Total` or `Equipment Delivery Sub Total`.

## 6. Build The PDF

Create:

- A4 portrait PDF.
- Cover page.
- Detailed scope pages.
- Final total and notes.

Cover:

- Trinity logo top-left.
- Date top-right.
- `SHOPFITTING QUOTATION`.
- Large project name.
- Gold underline.
- Project info table:
  - `CLIENT`
  - `PROJECT ADDRESS`
  - `QUOTATION DATE`
  - `DRAWINGS`
- Centered stacked footer.

Detailed pages:

- Date top-right.
- Centered stacked footer.
- Page number bottom-right excluding cover.
- First detailed page has `DETAILED SCOPE` and `{Project Name} Quotation`.
- Section title band above each table.
- Table columns:
  - `NO.`
  - `AREA / LOCATION`
  - `DESCRIPTION / SPECIFICATION`
  - `QTY`
  - `UNIT`

## 7. Price Box Styling

Use:

- Light blue/grey compact right-aligned boxes for ordinary section subtotals and regular summary rows.
- A stronger dark navy row for major construction subtotal if useful.
- Dark navy compact right-aligned box for final `TOTAL PRICE`.

All displayed subtotal/summary/final amounts should include `+ GST` unless the user explicitly asks otherwise.

All price boxes must align to the main table right edge:

- ordinary section subtotals
- construction summary block
- `EQUIPMENT SUB TOTAL`
- `TOTAL PRICE`

## 8. Notes

After `TOTAL PRICE`, add notes:

- Use bullet points.
- Keep `Client Initial: ___________`.
- Remove duplicate drawing-basis note if the drawing reference already appears on the cover.

## 9. Reconciliation Checks

Produce or perform a reconciliation check:

- List each section.
- Count source rows with QTY/UNIT.
- Count PDF rows with QTY/UNIT.
- Confirm no section has fewer PDF QTY/UNIT rows than source QTY/UNIT rows.
- Confirm the last item in each section appears in the PDF.
- Confirm all source major sections appear.
- Confirm all required summary rows appear when present in Excel.

Reject the PDF and fix it if:

- A QTY/UNIT row is missing.
- A section is missing.
- A source summary row is missing.
- Internal columns F-M appear.
- `TOTAL PRICE` is wrong.
- `EQUIPMENT SUB TOTAL` is missing when Excel contains it.

## 10. Visual QA

Render or preview the PDF before delivery.

Inspect at least:

- cover page
- first detailed scope page
- one ordinary section subtotal page
- construction summary page if present
- equipment subtotal/final total page
- notes page

Check:

- no subtotal box protrudes beyond the table right edge
- all subtotal boxes align with the table right edge
- final `TOTAL PRICE` aligns with the same right edge
- body font size is consistent
- area/location duplicates are not repeated unnecessarily
- notes are readable and not awkwardly split if avoidable
- final total is not stranded on a mostly blank page if it can be avoided

## 11. Output Files

Save:

- final customer PDF
- optional reconciliation JSON/report
- optional rendered preview images for QA

Final PDF naming:

- `Quotation_{Project Brand}@{Location}.pdf`

Examples:

- `Quotation_Fat Pomelo@Balgowlah.pdf`
- `Quotation_Kookai@Bowral.pdf`

Do not use URL-encoded filenames, plus signs, or `%40`.

## 12. Delivery Response

When handing back the result, mention:

- final PDF path
- version used
- whether summary rows were preserved
- whether visual QA and reconciliation checks passed

