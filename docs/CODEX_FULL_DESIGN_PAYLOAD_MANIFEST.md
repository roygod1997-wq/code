# CROW & CROWN — Full Design Payload Manifest for Codex

Date: 2026-06-19  
Purpose: prevent Codex from launching product shells without the actual designs.

## Core rule

Codex must not create saleable Shopify or Printful products from product names alone. Every product must be backed by the full final design payload:

1. Customer-download ZIP or PDF package.
2. Print-ready production file(s).
3. Listing/hero images.
4. Source/design audit notes.
5. QA proof that files open and match the intended product.

If the final design payload is missing, corrupt, placeholder-only, outdated, or visually rejected, keep the Shopify product in `DRAFT` and mark it `BLOCKED_DESIGN_PAYLOAD_MISSING`.

## Full design payload structure

Codex should expect or create this asset structure before publishing:

```text
/assets/crow-crown/
  icon-edit/
    customer-downloads/
      THE_ICON_EDIT_COMPLETE_EXHIBITION_ARCHIVE.zip
      THE_ICON_EDIT_INVITATION_ATELIER.zip
      THE_ICON_EDIT_SIGNAGE_GALLERY.zip
      THE_ICON_EDIT_FAVOR_LABEL_ARCHIVE.zip
    source-print-pdfs/
      icon-edit-full-print-ready-master.pdf
      icon-edit-invitation-suite-print-ready.pdf
      icon-edit-signage-gallery-print-ready.pdf
      icon-edit-favor-label-archive-print-ready.pdf
    printful-ready/
      welcome-sign-18x24.pdf
      gallery-welcome-sign-24x36.pdf
      photo-booth-backdrop-36x24.pdf
    listing-images/
      hero/
      product-pages/
      thumbnails/
    qa/
      file-open-report.json
      dimension-report.json
      visual-approval-notes.md

  court-canvas/
    customer-downloads/
      THE_COURT_IS_MY_CANVAS_COMPLETE_ART_COURT_ARCHIVE.zip
      THE_COURT_IS_MY_CANVAS_INVITATION_SET.zip
      THE_COURT_IS_MY_CANVAS_SIGNAGE_SET.zip
      THE_COURT_IS_MY_CANVAS_FAVOR_LABEL_SET.zip
    source-print-pdfs/
      court-canvas-polished-print-rebuild.pdf
      court-canvas-correction-pages.pdf
      court-canvas-customer-print-cut-fold-templates.pdf
    printful-ready/
      welcome-sign-18x24.pdf
      court-backdrop-36x24.pdf
    listing-images/
      hero/
      product-pages/
      thumbnails/
    qa/
      file-open-report.json
      dimension-report.json
      visual-approval-notes.md
```

## Located design references

These are known current/near-current design files that Codex or the operator must resolve into the asset structure above.

### THE ICON EDIT

Use current full print-ready files and not old placeholders.

Candidate design files located in Drive/File Library:

- `CROW_CROWN_THE_ICON_EDIT_FULL_PRINT_READY_US_LETTER.pdf`
- `CROW_CROWN_ICON_EDIT_POLISHED_1UP_300DPI_CLEAN_SHELL.pdf`
- `CROW_CROWN_ICON_EDIT_REAL_MASTER_PAGES_REBUILT_CLEAN_1UP_300DPI.pdf`
- `THE_ICON_EDIT_PRINTABLE_MEGA_BUNDLE_45_CUSTOMER_PACKAGE.pdf`
- `THE_ICON_EDIT_BASICS_PRINTABLE_PACK_25_CUSTOMER_PACKAGE.pdf`
- `THE_ICON_EDIT_EVENT_SIGNS_CURATED_COLOR_SHAPE_SET_CORRECTED_US_LETTER_1UP_PRINTABLE.pdf`
- `CROW_CROWN_ICON_EDIT_MASTER_PAGES_16_24_REMOVED_USLETTER_1UP_PDFX1A_2001_FOGRA39L.pdf`

Known invitation-suite contents include:

- Icon Gala Invitation — Coily
- Icon Gala Invitation — Messy Bun
- Access Confirmation RSVP
- Details Card
- VIP Access Ticket — Coily
- VIP Access Ticket — Messy Bun

Keep both hair versions wherever the muse is used.

### THE COURT IS MY CANVAS

Use the corrected files, not older broken pages.

Candidate design files located in Drive/File Library:

- `THE_COURT_IS_MY_CANVAS_POLISHED_PRINT_REBUILD.pdf`
- `THE_COURT_IS_MY_CANVAS_TARGETED_CORRECTION_V2.pdf`
- `00_ALL_CUSTOMER_PRINT_CUT_FOLD_TEMPLATES_PRO_REBUILD_CLEAN_SELL_READY.pdf`
- `THE_COURT_PAGE_13_WHITE_BASKETBALL_CORRECTION_V4.pdf`
- replacement page files for pages 01, 02, 07, 08, 09, 10, 13, 14, 15, 19, 21, 22

Known Court contents include:

- Halftime Bites tent card
- Courtside Sip water bottle labels
- Dribble/Create/Shine signs
- Canvas Play basketball toppers
- Court 01 round toppers
- Court Crew credential tags
- All-Star Artist credential tags
- Paint + Play station signs
- Court photo moment signs

## Product-to-design mapping

| Shopify product | Required design payload |
|---|---|
| THE ICON EDIT — Complete Exhibition Archive | Full Icon Edit customer archive ZIP + full print-ready master + listing images |
| THE ICON EDIT — Invitation Atelier | Invitation suite ZIP/PDF with both muse hair versions + listing images |
| THE ICON EDIT — Signage Gallery | Signage set ZIP/PDF + listing images |
| THE ICON EDIT — Favor & Label Archive | Favor, label, tag, topper, wrap ZIP/PDF + listing images |
| THE COURT IS MY CANVAS — Complete Art Court Archive | Full Court customer archive ZIP + polished/replacement corrected PDFs + listing images |
| THE COURT IS MY CANVAS — Invitation Set | Court invitation/download package + listing images |
| THE COURT IS MY CANVAS — Signage Set | Court signage ZIP/PDF + corrected pages + listing images |
| THE COURT IS MY CANVAS — Favor & Label Set | Court favors, labels, toppers, tags ZIP/PDF + corrected pages + listing images |
| Printful physical products | Printful-template-sized PDFs/PNGs generated from approved designs only |

## Codex execution rules

1. Build scripts may create products, but products stay in `DRAFT` until design assets are present and verified.
2. The file validator must check:
   - file exists,
   - opens without error,
   - not zero bytes,
   - not placeholder-only,
   - PDF page count matches expected product scope,
   - image dimensions meet listing requirements,
   - physical Printful files match exact Printful print area.
3. Any file containing `UNCORRECTED`, `BACKUP`, `PLACEHOLDER`, `DROP-IN`, `SOURCE REQUIRED`, or `PROOF ONLY` in the filename or visible text must be blocked unless explicitly whitelisted.
4. Old `Mega Bundle` and `Basics Pack` files may be used only as source candidates to rebuild the new premium package names. The storefront must use the new premium names.
5. Do not publish from File Library references alone. Copy the final approved files into the Codex-accessible asset folder or Drive folder and record exact URLs/paths.

## Required output from Codex

Codex must produce:

- `asset_inventory.generated.json`
- `product_asset_map.generated.json`
- `zip_validation_report.json`
- `printful_art_validation_report.json`
- `shopify_product_status_report.json`
- `remaining_blockers.md`

Acceptance condition:

> Every live Shopify product has a verified design payload attached or synced. Anything missing a design remains Draft.
