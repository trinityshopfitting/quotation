# Quotation PDF Skill

Use this skill when converting Trinity Shopfitting Excel quotation workbooks into customer-facing quotation PDFs.

## Goal

Create a polished customer-facing PDF quotation from an Excel source workbook without exposing internal costing data and without losing any customer-facing scope, subtotal, builder margin, equipment subtotal, or final total information.

## Inputs

Expected user inputs:

- Source Excel quotation file, usually `.xlsx`.
- Desired version:
  - `1` = final total only, but preserve Excel summary rows.
  - `2` = ordinary section subtotals plus final total, and preserve Excel summary rows.
  - `3` = small job breakdown, using customer-facing column F prices only when present.
- Optional reference PDF or existing reusable rule file.

If the user has not clearly specified the version, ask:

> 选哪个版本？1: 总价  2: 带 breakdown  3: 小活 breakdown

Do not guess the version.

## Non-Negotiable Rules

- Read only customer-facing scope columns A-E for visible scope content.
- Do not expose internal costing columns F-M unless the user explicitly asks.
- Extra price/breakdown columns are not default, but every workbook must be scanned for them during inspection, especially inside `Joinery Works`.
- Add an optional breakdown column when the user explicitly says it is customer-facing, when the Excel header clearly identifies it as a customer-facing breakdown price column, or when a dedicated line-item price column reconciles to the section subtotal.
- If `Joinery Works` contains customer-facing line-item breakdown prices, such as a `BREAKDOWN PRICE` / Excel column H breakdown in Kookai quotes, the PDF must show a `BREAKDOWN PRICE` column in the Joinery table.
- Apply an optional breakdown column only to the relevant section, such as Joinery, not to every quote or every section.
- Do not append `+ GST` to optional line-item breakdown prices unless the user asks; keep `+ GST` on subtotals, summary rows, and final total.
- Every customer-facing row with QTY or UNIT in D-E must be represented as its own visible PDF row.
- Preserve all major sections present in the source workbook.
- Preserve all Excel customer-facing summary rows when present.
- Do not drop final sections such as Signage, Others, Equipment Works, Equipment Delivery, Builder Margin, Margin, or Equipment Sub Total.
- Do not shorten the quote by deleting scope rows.
- Use compact formatting instead of deleting content.
- Preserve customer-facing Excel formatting from columns A-E, including highlights, red font, and strikethrough.
- Do not merge styled rows into other rows unless Joe explicitly approves it.
- Do not use whole-section keep-together behavior for normal scope sections when it creates large blank page areas.

## Version 1 Behavior

Version 1 means the client should not see ordinary per-section subtotal boxes.

Hide ordinary section subtotal boxes such as:

- `FLOORING & WALL TILE WORKS SUB TOTAL`
- `PLASTERBOARD & SOLID WALL WORKS SUB TOTAL`
- `PAINTING WORKS SUB TOTAL`
- `ELECTRICAL WORKS SUB TOTAL`
- `SIGNAGE SUB TOTAL`
- other normal trade/category subtotals

However, Version 1 must still preserve real Excel summary rows when they exist:

- `Sub total:`
- `10 % Builder Margin:`
- `Construction Sub Total:`
- `Equipment Sub Total:`
- any other customer-facing subtotal/summary rows in columns A-E

These rows are not optional. They must stay visible, stay in Excel order, include `+ GST`, and appear before `TOTAL PRICE` when that is their Excel position.

Version 1 ends with a dark right-aligned `TOTAL PRICE` box.

## Version 2 Behavior

Version 2 means the client should see:

1. Ordinary section subtotal boxes after each major section when applicable.
2. All Excel customer-facing summary rows when present.
3. Final dark `TOTAL PRICE`.

Do not treat Excel summary rows as duplicates of ordinary section subtotals.

If Excel contains:

- `EQUIPMENT WORKS SUB TOTAL`
- `EQUIPMENT DELIVERY SUB TOTAL`
- `EQUIPMENT SUB TOTAL`
- `TOTAL PRICE`

then Version 2 must show all of them in that order. `EQUIPMENT SUB TOTAL` is required, not optional, and not a duplicate.

All light blue/grey subtotal boxes and summary rows shown to the customer must include `+ GST` unless the user explicitly asks otherwise.

## Version 3 Behavior

Version 3 is for small-scope jobs only.

Use Version 3 when the user chooses `3: 小活 breakdown` or clearly asks for the small-job breakdown style.

Rules:

- Do not change Version 1 or Version 2 behavior.
- Do not split every small scope item automatically.
- Only create a separate breakdown price box when Excel column F has a customer-facing price for that row.
- If column F is blank, keep that item in the normal scope table and do not invent a price box.
- Keep the order from Excel.
- Keep useful scope rows visible in the table.
- Show the column F price as a light blue/grey right-aligned price box directly after the related scope block.
- If a column F priced item is clearer as its own small section, create that section with its own table row and price box.
- All price boxes must include `+ GST` unless the user explicitly asks otherwise.
- Do not expose unrelated internal supplier URLs, markup rows, formulas, or non-customer columns.

Example small-job structure:

- `Joinery Material`
  - material scope rows
  - `MATERIAL COST` / `$798.00 + GST`
- `Labour Cost`
  - table row: `NO. 1 / AREA: Labour Cost / QTY: 1 / UNIT: day`
  - `LABOUR COST` / `$400.00 + GST`
- `Others`
  - related scope rows
  - `OTHERS SUB TOTAL` / `$300.00 + GST`
- `TOTAL PRICE`

## Summary Rows

Not every workbook has Builder Margin, Construction Sub Total, Equipment Works, Equipment Delivery, or Equipment Sub Total.

Rules:

- If Excel has the row, preserve it.
- If Excel does not have the row, do not invent it.
- Keep the row in the same order and relative position as Excel.
- Do not merge it into another subtotal.
- Do not hide it in Version 1 or Version 2.

Common required labels:

- `SUB TOTAL`
- `10% BUILDER MARGIN`
- `CONSTRUCTION SUB TOTAL`
- `EQUIPMENT SUB TOTAL`

## Layout

Use an A4 portrait customer-facing layout:

Mandatory table QA for every quote and every version:

- Scope table page splits must never leave an open bottom edge. When a scope table is cut by a page break, close the page fragment with a bottom horizontal line on the last visible row.
- Scope table body row spacing must be consistent. Keep the same body line-height and top/bottom padding across the same table. Rows may become taller only when text genuinely wraps.
- These checks apply to Version 1, Version 2, and Version 3.

- Cover page with Trinity logo top-left.
- Preserve the Trinity logo aspect ratio. Do not stretch or squash the logo.
- Date top-right in `DD/MM/YYYY`.
- Large project name on cover.
- Gold underline below project name.
- Project information table with `CLIENT`, `PROJECT ADDRESS`, `QUOTATION DATE`, `DRAWINGS`.
- Centered stacked company footer on all pages.
- Page numbers on detailed pages only, excluding cover.
- Detailed pages begin with `DETAILED SCOPE` and `{Project Name} Quotation`.
- Section titles use light blue/grey bands with a gold left accent line.
- Table header is dark navy with white uppercase text.
- Table columns are:
  - `NO.`
  - `AREA / LOCATION`
  - `DESCRIPTION / SPECIFICATION`
  - `QTY`
  - `UNIT`
- Use one consistent small readable table body font size.
- Keep rows compact and readable.
- Keep body row line-height and top/bottom padding consistent across the same table; rows should only become taller when the text genuinely wraps.
- Allow normal scope tables to split naturally across pages.
- Keep only short final summary blocks together when needed, such as Builder Margin, final total, and notes.
- Follow Excel horizontal borders/grouping for scope tables.
- When a scope table splits across pages, automatically add a bottom horizontal line to the last visible row of each page fragment.
- Do not leave any ordinary section subtotal stranded at the top of the next page. If a section subtotal would be orphaned, split the last few table rows earlier so the final table fragment and its subtotal stay together.
- Do not add `BREAKDOWN PRICE` or similar extra columns unless the source/user request makes that column customer-facing for that specific section.

## Customer-Facing Formatting

Excel columns A-E may contain customer-facing formatting that must remain visible in the PDF.

Preserve:

- yellow fills
- blue fills
- green fills, normalized to pale blue when Joe requests a consistent blue look
- red font
- strikethrough text
- keyword-highlight warning, allowance, exclusion, lead-time, and client-supply rows

Rules:

- Scan formatting before building the PDF.
- Preserve cell-level formatting where possible.
- Do not convert all highlighted cells into generic whole-row yellow highlights.
- Do not merge a styled source row into another row unless Joe explicitly approves it.
- Build a formatting reconciliation count and fix the PDF if a customer-facing style is missing.

## Area / Location

- Preserve useful Excel column B content.
- Carry forward the nearest parent area/location internally when measurable child rows have blank column B.
- Do not visibly repeat the same `AREA / LOCATION` value on every consecutive child row.
- Show the area/location once at the start of a consecutive group, then leave repeated child cells blank until the area changes.
- Keep drawing references such as `A.06; A.31` or `0308; 0309` in `AREA / LOCATION`.

## Subtotal And Total Alignment

All price summary boxes must align to the same right edge as the main table:

- ordinary light blue/grey section subtotals
- construction summary block
- `EQUIPMENT SUB TOTAL`
- dark `TOTAL PRICE`

Do not let subtotal or total boxes protrude beyond the right edge of the table.

Before delivery, render/check the relevant pages visually. Do not rely only on guessed widths.

## Notes

- Final notes appear after final total.
- Keep `Client Initial: ___________`.
- Use readable bullet points.
- Do not force notes onto a separate page when they fit below `TOTAL PRICE`.
- Keep the notes block together. If notes cannot fit in the remaining space, move the whole notes block rather than splitting it across two pages.
- If Builder Margin or Margin is a short final section, keep that section, its subtotal, `TOTAL PRICE`, and notes together when they fit.
- If notes do not fit with Builder Margin / Margin and `TOTAL PRICE`, split final layout into two keep-together blocks: final summary first (`Builder Margin` / `Margin`, subtotal, `TOTAL PRICE`), then notes. Do not let notes drag the final summary block onto a new mostly blank page.
- Remove a duplicate note saying the quotation is based on drawings if the same drawing reference already appears on the cover under `DRAWINGS`.

## Required Validation

Before delivering:

- Confirm selected version was followed.
- Confirm all customer-facing rows from A-E are represented.
- Confirm every source row with QTY/UNIT in D-E is a visible PDF row.
- Confirm internal columns F-M are not exposed.
- Confirm optional breakdown columns are not invented.
- Confirm every workbook was scanned for customer-facing breakdown columns, especially `Joinery Works`.
- If Joinery has a customer-facing breakdown column, confirm the PDF includes `BREAKDOWN PRICE`, all breakdown amounts are present in Excel order, and line-item values do not show `+ GST` unless requested.
- If an optional breakdown column is used, confirm it appears only in the relevant section and does not leak internal costing data.
- Check all visible table text, section labels, subtotal/summary labels, and notes for obvious spelling mistakes. Automatically correct safe typos without changing scope meaning.
- At minimum, scan for common quote typos such as `counterop`, `Shopfloor`, `paper work`, `leadtime`, `onsite inspection`, `Supply by client`, `tape ware`, and `Illuminate signage`.
- Do not treat material names, colour names, finish names, brand names, or dimensions as typos only because a dictionary does not recognize them.
- Do not change brand names, product names, material/finish codes, drawing references, dimensions, addresses, proper nouns, or intentional abbreviations unless the source clearly contains a typo.
- Log spelling corrections when applied.
- Confirm final total matches Excel.
- Confirm summary rows are present when Excel contains them.
- Confirm customer-facing formatting from A-E is preserved:
  - highlights
  - red font
  - strikethrough
- For Version 1, confirm ordinary per-section subtotal boxes are hidden but Excel summary rows remain.
- For Version 2, confirm ordinary section subtotals and Excel summary rows both remain.
- Confirm all displayed subtotal/summary amounts include `+ GST`.
- Confirm `EQUIPMENT SUB TOTAL` is present when Excel contains `Equipment Sub Total:`.
- Confirm subtotal and total boxes align to the table right edge.
- Confirm scope table horizontal lines follow Excel grouping and page-split table fragments are closed with a bottom line.
- Confirm table body row line-height and padding are consistent, with no random tall/short rows.
- Confirm the cover logo is not stretched or squashed.
- Confirm normal scope sections are not creating large blank areas because of whole-section keep-together behavior.
- Confirm Builder Margin or Margin is not split awkwardly from its subtotal, final total, or notes when it is a final short section.
- Confirm notes did not push Builder Margin / Margin and final total onto a new mostly blank page when the final summary block could fit on the previous page.
- Confirm notes are not split across two pages.
- Visually inspect at least:
  - cover
  - first detailed page
  - a normal section subtotal page
  - construction summary page if present
  - equipment subtotal/final total page
  - final notes page

## Output Naming

Use readable final filenames:

- `Quotation_{Project Brand}@{Location}.pdf`
- `Quotation_{Project Brand}@{Location}_{Scope}.pdf` when separate scope PDFs are created from one workbook.

Examples:

- `Quotation_Fat Pomelo@Balgowlah.pdf`
- `Quotation_Kookai@Bowral.pdf`
- `Quotation_Reuben Hills Cafe@Surry Hills_Roof Repairs.pdf`

Do not leave URL-encoded names, plus signs, or `%40` in final PDF filenames.

Do not include `_V1` on the first issued PDF. Add a version suffix only for later updates to the same quotation, beginning with `_V2` and continuing sequentially (`_V3`, `_V4`, and so on). Put the version suffix last, after any scope descriptor.
