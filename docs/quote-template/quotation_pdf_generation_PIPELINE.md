# Quotation PDF Generation Pipeline

Use this pipeline every time an Excel quotation is converted into a customer-facing PDF.

## 1. Intake

Collect:

- Excel source workbook path.
- Requested version:
  - `1` = final total only, while preserving Excel summary rows.
  - `2` = ordinary section subtotals plus final total, while preserving Excel summary rows.
  - `3` = small job breakdown, using customer-facing column F prices only when present.
- Any reference PDF or reusable rule file.

If the version is not specified, ask:

> 选哪个版本？1: 总价  2: 带 breakdown  3: 小活 breakdown

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
- Customer-facing cell formatting in columns A-E:
  - fill colors, including yellow, blue, green, and other highlights
  - red font or other customer-facing font colors
  - strikethrough text

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
10. Preserve customer-facing cell formatting from A-E, including fill colors, red font, and strikethrough.
11. Do not merge a styled source row into another row unless Joe explicitly approves it. Styled rows often contain customer-facing emphasis.

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

### Version 3

Use this for small-scope quotations only.

Show:

- all useful customer-facing scope rows from A-E
- a separate light blue/grey price box only when the related Excel row has a customer-facing price in column F
- any required ordinary subtotal or summary rows
- final dark `TOTAL PRICE`
- notes

Mandatory:

- Do not split every small scope item automatically.
- Do not invent price boxes for rows with blank F.
- Keep Excel order.
- If a column F priced item is clearer as its own major item, create a small section for it.
- For a small labour breakdown, use a table row like `NO. 1 / AREA: Labour Cost / QTY: 1 / UNIT: day` when that matches the customer-facing scope.
- Price boxes must include `+ GST`.
- Verify that pulled-out column F prices reconcile with subtotals and final total.

## 6. Build The PDF

Create:

- A4 portrait PDF.
- Cover page.
- Detailed scope pages.
- Final total and notes.

Cover:

- Trinity logo top-left.
- Preserve the Trinity logo aspect ratio. Calculate image height from the source ratio or use an image method that does not stretch the logo.
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
- Allow normal scope tables to split naturally across pages.
- Do not wrap entire ordinary sections in one unbreakable keep-together block, because that creates large blank page areas.
- Keep only short final summary blocks together when needed, such as Builder Margin, final total, and notes.
- Preserve Excel cell formatting in the table body:
  - yellow highlights stay yellow
  - blue highlights stay blue or pale blue
  - green highlights may be normalized to pale blue when Joe wants a consistent blue look
  - red font stays red
  - strikethrough stays strikethrough

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
- Do not force notes onto a separate page when they fit below `TOTAL PRICE`.
- Keep the notes block together. If notes cannot fit in the remaining space, move the whole notes block rather than splitting it across two pages.
- If Builder Margin or Margin is the final short section, keep the section, its subtotal, `TOTAL PRICE`, and notes together when they fit.

## 9. Reconciliation Checks

Produce or perform a reconciliation check:

- List each section.
- Count source rows with QTY/UNIT.
- Count PDF rows with QTY/UNIT.
- Confirm no section has fewer PDF QTY/UNIT rows than source QTY/UNIT rows.
- Confirm the last item in each section appears in the PDF.
- Confirm all source major sections appear.
- Confirm all required summary rows appear when present in Excel.
- Confirm customer-facing styles from A-E are preserved:
  - highlighted fills
  - red font
  - strikethrough
- Count source rows/cells with special formatting and compare against the rendered PDF text/rows.

Reject the PDF and fix it if:

- A QTY/UNIT row is missing.
- A section is missing.
- A source summary row is missing.
- Internal columns F-M appear.
- `TOTAL PRICE` is wrong.
- `EQUIPMENT SUB TOTAL` is missing when Excel contains it.
- a customer-facing highlight, red font, or strikethrough from A-E is missing.
- the cover logo is visibly stretched or squashed.

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

- cover logo is not stretched or squashed
- no subtotal box protrudes beyond the table right edge
- all subtotal boxes align with the table right edge
- final `TOTAL PRICE` aligns with the same right edge
- body font size is consistent
- yellow/blue/green highlights, red font, and strikethrough from Excel are visible in the PDF
- area/location duplicates are not repeated unnecessarily
- notes are readable and not split across two pages
- final total is not stranded on a mostly blank page if it can be avoided
- normal sections are not creating large blank areas because of whole-section keep-together behavior
- Builder Margin or Margin, when it is a final short section, is not split awkwardly from its subtotal, final total, or notes

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
