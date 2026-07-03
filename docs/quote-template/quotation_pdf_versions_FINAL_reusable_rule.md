# Quotation PDF Versions - Updated Reusable Rules

Joe's customer-facing quotation PDF has three standard price-display versions.

Before making a customer PDF from an Excel quotation, ask:

> 选哪个版本？1: 总价  2: 带 breakdown  3: 小活 breakdown

Do not assume the version unless Joe has already clearly specified it.

## Version 1: Final Total Only

Use this version when the client should not see each ordinary trade/category subtotal, but the PDF must still preserve any customer-facing summary rows that already exist in the Excel source.

Rules:

- Do not show ordinary major-section subtotals after each trade/category table.
- Hide ordinary section subtotal boxes such as:
  - `FLOORING & WALL TILE WORKS SUB TOTAL`
  - `PLASTERBOARD & SOLID WALL WORKS SUB TOTAL`
  - `PAINTING WORKS SUB TOTAL`
  - `ELECTRICAL WORKS SUB TOTAL`
  - `SIGNAGE SUB TOTAL`
  - other normal per-section subtotal boxes
- Do not hide customer-facing Excel summary rows just because Version 1 is selected.
- If Excel contains summary rows such as `Sub total:`, `10 % Builder Margin:`, `Construction Sub Total:`, or `Equipment Sub Total:`, show those rows explicitly in the PDF.
- Preserve these Excel summary rows in the same order and location as the Excel source.
- Do not merge Builder Margin, Construction Sub Total, or Equipment Sub Total into the final total only.
- Do not invent Builder Margin, Construction Sub Total, or Equipment Sub Total if they are not in the Excel source.
- After all detailed scope items and preserved Excel summary rows, show the final `TOTAL PRICE`.
- Place the final total after all detailed scope items and before final notes.
- If an `Equipment Sub Total` exists in Excel, it should usually appear before the final `TOTAL PRICE`, following the Excel order.
- All preserved summary amounts must include `+ GST` unless Joe explicitly asks otherwise.
- Use a dark, right-aligned total box.
- Format the total like `$453,200.00 + GST`.

In short:

- Version 1 hides normal section subtotal boxes.
- Version 1 does not hide real Excel summary rows.
- Version 1 still ends with the final dark `TOTAL PRICE`.

## Version 2: Section Subtotals + Final Total

Use this version when the client needs to see each major trade/category subtotal as well as the final quotation price.

Rules:

- Add a subtotal after each major section, such as flooring, plastering, painting, electrical, fire service, plumbing, stainless steel, shopfront, stone, glazing, cool room, joinery, signage, others, equipment, equipment delivery, and margin if present.
- Version 2 must show both ordinary section subtotal boxes and all customer-facing Excel summary rows when they exist.
- Do not treat Excel summary rows as duplicates of section subtotals.
- Do not hide, merge, replace, or swallow Excel summary rows such as `Sub total:`, `10 % Builder Margin:`, `Construction Sub Total:`, or `Equipment Sub Total:`.
- If Excel contains `Equipment Sub Total:`, Version 2 must show `EQUIPMENT SUB TOTAL` explicitly before `TOTAL PRICE`, following the Excel order.
- If Excel contains both `EQUIPMENT WORKS SUB TOTAL`, `EQUIPMENT DELIVERY SUB TOTAL`, and `EQUIPMENT SUB TOTAL`, Version 2 must show all of them in order. `EQUIPMENT SUB TOTAL` is not optional and is not a duplicate.
- Section subtotal boxes must be visually smaller and quieter than the final total.
- Use a light blue/grey subtotal box, right-aligned, with the label on the left and price on the right.
- Section subtotal boxes must be separate right-side boxes below the table, not full-width table rows.
- All light blue/grey subtotal boxes must align to the right edge of the main table.
- All subtotal amounts shown in light blue/grey boxes must include `+ GST`.
- Format section subtotals like `$23,910.00 + GST`.
- The final `TOTAL PRICE` remains the most visually important price.
- The final total remains in a dark, right-aligned box.
- The final total must align to the same right edge as the subtotal boxes.
- Format final total like `$453,200.00 + GST`.
- Place the final total after all section subtotals and before final notes.

## Optional Customer-Facing Breakdown Columns

Some quotes may contain a special customer-facing breakdown column for one section, such as a Joinery `BREAKDOWN PRICE` column in Excel column H.

This is optional and uncommon. Do not add a breakdown price column by default.

Rules:

- Default visible scope content is still columns A-E only.
- Add an extra breakdown column only when Joe explicitly says that Excel column is customer-facing, or the Excel header clearly identifies it as a customer-facing breakdown price column.
- Apply the extra column only to the relevant section, for example `Joinery Works`; do not add it to every trade unless the Excel source clearly has that structure for every trade.
- Preserve the Excel order of those breakdown prices.
- Do not expose unrelated internal costing columns, formulas, supplier notes, markup, or margin columns.
- If the breakdown column is a line-item breakdown, do not append `+ GST` to each breakdown cell unless Joe specifically asks for it. Keep `+ GST` on subtotal, summary, and final total boxes.
- Reconcile the displayed breakdown values against the section subtotal when possible.

## Version 3: Small Job Breakdown

Use this version only for small-scope quotations where Joe wants a clearer customer-facing breakdown and Excel contains customer-facing prices in column F.

This does not change Version 1 or Version 2.

Rules:

- Do not split every small scope item automatically.
- Only pull out a scope item as a separate breakdown price when Excel column F contains a customer-facing price for that row.
- If column F is blank for a scope item, keep that item in the normal scope table and do not invent a separate price box for it.
- Keep the visible scope order the same as Excel.
- Keep the customer-facing scope row in the table when useful, then show its column F price directly below as a light blue/grey right-aligned price box.
- If a column F priced row reads better as its own small major item, it may be shown as a separate section with its own table row and price box.
- Price boxes must align to the same right edge as the main table and final total.
- Amounts must include `+ GST` unless Joe explicitly asks otherwise.
- After all small-job breakdown items, show any ordinary section subtotal or other summary rows that are present and useful, then show the final dark `TOTAL PRICE`.
- Do not expose unrelated internal columns, supplier URLs, markup rows, or formulas.

Example:

- `Joinery Material`
  - keep the material scope rows in the table
  - show `MATERIAL COST` / `$798.00 + GST` from column F
- `Labour Cost`
  - show a table row such as `NO. 1 / AREA: Labour Cost / QTY: 1 / UNIT: day`
  - show `LABOUR COST` / `$400.00 + GST` from column F
- `Others`
  - show the related scope rows
  - show `OTHERS SUB TOTAL` / `$300.00 + GST`
- `TOTAL PRICE` / `$1,498.00 + GST`

## Preferred Customer-Facing Layout

The preferred style is clean, compact, and quotation-like rather than Excel-like.

Overall:

- Use A4 portrait pages.
- Match the reference PDF `Quotation_Kookai_Bowral.pdf` more closely than a generic quotation design.
- Use generous white space, especially on the cover.
- Use Trinity blue/dark navy for table headers and dark text.
- Use gold as an accent line only, not as a dominant background.
- Use compact typography so the quote is readable but not overly long.
- Use one consistent table body font size throughout the scope tables.
- Avoid switching body font size row by row just because a description is longer.
- Avoid copying the Excel row-by-row appearance when rows are only continuation notes.
- Do not make the document longer just because row completeness was enforced. After preserving all rows, tune font sizes, row heights, margins, and final-page flow to keep the quote compact.
- Do not lock every major section as one unbreakable block. Long scope tables should be allowed to split naturally across pages so the PDF does not create large empty areas.
- Keep only short final summary blocks together when needed, such as Builder Margin, Builder Margin Sub Total, `TOTAL PRICE`, and final notes.

Reference density:

- Page count is not fixed. It must be driven by the Excel scope content, readable row heights, notes, and page breaks.
- The reference PDF is a density/style guide, not a mandatory page-count target.
- Do not force a quote into a fixed page count if the Excel content needs more pages to stay complete and readable.
- Do not stretch a quote to extra pages through oversized spacing, loose row padding, oversized fonts, or avoidable blank areas.
- Use compact table rows and sensible continuation lines to control page count.
- Completeness is mandatory, but excessive vertical padding is not acceptable.

## Cover Page

Cover page rules:

- White clean cover.
- Place the Trinity Shopfitting logo near the top-left, not centered.
- The cover logo should sit in the upper-left area with its left edge roughly aligned to the main content margin.
- Do not place the logo at the top center.
- Preserve the logo aspect ratio. Never stretch or squash the logo by forcing arbitrary width and height.
- Calculate the logo height from the source image ratio, or use a rendering method that preserves aspect ratio.
- Render-check the cover page before delivery to confirm the logo is not distorted.
- Show the quotation date at the top-right in `DD/MM/YYYY` format, unless Joe requests another date format.
- Include the title `SHOPFITTING QUOTATION` above the project name.
- Show the project name in large bold text. If the project name has a brand and location, split it cleanly across lines.
- Place a gold horizontal underline directly below the project name.
- Add a simple project information table below the underline.
- The project information table should use horizontal divider lines, not a heavy boxed grid.
- Use these labels:
  - `CLIENT`
  - `PROJECT ADDRESS`
  - `QUOTATION DATE`
  - `DRAWINGS`
- Include the company footer at the bottom, centered, as multiple stacked lines:
  - `Trinity Shopfitting Pty Ltd`
  - `ABN: 45 625 847 305`
  - `Unit 6, 108 Percival Road, Smithfield NSW 2164`
  - `trinityshopfitting@gmail.com | www.trinityshopfitting.com.au`
- Do not put the company footer into one long single line.
- Do not put company details as a single-line header across the top of the cover.
- Do not show the old right-lower black document box.
- Do not show duplicated company address/email blocks floating near the top-left outside the logo area.

Cover positioning:

- The date must be visible at the top-right of the cover.
- The project title block should start in the left half of the page, below the logo area, similar to the reference.
- The project information table should be narrower than the full page and centered/left-aligned under the project title block, not stretched edge-to-edge.
- The gold underline should be strong and horizontal, below the project name.

## Detailed Scope Pages

Detailed scope pages should be compact and customer-facing.

## Mandatory Table QA For All Quotes

These table rules apply to every quotation and every version: Version 1, Version 2, and Version 3.

- Scope table page splits must never leave an open bottom edge. When a scope table is cut by a page break, add a bottom horizontal line to the last visible row of every page fragment.
- Scope table body row spacing must be consistent. Use the same body line-height and top/bottom padding across the same table. Rows may become taller only when the text genuinely wraps.
- These are not project-specific exceptions. They must be checked before delivering every quote PDF.

Page header/footer:

- Show the quotation date at the top-right of every detailed scope page.
- Show the company footer at the bottom of every detailed scope page, centered, as multiple stacked lines:
  - `Trinity Shopfitting Pty Ltd`
  - `ABN: 45 625 847 305`
  - `Unit 6, 108 Percival Road, Smithfield NSW 2164`
  - `trinityshopfitting@gmail.com | www.trinityshopfitting.com.au`
- Do not show the company footer as one long single line.
- Do not show the company information as a running top header.
- Page numbers go at the bottom-right and exclude the cover page, for example `1/5`, `2/5`.
- The first detailed page should show:
  - `DETAILED SCOPE`
  - `{Project Name} Quotation`
- Later detailed pages may continue directly with the table if space is needed.

Section heading style:

- Each major section has a light blue/grey horizontal title band.
- Add a gold vertical accent line at the left edge of the section title band.
- The section title band should span the table width and sit immediately above the table header.
- Leave a modest gap between sections, not a large whitespace block.
- Section titles should be human-readable, not raw Excel keys.

Human-readable section names include:

- `Flooring & Wall Tile Works`
- `Plasterboard & Solid Wall Works`
- `Painting Works`
- `Electrical Works`
- `Fire Service`
- `Plumbing Work`
- `Stainless Steel Work`
- `Shopfront Works`
- `Stone Work`
- `Glazing Work`
- `Cool Room & Freezer Room`
- `Joinery Works`
- `Signage`
- `Others`
- `Equipment Works`
- `Equipment Delivery`
- `Builder Margin`
- `Margin`

Table columns:

- Keep columns:
  - `NO.`
  - `AREA / LOCATION`
  - `DESCRIPTION / SPECIFICATION`
  - `QTY`
  - `UNIT`
- Use a dark navy table header with white uppercase text.
- Use thin light grid lines.
- Follow the Excel horizontal border/grouping logic for scope tables; do not invent odd row divisions that make the table look unlike the source.
- When a scope table splits across pages, automatically add a bottom horizontal line to the last visible row of every page fragment so no table is left open at the bottom.
- Keep rows compact.
- Use one consistent, small readable table body font size.
- Use consistent body row line-height and top/bottom padding across the same table. Rows may grow only because the content genuinely wraps; do not create random tall/short rows from inconsistent spacing.
- Avoid oversized row padding.
- Avoid large blank areas at the bottom of pages when another short section can fit.
- Do not use whole-section `KeepTogether` behavior for normal scope sections. Keep the section heading near the start of the table, but allow table rows to continue across pages.
- Right-align or center `QTY` and `UNIT`.
- Do not include the extra `Quotation notes:` explanation block at the top.
- Do not expose internal costing columns F-M unless Joe explicitly asks.
- Do not add extra price/breakdown columns to ordinary scope tables unless the source has a clearly customer-facing breakdown column or Joe explicitly asks for that column.

## Area / Location Rules

The `AREA / LOCATION` column must preserve useful customer-facing context from Excel column B.

Rules:

- If Excel column B contains useful location or drawing information, preserve it in `AREA / LOCATION`.
- If a measurable row has blank column B but clearly belongs to the previous area/location, carry forward that area/location internally for readability.
- However, do not repeat the same visible `AREA / LOCATION` value on every consecutive child row.
- Show the area/location the first time in a consecutive group, then leave following consecutive duplicate area/location cells blank.
- When the area/location changes, show the new value.
- For measurable child rows such as `CH: 3200mm`, `CH: 3600mm`, dimensions, sizes, heights, repeated finish quantities, or other sub-items with their own QTY/UNIT, use the nearest parent area/location, but only display repeated duplicates once per consecutive group.
- If Excel column B contains a drawing reference such as `A.06; A.31` or `0308; 0309`, preserve it.
- Do not concatenate too many unrelated area/location values into one cell.
- Do not move area/location text into the description if doing so makes the `AREA / LOCATION` column lose useful structure.
- Blank area/location is acceptable when it is a continuation row under the same visible area/location.

## Required Scope-Building Algorithm

When converting Excel rows into PDF rows, use this logic.

For each major section:

1. Start a new section when column A contains a major section name, such as `Flooring_Works_wall_tiles`, `Plaster_Works`, `Painting_Works`, etc.
2. Ignore the section header row itself as a scope item.
3. Read only customer-facing columns A-E for scope text.
4. For each row below the section header and before the next section:
   - If columns A-E are all blank, skip it.
   - If the row has QTY or UNIT in D-E, create a visible PDF row.
   - If the row has a new item description in C and a QTY/UNIT, create a visible PDF row even when A and B are blank.
   - For visible PDF rows, set `AREA / LOCATION` from Excel column B when present.
   - If Excel column B is blank but the row is a measurable child row under the previous visible area/location, carry forward that area/location internally.
   - If Excel column B is a drawing reference, keep it in `AREA / LOCATION` rather than burying it in the description.
   - If the row has text but no QTY/UNIT, attach it to the nearest previous PDF row only when it is clearly a note/detail for that row.
   - If attaching a note would make the previous PDF row too dense or confusing, keep the note as a separate visible row with blank QTY/UNIT.
   - If the source row in columns A-E has customer-facing formatting such as fill color, red font, or strikethrough, preserve that row as its own visible row unless Joe explicitly approves merging it. Merging styled rows often loses the customer's visual instruction.
5. After all rows in the section are represented, add the section subtotal if Version 2 is selected.

Do not:

- Do not group an entire `NO.` block into one row if that block contains multiple quantities.
- Do not group an entire area/location into one row if that area contains multiple quantities.
- Do not group an entire section into one row.
- Do not discard continuation rows just because they have blank QTY/UNIT.
- Do not discard rows near a page break.
- Do not drop later rows of a long section to make the page count match an example.

Safe consolidation:

- It is safe to combine finish/specification note rows such as `Name:`, `Colour:`, `Code:`, `Finish:`, `Size:`, or `Supply by client` into the previous item only when those rows have no QTY/UNIT of their own.
- It is safe to combine drawing/dimension rows into the previous item only when they have no QTY/UNIT of their own and are clearly descriptive.
- It is not safe to combine rows when D-E contain measurable values.
- When consolidating notes, preserve the visible area/location structure of measurable rows.

## Excel Summary Rows / Builder Margin / Equipment Subtotal

Not every quotation has Builder Margin, Construction Sub Total, Equipment Works, Equipment Delivery, or Equipment Sub Total.

The rule is not to force these rows into every PDF. The rule is:

- If Excel has a customer-facing summary row, preserve it.
- Keep summary rows in the same order as Excel.
- Do not move summary rows to a different part of the quote unless Joe explicitly asks.
- Do not hide, merge away, or swallow these rows inside another total.
- Do not invent summary rows that are not in the Excel source.
- This rule applies to both Version 1 and Version 2.
- Version 1 hides ordinary per-section subtotals, but it still preserves these Excel summary rows.
- Version 2 shows ordinary per-section subtotals and also preserves these Excel summary rows.

Common summary rows that may appear:

- `Sub total:`
- `10 % Builder Margin:`
- `Construction Sub Total:`
- `Equipment Sub Total:`
- Other customer-facing subtotal/summary rows in columns A-E

Rules:

- If Excel shows `10 % Builder Margin`, show it explicitly.
- If Excel shows `Construction Sub Total`, show it explicitly.
- If Excel shows `Equipment Sub Total`, show it explicitly.
- In Version 1, do not treat these rows as optional section subtotals. They are Excel summary rows and must remain visible.
- In Version 1, ordinary section subtotal boxes are hidden, but the following summary block must still remain visible if present:
  - `SUB TOTAL`
  - `10% BUILDER MARGIN`
  - `CONSTRUCTION SUB TOTAL`
  - `EQUIPMENT SUB TOTAL`
- If these rows appear between construction scope and equipment scope in Excel, keep them there in the PDF.
- If these rows appear somewhere else in a different Excel quotation, keep that Excel order instead.
- Style related consecutive summary rows as a compact right-aligned summary block.
- Regular summary rows may use light blue/grey rows.
- A major summary such as `Construction Sub Total` may be visually stronger, using a dark navy row similar to the final total but smaller/lower hierarchy.
- Summary amounts shown to the customer must include `+ GST` unless Joe explicitly asks otherwise.
- Format examples:
  - `SUB TOTAL` / `$889,981.82 + GST`
  - `10% BUILDER MARGIN` / `$88,998.18 + GST`
  - `CONSTRUCTION SUB TOTAL` / `$978,980.00 + GST`
  - `EQUIPMENT SUB TOTAL` / `$99,082.30 + GST`
- If there is an `Equipment Delivery` section, preserve it in the same order as Excel.
- If there is a second Excel `Others` section used only for equipment delivery, it may be renamed customer-facing as `Equipment Delivery`, but its position must still follow the Excel order.
- If `Builder Margin` or `Margin` appears as a short final section, do not split the Builder Margin heading, rows, subtotal, `TOTAL PRICE`, and notes awkwardly across pages. Keep that final block together when it fits.

## Subtotal And Total Alignment

This is mandatory for polish.

- Every light blue/grey subtotal box must align to the right edge of the main table.
- Every construction summary box must align to the right edge of the main table.
- `EQUIPMENT SUB TOTAL` must align to the same right edge.
- The final dark navy `TOTAL PRICE` box must align to the same right edge as all subtotal boxes.
- Amount text inside subtotal boxes must be right-aligned.
- Do not let subtotal or total boxes protrude beyond the right edge of the table.
- Do not rely only on visual guesswork. Before delivery, render the relevant pages and visually confirm:
  - the main table right edge
  - the light blue subtotal box right edge
  - the dark total box right edge
  all line up.
- Check at least the first detailed scope page, the construction summary page, and the final total page.

## Customer-Facing Row Consolidation

The PDF should not simply copy every Excel row as a separate PDF row.

Rules:

- Preserve customer-facing Excel content from columns A-E.
- Do not use the `NO.` column alone to decide what becomes one PDF row.
- A source row must become its own PDF row when it has a customer-facing quantity or unit in columns D-E.
- A source row must become its own PDF row when it is a separate measurable/scope item, even if column A is blank.
- A source row must become its own PDF row when column C contains a new item name and columns D-E contain that item's quantity/unit.
- Continuation/specification rows below an item may be combined into the `DESCRIPTION / SPECIFICATION` field only when they do not have their own quantity/unit and are clearly descriptive notes for the previous row.
- If a continuation row has a drawing reference or location in column B, preserve that column B content. It may become the `AREA / LOCATION` for that continuation line when it improves readability.
- Never merge two rows that have different quantities into one PDF row.
- Never merge two rows that have different units into one PDF row.
- Never merge separate supply/install items into a single row if doing so hides their individual quantities.
- If in doubt, keep more rows rather than fewer rows.
- Keep meaningful dimensions, finishes, names, codes, installation notes, lead times, exclusions, and client-supply notes.
- Remove blank-only rows.
- Do not show raw internal formulas or internal notes.
- Do not show internal supplier/costing content from columns F-M.
- Use human-readable section names instead of raw Excel names.

## Mandatory Completeness Rules

These rules are more important than compactness.

- Every major section present in the Excel customer scope must appear in the PDF.
- Every source row in columns A-E that contains customer-facing scope text must be represented in the PDF.
- Every source row in columns A-E with a quantity or unit must be represented as a visible PDF row with that same quantity and unit.
- Every numbered item from the Excel customer scope must appear.
- If a section continues across pages, continue it; do not drop remaining rows to make the PDF shorter.
- Signage, Others, Equipment, Equipment Delivery, Margin, and other short final sections must still appear in full before `TOTAL PRICE`.
- The final PDF may be longer if needed. Do not reduce page count by deleting or over-merging scope.
- Compactness is secondary to accuracy and completeness.

Required validation before delivery:

- Count the nonblank customer-facing source rows in columns A-E by section.
- Count the represented PDF rows/items by section.
- For each section, confirm no source row with QTY/UNIT was lost.
- Search the PDF text for every section title from the source.
- Search the PDF text for the last item in each section to confirm page continuation did not drop it.
- Specifically confirm commonly missed final sections are present when they exist:
  - `Joinery Works`
  - `Signage`
  - `Others`
  - `Equipment Works`
  - `Equipment Delivery`
  - `Builder Margin`
  - `Margin`
- Do not deliver the PDF if any section has fewer PDF QTY/UNIT rows than source QTY/UNIT rows unless Joe explicitly approved a manual omission.
- Do not deliver the PDF if a long section's last source item cannot be found in the PDF text.

## Excel Formatting / Highlight Rules

Preserve customer-facing formatting from Excel columns A-E. Do not only look for yellow fills.

Required source formatting to scan:

- cell fill colors, including yellow, light blue, green, and other customer-facing highlights
- font colors, especially red text
- strikethrough text
- keyword-highlight rows

Rules:

- If Excel source cells are highlighted in customer-facing columns A-E, bring those highlights into the PDF.
- Preserve cell-level formatting where possible. Do not downgrade every styled cell into a generic whole-row yellow highlight.
- Yellow fills should remain yellow.
- Blue fills should remain blue or pale blue in the PDF.
- Green fills may be normalized to the same pale blue style when Joe asks for a consistent blue look, but they must not disappear.
- Red font must remain red in the PDF.
- Strikethrough text must remain strikethrough in the PDF.
- If a source row has special formatting in A-E, do not merge it into the previous row unless Joe explicitly approves it.
- Keyword highlights may highlight the whole PDF row when the whole row is a customer-facing warning, allowance, lead time, exclusion, or client-supply note.
- Highlight keywords include:
  - `Allowed Supplier`
  - `Allowed`
  - `Allowance`
  - `Not included`
  - `Items Not included`
  - `Client supply`
  - `Supply by client`
  - `Supply  by client`
  - `Lead time`
  - `Leadtime`
  - `Provisional sum`
- Use pale, readable highlight colors. Do not use dark fills that reduce legibility.
- Build a formatting reconciliation check before delivery:
  - count source rows/cells in A-E with fills
  - count source rows/cells in A-E with red font
  - count source rows/cells in A-E with strikethrough
  - confirm the matching PDF text/rows preserve those styles
  - do not deliver if a customer-facing highlight, red font, or strikethrough was lost

## Spelling And Typo Check

Every quotation must be checked for obvious spelling mistakes in customer-facing table text before delivery.

Rules:

- Check all visible scope table text, section labels, subtotal/summary labels, and notes.
- Automatically correct obvious spelling mistakes and common typos, especially in trade descriptions, notes, and customer-facing warnings.
- Do not change brand names, product names, material codes, finish codes, drawing references, dimensions, addresses, proper nouns, or intentional abbreviations unless the source clearly contains a typo.
- Keep technical meaning unchanged. If a correction could change scope or commercial meaning, leave it unchanged and flag it instead of guessing.
- Include spelling corrections in the reconciliation/check summary when corrections were applied.

## Final Page And Notes

Final total and notes:

- Final notes must be placed after the final total.
- Notes should be in a readable notes block with padding and proper line spacing.
- Prefer bullet points for final notes.
- Keep `Client Initial: ___________` at the end of the notes block.
- The notes block should be light/white with a subtle border or pale background, not visually heavier than the total box.
- Bullets should render as proper bullet dots (`•`), not missing-glyph boxes or control characters.
- Do not use a large `NOTES` heading unless it matches the reference style.
- The final page should be compact and balanced.
- If the last sections are short, keep their tables, subtotals, final total, and notes together where possible.
- If the last section is `Builder Margin` or `Margin`, keep that final short section with its subtotal, the final `TOTAL PRICE`, and notes when it fits.
- If notes do not fit with `Builder Margin` / `Margin` and `TOTAL PRICE`, do not let the notes block drag `Builder Margin` or `TOTAL PRICE` onto a new mostly blank page. Split the layout into two keep-together blocks: final summary block (`Builder Margin` / `Margin`, its subtotal, and `TOTAL PRICE`) first, then the notes block.
- Avoid leaving the final total alone on an otherwise empty page.
- Do not force notes onto their own separate page if they fit below `TOTAL PRICE`.
- Do not split notes across two pages. If notes cannot fit in the remaining space, move the whole notes block rather than splitting it.
- If a note says the quotation is based on drawings and the same drawing reference is already shown on the cover under `DRAWINGS`, remove that duplicate note from the final notes.

Final total style:

- The final total should be a dark navy box aligned toward the right side.
- The final total box should not span the full page width unless necessary.
- The label `TOTAL PRICE` should be on the left side of the dark box.
- The amount should be on the right side of the dark box.
- The final total box must align to the same right edge as all subtotal boxes.
- Format final total like `$453,200.00 + GST`.

## Data And Formatting Checks

Before delivering the PDF:

- Confirm the selected version was followed.
- If Version 1 is selected:
  - Confirm ordinary per-section subtotal boxes are not shown.
  - Confirm Excel summary rows are still shown when present.
  - Confirm `10% BUILDER MARGIN` is present when Excel contains `10 % Builder Margin:`.
  - Confirm `CONSTRUCTION SUB TOTAL` is present when Excel contains `Construction Sub Total:`.
  - Confirm `EQUIPMENT SUB TOTAL` is present when Excel contains `Equipment Sub Total:`.
  - Confirm these preserved summary rows include `+ GST`.
  - Confirm the final `TOTAL PRICE` still appears after the preserved summary rows and before final notes.
- If Version 2 is selected:
  - Confirm ordinary per-section subtotal boxes are shown after each major section when present.
  - Confirm Excel summary rows are also shown when present.
  - Confirm any optional extra breakdown column is shown only when the Excel source/user request makes it customer-facing, and only for the relevant section.
  - Confirm optional line-item breakdown prices do not show `+ GST` unless Joe requested it.
- If Version 3 is selected:
  - Confirm the quote is a small-scope quote or Joe explicitly requested small-job breakdown.
  - Confirm only rows with customer-facing prices in Excel column F were pulled out as separate breakdown price boxes.
  - Confirm rows with blank column F were not given invented price boxes.
  - Confirm pulled-out column F prices remain in Excel order.
  - Confirm pulled-out column F prices reconcile with section subtotals and final total.
  - Confirm the actual PDF filename Joe will open was rendered and visually checked.
- Confirm all customer-facing rows from columns A-E are represented, either as table rows or consolidated descriptions.
- Confirm every source row with a nonblank QTY or UNIT in columns D-E appears as a separate visible row in the PDF.
- Confirm internal columns F-M are not exposed.
- Confirm section subtotals match the Excel major-section totals when using Version 2.
- Confirm visible table text was checked for obvious spelling mistakes and corrected where safe.
- Confirm all light blue/grey subtotal boxes include `+ GST`.
- Confirm construction summary rows include `+ GST`.
- Confirm equipment subtotal includes `+ GST` when present.
- Confirm final total matches Excel.
- Confirm `TOTAL PRICE` appears before final notes.
- Confirm page numbers exclude the cover page.
- Confirm the cover logo is top-left, not centered.
- Confirm the cover logo is not stretched or squashed.
- Confirm the cover date appears at top-right.
- Confirm the footer is centered and stacked on multiple lines, not one long line.
- Confirm detailed pages do not use a one-line company header at the top.
- Confirm section subtotal boxes are right-aligned compact boxes, not full-width rows.
- Confirm subtotal boxes and the final total box align to the main table's right edge.
- Confirm scope table horizontal lines follow the Excel grouping and every page-split table fragment has a closed bottom line.
- Confirm scope table body rows use consistent line-height and padding; avoid uneven row heights except where longer wrapped content requires it.
- Confirm measurable child rows with blank Excel column B inherit the nearest appropriate parent area/location internally, while repeated visible area/location values are not duplicated unnecessarily.
- Confirm final total/notes are not stranded alone on a mostly blank last page when final short sections could fit there.
- Confirm normal scope sections are not over-protected with whole-section keep-together behavior that creates mostly blank pages.
- Confirm final short sections, especially Builder Margin or Margin, are not split awkwardly from their subtotal, `TOTAL PRICE`, or notes.
- Confirm notes did not drag Builder Margin or `TOTAL PRICE` onto a new page when those final summary items could fit on the previous page.
- Confirm proper bullets render in notes.
- Confirm the cover does not show the old black document box.
- Confirm highlighted Excel rows and keyword rows are highlighted in the PDF.
- Confirm all customer-facing Excel styles from A-E are preserved in the PDF:
  - yellow fills
  - blue fills
  - green fills normalized to blue if requested
  - red font
  - strikethrough
- Visually inspect at least:
  - cover
  - first detailed scope page
  - a page with normal section subtotal boxes
  - construction summary page if present
  - equipment subtotal / final total page
  - final total/notes page

Minimum reconciliation report:

- For each section, list:
  - source rows with QTY/UNIT count
  - PDF rows with QTY/UNIT count
  - section subtotal
  - missing-item check result
- Do not deliver the PDF if any section has fewer PDF QTY/UNIT rows than source QTY/UNIT rows unless Joe explicitly approved a manual omission.
- Do not deliver the PDF if a long section's last source item cannot be found in the PDF text.

## File Naming

For final customer PDF files, use Joe's preferred readable naming style:

- `Quotation_{Project Brand}@{Location}.pdf`

Examples:

- `Quotation_Fat Pomelo@Balgowlah.pdf`
- `Quotation_Kookai@Bowral.pdf`

Use spaces in the brand name when appropriate. Do not leave URL-encoded names, plus signs, or `%40` in the final PDF filename.
