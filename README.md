# Casa Fresca: Shopify theme

A custom Online Store 2.0 theme for [casafrescameals.com](https://casafrescameals.com), Casa Fresca's weekly meal-prep and catering store in Crawfordsville, Indiana.

The home page leads with this week's menu. Every meal can be added in one tap, the cart drawer is a tap away on every page, and phones get a sticky "Cart · N · $X · Checkout" bar.

- Preview with real store data: https://justuseflint.github.io/casa-fresca-theme-preview/
- Built on vanilla JS with no dependencies. Fonts are self-hosted (Bricolage Grotesque and Instrument Serif). It respects `prefers-reduced-motion`. `shopify theme check` passes with no offenses.

## Install
1. Zip the theme folder so the files sit at the zip root, or use the `casa-fresca-theme.zip` release.
2. In Shopify admin, go to **Online Store → Themes → Add theme → Upload zip file**.
3. On the new theme, click **Customize**, check every page, then click **Publish**.

## After uploading
1. **Theme settings → Ordering**: check that *This week's menu collection* is **Weekly Meals** and *All meals collection* is **All Meals**. Both are preset. Set the cut-off (Thursday, 18:00) and ready day (Tuesday). Tick **We're taking a week off** on weeks without a menu.
2. **App embeds** (Customize → App embeds): switch back on whatever you use: GetSiteControl countdown, GemPages and Shopify Forms. The theme has its own cut-off countdown, so the GSC bar is optional.
3. **Apps blocks**: re-add the Google Reviews (Appio) block on the home page if you want the live widget. Use an *Apps* section or the reviews section's app block.
4. **Page templates**: in **Online Store → Pages**, assign `page.catering`, `page.how-it-works`, `page.contact`, `page.macro-calculator` and `page.nutrition-quiz` to the matching pages, if Shopify didn't keep them.
5. **GemPages pages** (Locations, Crawfordsville Meal Prep): republish them from GemPages to the new theme.
6. **Metafields (optional, recommended)**: **Settings → Custom data → Products**:

| Name | Namespace and key | Type |
|---|---|---|
| Calories | `custom.calories` | Integer |
| Protein (g) | `custom.protein` | Integer |
| Carbs (g) | `custom.carbs` | Integer |
| Fat (g) | `custom.fat` | Integer |
| Short description | `custom.tagline` | Single line text |
| Ingredients | `custom.ingredients` | Multi-line text |
| Allergens | `custom.allergens` | List of single line text |
| Reheating | `custom.reheating` | Multi-line text |
| Nutrition label | `custom.nutrition_label` | File (image) |
| Card photo | `custom.card_image` | File (image) |

Everything falls back gracefully:
- Product images whose filename contains "Nutrition" or "Label" are detected automatically, kept out of the photo gallery and shown in the Nutrition label panel.
- "PhotoComingSoon" placeholders become a designed text tile.
- Allergens and reheating fall back to editable text.

## What stays the same
- Standard `/cart/add` (`id` and `quantity`), the AJAX Cart API, and the cart note ("Order special instructions").
- Shopify checkout, Shop Pay, and local pickup and delivery.
- Search & Discovery filters (availability and price) and the standard sorting.
- `@app` blocks in the product details, the cart drawer, the cart page, reviews and the footer.

## Structure
`layout/`, `templates/` (JSON), `sections/` (including header and footer groups), `snippets/`, `assets/`, `config/` and `locales/`.
