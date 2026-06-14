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
- Optional reference PDF or existing reusable rule file.

If the user has not clearly specified the version, ask:

> Which version do you want?
> 1. Final total only
> 2. Section subtotals + final total

Do not guess the version.

## Non-Negotiable Rules

- Read only customer-facing scope columns A-E for visible scope content.
- Do not expose internal costing columns F-M unless the user explicitly asks.
- Every customer-facing row with QTY or UNIT in D-E must be represented as its own visible PDF row.
- Preserve all major sections present in the source workbook.
- Preserve all Excel customer-facing summary rows when present.
- Do not drop final sections such as Signage, Others, Equipment Works, Equipment Delivery, Builder Margin, Margin, or Equipment Sub Total.
- Do not shorten the quote by deleting scope rows.
- Use compact formatting instead of deleting content.

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

- Cover page with Trinity logo top-left.
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
- Remove a duplicate note saying the quotation is based on drawings if the same drawing reference already appears on the cover under `DRAWINGS`.

## Required Validation

Before delivering:

- Confirm selected version was followed.
- Confirm all customer-facing rows from A-E are represented.
- Confirm every source row with QTY/UNIT in D-E is a visible PDF row.
- Confirm internal columns F-M are not exposed.
- Confirm final total matches Excel.
- Confirm summary rows are present when Excel contains them.
- For Version 1, confirm ordinary per-section subtotal boxes are hidden but Excel summary rows remain.
- For Version 2, confirm ordinary section subtotals and Excel summary rows both remain.
- Confirm all displayed subtotal/summary amounts include `+ GST`.
- Confirm `EQUIPMENT SUB TOTAL` is present when Excel contains `Equipment Sub Total:`.
- Confirm subtotal and total boxes align to the table right edge.
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

Examples:

- `Quotation_Fat Pomelo@Balgowlah.pdf`
- `Quotation_Kookai@Bowral.pdf`

Do not leave URL-encoded names, plus signs, or `%40` in final PDF filenames.

