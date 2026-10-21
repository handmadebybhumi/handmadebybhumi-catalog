# Handmade By Bhumi catalogue

A responsive static catalogue with universal search, categories, product variants, multi-image galleries and Instagram enquiries.

## Connect the Google Sheet for automatic updates

1. Download `handmade-by-bhumi-products-template.csv` from this repository and import it into Google Sheets (File → Import → Upload).
2. In Google Sheets choose **File → Share → Publish to web**.
3. Select the worksheet/tab containing products, choose **Comma-separated values (.csv)** and click **Publish**. Copy the published CSV URL.
4. Open `index.html` in this repository and find:
   `const GOOGLE_SHEET_CSV_URL = "PASTE_PUBLISHED_GOOGLE_SHEET_CSV_URL_HERE";`
5. Replace only the placeholder text inside the quotes with your published CSV URL. Commit the change to `main`.
6. Deploy via GitHub Pages: **Settings → Pages → Deploy from a branch → main → /(root)**. (If your site is already deployed, wait for the deployment after the commit.)

The storefront checks the sheet on first load and every 30 seconds. It adds a cache-busting query and uses `fetch(..., {cache:"no-store"})`, so visitors don't need to hard-refresh to see sheet edits. Google's own publish/feed propagation may take a short time, so updates aren't guaranteed to appear instantly.

## CSV columns

Required: `product_id,name,category,variant,price,image_url`

Optional: `gallery_urls,description,active,tag`

- Use one row per variant; repeat the same `product_id`, product name and category across variants.
- `price` should be numeric only, e.g. `599` (no ₹ symbol or thousands separators).
- `image_url` must be an HTTPS URL to an image the browser can display.
- Put additional gallery image URLs in `gallery_urls`, separated by semicolons.
- Set `active` to `FALSE` to hide a variant; blank or `TRUE` shows it.
- If all rows for a product are inactive, that product will disappear from the catalogue.

## Image links and privacy

Google Photos album/share links often aren't direct image URLs, so test a link before adding it. The image URL itself may be visible to visitors in browser developer tools. Publishing a sheet to the web makes its product data public; do not put private notes or supplier costs in it.

The sample data and Unsplash images are for testing only, not a recovered original catalogue. The storefront keeps its built-in sample catalogue until a valid published sheet URL is configured; if the sheet temporarily fails, the existing products remain on screen.
