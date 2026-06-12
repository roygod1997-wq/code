# THE ICON EDIT V3 - CODEX HANDOFF

Status: CORRECTED BUILD COMPLETED AND VALIDATED.

Use V3 only. V1 and V2 are rejected.

## Completed artifact

- File: `THE_ICON_EDIT_V3_APPROVED_2026-06-11_SELL_READY.zip`
- Approval batch date: June 11, 2026
- SHA-256: `cab64c4b8c11563e12074bcbb6a1e995283c58f12a181c06d01b70d9329b904c`
- Binary status: not committed to this public repository

The earlier build made from `THE_ICON_EDIT_CUSTOMER_PACKET` is superseded and must not be used.

## Approved source boundaries

- Reset-QA products 1-50: PASS 50/50
- Additional reset-QA products: PASS 20/20
- `BATCH05_V8_COMPLETE_EVERY_SELL_READY_ASSET`: 42 SELL READY inventory rows
- Standalone cupcake cutout and favor-bag ledger: PASS 40/40

Excluded:

- `THE_ICON_EDIT_CUSTOMER_PACKET`
- incomplete `BATCH05_V8_COMPLETED_SELL_READY`
- `_work`
- `BATCH05_V8_WORK`
- V1 and V2 scaffold packets

## V3 control counts

- Manifest rows: 186
- PDF scaffold pages: 105
- Transparent PNG / no-shell rows: 81
- Guide pages: 10
- Pro-print native-size rows: 42
- US Letter print-at-home rows: 53

## Final build result

- Physical customer files: 98
- Native pro-print PDFs: 19
- US Letter print-at-home PDFs: 46
- Physical transparent PNG files: 33
- Transparent PNG manifest rows satisfied: 41, including 8 aggregate index rows
- Rows rejected for no exact approved source: 86
- PDF size failures: 0
- PNG transparency or DPI failures: 0
- Missing audited outputs: 0
- Scaffold/drop-zone/placeholder filename hits: 0
- Independent validation: PASS

Rejected rows were not replaced with similar designs. They remain rejected until an exact approved source at the required V3 product, size, and output type is supplied.

## Non-negotiable rules

1. No child names, personalization fields, or placeholders.
2. Do not force native products into US Letter.
3. Preserve native trim and 0.125-inch bleed for pro-print files.
4. Keep print-at-home sheets at US Letter and 300 DPI.
5. Transparent PNG assets require real transparency and no PDF shell.
6. Cupcake and dessert assets are cutouts, not toppers.
7. Do not force two-inch circles unless the approved source is already circular.
8. Do not export scaffold labels, drop zones, technical guides, or placeholder text.
9. Use exact approved sources only. No generated images, mockups, tracing, redesign, or close-enough substitutions.

## Repository records

- `THE_ICON_EDIT_V3_APPROVED_BUILD_COMPLETION.md`
- `THE_ICON_EDIT_V3_FINAL_VALIDATION.json`
- `THE_ICON_EDIT_V3_ZIP_SHA256.txt`

The full ZIP and unsanitized provenance map remain outside this public repository because the audit contains local filesystem paths and the ZIP is a large binary customer deliverable.