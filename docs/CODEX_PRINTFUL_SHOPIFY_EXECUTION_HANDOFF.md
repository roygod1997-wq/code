# CROW & CROWN — Printful + Shopify Ready-to-Sell Codex Handoff

Date: 2026-06-19  
Owner: Royal / CROW & CROWN  
Storefront: thecrowandcrown.com  
Shopify admin domain known from prior context: `v0baxq-75.myshopify.com`  
Live theme: `CROW & CROWN — Industrial Museum Luxury Draft`  
Unpublished theme available: `Atelier` 4.1.0  
Execution target: Codex builds, validates, and executes the Shopify + Printful launch workflow.

## 0. Non-negotiable constraints

1. Do not redesign the approved artwork.
2. Do not alter typography, muse artwork, crown sketch, layouts, crop marks, proportions, wording, or product contents.
3. Do not add personalization fields.
4. Do not use yellow, cream, beige, taupe, greige, warm ivory, aged-paper, glitter, princess styling, cartoon styling, or mockup-only printable files.
5. Shell/background standard for production pages: true clean white or matte black/dark editorial backgrounds only.
6. Production PDFs must be real print files, not image-generation previews.
7. Every saleable product must have:
   - final customer ZIP/PDF/PNG assets attached or Printful product synced,
   - polished listing images,
   - working checkout,
   - correct delivery/fulfillment path,
   - test order verification before publishing.

## 1. Launch architecture

Use two active product lines:

### A. THE ICON EDIT
Luxury children’s fashion exhibition printable party collection.

### B. THE COURT IS MY CANVAS
Basketball/editorial printable party collection.

The launch has two fulfillment types:

### 1. Shopify digital downloads first
These are the immediate revenue products. They must not require shipping.

### 2. Printful physical “Print for You” products second
These are optional physical print-on-demand products synced into Shopify through Printful. Codex must not use Printful’s Manual Orders Products API for a Shopify-connected store. Use the Printful Shopify dashboard sync flow or the appropriate Ecommerce Platform Sync API flow after validating the current Printful API capabilities.

## 2. Required public products

### Digital Shopify products

| Product | SKU | Price | Status target | Fulfillment |
|---|---:|---:|---|---|
| THE ICON EDIT — Mega Printable Bundle | ICON-EDIT-MEGA-BUNDLE | 45.00 | Active after asset attach/test | Shopify Digital Downloads |
| THE ICON EDIT — Basics Printable Pack | ICON-EDIT-BASICS-PACK | 25.00 | Active after asset attach/test | Shopify Digital Downloads |
| THE COURT IS MY CANVAS — Mega Printable Bundle | COURT-CANVAS-MEGA-BUNDLE | 45.00 | Active after asset attach/test | Shopify Digital Downloads |
| THE COURT IS MY CANVAS — Basics Printable Pack | COURT-CANVAS-BASICS-PACK | 25.00 | Active after asset attach/test | Shopify Digital Downloads |

### Printful physical products to create/sync only if Printful catalog supports the exact product/size

Codex must query the current Printful catalog / sync capabilities and map exact product IDs, variant IDs, print areas, and file dimensions. Do not hardcode product IDs.

| Product | SKU | Intended size | Suggested retail rule |
|---|---:|---|---|
| THE ICON EDIT — Welcome Sign, Printed for You | ICON-EDIT-WELCOME-PRINT-18X24 | 18x24 poster/sign | Cost + shipping-aware margin; target >=55% gross margin |
| THE ICON EDIT — Gallery Welcome Sign, Printed for You | ICON-EDIT-WELCOME-PRINT-24X36 | 24x36 poster/sign | Cost + shipping-aware margin; target >=55% gross margin |
| THE ICON EDIT — Photo Booth Backdrop Print | ICON-EDIT-BACKDROP-PRINT-36X24 | 36x24 horizontal poster/sign if supported | Cost + shipping-aware margin; target >=55% gross margin |
| THE COURT IS MY CANVAS — Welcome Sign, Printed for You | COURT-CANVAS-WELCOME-PRINT-18X24 | 18x24 poster/sign | Cost + shipping-aware margin; target >=55% gross margin |
| THE COURT IS MY CANVAS — Court Backdrop Print | COURT-CANVAS-BACKDROP-PRINT-36X24 | 36x24 horizontal poster/sign if supported | Cost + shipping-aware margin; target >=55% gross margin |

If Printful does not support the exact intended sign/backdrop dimensions, keep the product in Draft and add a blocking note with the available alternatives.

## 3. Shopify implementation requirements

Use Shopify Admin API GraphQL stable version available to the store. Preferred: current stable GraphQL Admin API; do not rely on deprecated REST unless a specific action is not yet available in GraphQL.

Create/update:
- Products
- Variants
- Product media
- SEO title/description
- Collections
- Tags
- Metafields
- Navigation links if missing
- Product templates/sections where needed

### Required Shopify product settings

For digital products:
- `requires_shipping = false`
- inventory tracking off unless the store has a reason to cap sales
- status `DRAFT` until the file is attached and tested
- product type: `Digital Printable`
- vendor: `CROW & CROWN`
- tags:
  - `digital-download`
  - `printable-party`
  - collection tag (`the-icon-edit` or `court-canvas`)
  - `ready-to-print`
  - `no-personalization`

For Printful products:
- `requires_shipping = true`
- fulfillment service / shipping must be Printful-managed after sync
- product type: `Printful POD`
- vendor: `CROW & CROWN`
- tags:
  - `printful`
  - `printed-for-you`
  - collection tag
  - `physical-product`

## 4. Digital delivery requirements

Use Shopify Digital Downloads app if installed and accessible.

Digital Downloads app behavior to respect:
- ZIP/PDF/JPG/PNG files can be attached to products.
- Multiple files can be added per variant.
- Digital products can automatically send download links after payment.
- Downloads at checkout can be enabled only when the Shopify plan supports checkout customization.

If no supported programmatic API is available for the Digital Downloads app file attachment:
1. Create all Shopify products, variants, pricing, descriptions, images, SEO, and collections through API.
2. Leave products in `DRAFT`.
3. Generate a precise manual completion checklist for attaching the ZIPs in the Digital Downloads app.
4. Do not publish until the files are attached and a test order proves download delivery.

## 5. Printful requirements

Codex must validate current Printful behavior before execution:
- Shopify-connected Printful products should be created/synced through the Printful Shopify flow or Ecommerce Platform Sync API.
- Do not use the Printful Manual Orders Products API for Shopify-connected synced products.
- Pull current catalog/variant/print-area data before constructing products.
- Generate or upload print files according to the exact Printful template for the selected product.
- Generate Printful mockups from the synced product flow if available.
- Do not publish a Printful product if image placement, print area, variant mapping, shipping, or tax is incomplete.

## 6. Asset requirements

Expected source/customer packages:
- `THE_ICON_EDIT_PRINTABLE_BUNDLE.zip`
- `THE_COURT_IS_MY_CANVAS_PRINTABLE_BUNDLE.zip`
- any smaller Basics Pack ZIPs or Codex-generated subset ZIPs
- product listing images, minimum 2000 px on the short side; primary should be clean single-product/lifestyle finished-product style, not cluttered collage

Digital ZIP internal standard:
```text
00_START_HERE/
01_INVITATIONS/
02_SIGNS/
03_PARTY_LABELS/
04_CUTOUTS/
05_FAVOR_PACKAGING/
06_PRINT_FOR_YOU/
LICENSE_AND_TERMS/
```

Codex must fail the build if a required customer ZIP is missing, corrupt, blank, has low-resolution files, or contains rejected/off-brand assets.

## 7. Product copy

### THE ICON EDIT — Mega Printable Bundle
Title: `THE ICON EDIT — Luxury Printable Party Bundle`
Subtitle/metafield: `A high-fashion birthday exhibition printable collection.`
Price: `$45`
Description:
```markdown
A luxury printable party collection designed like a children’s fashion exhibition.

THE ICON EDIT includes coordinated ready-to-print pieces for the invitation moment, welcome area, dessert table, drink station, activity station, photo moment, and favor table. The look is editorial, minimal, black-and-white, gallery-inspired, and intentionally polished.

This is a digital printable product. No physical item ships with this purchase.

Included:
- Start Here printing guide
- Invitation suite
- Welcome/signage files
- Food and drink printables
- Favor tags and party labels
- Cutout and activity pieces
- Print-for-you guidance

Format:
- PDF/PNG files bundled in ZIP format
- Ready to print
- Non-editable
- No personalization required
```

### THE ICON EDIT — Basics Printable Pack
Title: `THE ICON EDIT — Basics Printable Pack`
Price: `$25`
Description:
```markdown
A smaller ready-to-print starter pack from THE ICON EDIT collection.

Use this pack for the core party setup: invitation, welcome/signage, food table accents, drink labels, and basic favor details. Designed for a clean editorial birthday setup without customization or extra design work.

Digital download only. No physical product ships.
```

### THE COURT IS MY CANVAS — Mega Printable Bundle
Title: `THE COURT IS MY CANVAS — Basketball Printable Party Bundle`
Price: `$45`
Description:
```markdown
A modern basketball-inspired printable party collection with an editorial black-and-white art direction.

This digital bundle is built for a polished party setup, including invitation pieces, signs, labels, activity pieces, favor packaging, and print guidance.

Digital download only. No physical product ships.
```

### THE COURT IS MY CANVAS — Basics Printable Pack
Title: `THE COURT IS MY CANVAS — Basics Printable Pack`
Price: `$25`
Description:
```markdown
A smaller basketball printable starter pack for a clean party setup.

Includes the core ready-to-print files for invitations, signage, labels, and basic party styling.

Digital download only. No physical product ships.
```

## 8. Collections and navigation

Create/verify these Shopify collections:
- `The Icon Edit`
- `The Court Is My Canvas`
- `Digital Printable Bundles`
- `Printed For You`

Homepage/product routing:
- Icon Edit hero remains primary.
- Court Is My Canvas appears as a separate lower section.
- Do not mix Court artwork into Icon Edit sections.
- Keep live theme safe; do not publish a theme change without explicit review.

## 9. Required Codex files to add/update in repo

Create:
- `data/products.crow-crown.launch.json`
- `scripts/shopify/create_or_update_products.ts`
- `scripts/shopify/attach_digital_downloads_runbook.md`
- `scripts/printful/sync_printful_products.ts`
- `scripts/qa/validate_customer_zips.ts`
- `scripts/qa/validate_product_pages.ts`
- `docs/CODEX_PRINTFUL_SHOPIFY_EXECUTION_HANDOFF.md`

Use dry-run mode first:
```bash
SHOPIFY_STORE_DOMAIN=v0baxq-75.myshopify.com \
SHOPIFY_ADMIN_API_ACCESS_TOKEN=... \
PRINTFUL_API_TOKEN=... \
PRINTFUL_STORE_ID=... \
node scripts/shopify/create_or_update_products.ts --dry-run
```

Then execute only after dry-run output is clean:
```bash
node scripts/shopify/create_or_update_products.ts --apply
node scripts/printful/sync_printful_products.ts --dry-run
node scripts/printful/sync_printful_products.ts --apply
node scripts/qa/validate_product_pages.ts
```

## 10. Secrets required

Add these as GitHub/Codex environment secrets, never commit them:

```text
SHOPIFY_STORE_DOMAIN=v0baxq-75.myshopify.com
SHOPIFY_ADMIN_API_ACCESS_TOKEN=
SHOPIFY_API_VERSION=2026-01
PRINTFUL_API_TOKEN=
PRINTFUL_STORE_ID=
PRINTFUL_SHOPIFY_STORE_ID=
```

Optional:
```text
SHOPIFY_PUBLIC_DOMAIN=thecrowandcrown.com
SHOPIFY_THEME_ID_LIVE=
SHOPIFY_THEME_ID_ATELIER=
```

## 11. QA gates before any product goes active

Digital product cannot go active until:
- product exists in Shopify
- price is correct
- shipping is off
- ZIP is attached in Digital Downloads app
- automatic delivery is enabled
- checkout download/email delivery is tested
- product page displays correct listing images
- file opens after purchase

Printful product cannot go active until:
- exact Printful product/variant selected
- print file fits official template/print area
- mockups generated
- shipping profile attached
- test checkout calculates shipping
- Printful sync status is clean
- no production order is automatically placed during testing unless explicitly approved

Global store launch cannot be marked ready until:
- storefront password is off
- payments are active
- tax settings reviewed
- policies are present
- contact/support email visible
- navigation has all launch collections
- mobile product pages checked
- one digital test order and one physical test checkout complete

## 12. Acceptance criteria

Codex is done only when it opens a PR containing:
- product manifest
- Shopify product creation/update script
- Printful sync script or documented dashboard-sync fallback
- customer ZIP validation script
- digital-download attachment runbook if app attachment is not API-accessible
- QA report with pass/fail status per product
- screenshots or URLs for each saleable product
- list of any remaining blockers

No product should be published as active if the final customer asset or Printful sync is incomplete.
