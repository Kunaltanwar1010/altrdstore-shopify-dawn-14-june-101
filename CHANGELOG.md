# Changelog

## Black/white collection page (wearadhd-style)

Rebuilt the collection header in strict black & white (`sections/main-collection-banner.liquid`) and switched filtering to Shopify's **native drawer** facets. Theme-check clean, validated via the Dev MCP, OS 2.0.

**Delivered:**
- **Collection header** — lowercase H1 title, product count ("N products"), optional description. Color mode toggle (light/dark, monochrome either way).
- **Sub-collection pills** — editable as `pill` blocks (pick a collection, optional custom label/link). The pill matching the current collection auto-highlights. Hidden when no pills are added.
- **Grid-density toggles** — desktop 2/3 (4 available) and mobile 1/2 icon buttons. The choice persists in `localStorage` (`altrd-density-desktop` / `altrd-density-mobile`) so it sticks across pages. Controls the native `#product-grid` columns via robust data-attribute CSS (no dependency on Dawn class names).
- **Filter & sort drawer** — `templates/collection.json` → `product-grid.filter_type: "drawer"` (native Shopify facets; sort, availability, size, price all keep working with state in the URL `?filter.*` / `?sort_by=`).

**How to edit (Theme editor → Collection template):**
- **Sub-collection pills:** open the **Collection banner** section → add **Sub-collection pill** blocks → pick a collection (e.g. on a hoodies page add Pullover / Zip). Label defaults to the collection title; override with the Label/Link fields.
- **Density defaults:** Collection banner → *Default columns — desktop/mobile*. (Shoppers can still toggle; their choice is saved per-browser.)
- **Color mode:** Collection banner → *Color mode* (light = white bg/black text, dark = inverted). Strict monochrome either way.

**Admin step you must do (Shopify → Search & Discovery → Filters):**
Enable the **Availability**, **Size** (variant option), and **Price** filters so the drawer facets and counts ("S (12)") populate. Without this, the drawer shows only Sort.

**Phase 2 (done — `snippets/card-product.liquid` + `snippets/price.liquid`, applies to every product card site-wide):**
- **Monochrome badge stack** (top-left, stackable) — Dawn's coloured badges are hidden and replaced with black pill / white text badges: **Sold out**, computed **Save X%** on sale, plus **tag-driven labels**.
- **Save X% pill** added to pricing (`price.liquid`) — shows next to the struck compare-at price (matches the PDP). Compare-at is struck + muted grey; sale price stays monochrome (no accent).
- **Lowercase card titles**, underline-on-hover, monochrome "Choose options" quick-add.
- Hover image-swap is Refresh's native `show_secondary_image` (on in `collection.json`).

**Badge tags (set on a product in Admin → Products → Tags):**
`New In`, `Limited`, `Best Seller`, `Last Few Sizes` → render as monochrome badges on the card (also accepts `new-in` / `best-seller`). Save X% and Sold out are automatic. Add/rename tags to control labels; edit the badge list in `snippets/card-product.liquid` (the `altrd-card-badges` block).

## Black/white footer (wearadhd-style) — `sections/footer.liquid`

Rebuilt Refresh's footer into a near-exact ditto of the wearadhd.com footer in a **strict black & white** scheme (no hi-vis accent). OS 2.0, fully editable, theme-check clean. The newsletter `customer` form, payment icons, and country/language localization selectors remain functional.

It is wired in as the **active footer** via `sections/footer-group.json` (the previous `ALTRD — Footer` section is disabled, not deleted).

### Structure (top → bottom)
1. **Service strip** — 4 icon + title + subtext blocks (desktop 4-across, mobile 2×2).
2. **Newsletter band** — footer logo → "Newsletter" eyebrow → headline → email form → fine print.
3. **Link columns** — three menu columns (desktop columns, mobile `<details>` accordions).
4. **On rotation** — optional Spotify embed block (off by default).
5. **Trademark / legal microcopy** — editable rich text.
6. **Bottom bar** — social icons + localization + payment icons, then copyright + policies.

### How to edit (Theme editor → Footer group → "Footer")

- **Upload the footer logo:** section setting **Logo → Footer logo**. Use a **white PNG/SVG** (the footer is dark by default). If left empty it falls back to Theme settings → Logo, and if that's empty it shows the shop name in Bebas. Adjust **Logo width**.
- **Set the three menus:** each **Menu column** block → **Menu** picker. Defaults: column 1 → `main-menu`, columns 2 & 3 → `footer`. Build/point these in **Admin → Online Store → Navigation** (suggested: `shop`, `info`, `support`). Edit each column **Heading** inline.
- **Newsletter copy:** section settings → **Newsletter** → *Eyebrow label*, *Heading* ("Subscribe and get 10% off"), *Fine print*. The form posts to the customer list tagged `newsletter` (unchanged Refresh behavior).
- **Trademark / legal:** section settings → **Legal → Trademark / legal microcopy** (rich text; edit to your own brand notice).
- **Color mode:** section setting **Color mode** → Dark (default) or Light. Stays monochrome either way — no accent color.
- **Social icons:** Instagram / X / Facebook come from **Theme settings → Social media**. **WhatsApp** and **Spotify** links are section settings (Social & bottom bar). Set the Instagram handle (e.g. `@cs.ujjawalpahwa`) in Theme settings.
- **On rotation (optional):** enable section setting **On rotation → Show "On rotation" block**, add the **On rotation** block, paste a Spotify **embed** URL (Spotify → Share → Embed → copy the `src`).

### Notes
- Payment icons use Shopify's `payment_type_svg_tag` and are desaturated to monochrome via CSS to fit the B&W scheme.
- Localization selectors reuse Refresh's `country-localization` / `language-localization` snippets.
- Pre-existing theme-check error in `sections/header.liquid` (`StaticStylesheetAndJavascriptTags`) is Dawn core and unrelated to this change.
