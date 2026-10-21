# Handmade By Bhumi Catalogue

A lightweight, responsive, static product catalogue for Handmade By Bhumi. It uses plain HTML, CSS and JavaScript, so there is no build step, database, paid API or customer login.

## Features
- Warm pastel handmade-brand styling
- Search across all categories (a search query takes priority over the selected category)
- Category filters and product sorting
- Product variants with prices and variant-specific images
- Multiple image thumbnails per product
- Product detail pop-up and Instagram enquiry link
- Responsive mobile layout

## Preview locally
Open `index.html` in a browser.

## Publish for free
Use Netlify's manual deploy by dragging the project folder into Netlify Drop, or enable GitHub Pages in repository Settings → Pages and select the `main` branch and `/ (root)`.

## Important before launch
The current products, prices and stock photos are sample content to demonstrate the interface. They are **not** claimed to be the original Handmade By Bhumi catalogue. Replace the `productsData` array in `index.html` with confirmed product names, prices and image URLs when the original data is recovered. Replace the Instagram profile URL in the page if the correct handle differs.

### Editing a product
Each entry in `productsData` has:
- `name`, `category`, `description`
- `images`: array of image URLs
- `variants`: array of `{ name, price, image }`; `image` is a zero-based index into that product's images

All displayed prices are in Indian rupees (₹). No checkout, cart, customer account or payment gateway is included by design.
