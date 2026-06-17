# Changelog

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
