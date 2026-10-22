# shopify-sample-catalogues

Realistic, fictional sample catalogues for Shopify development stores. Each store has products,
variants, metafields, collections, navigation menus and images, so you can test a theme, an app
or a workflow against a store that looks lived in. Everything here is data: CSV files, a setup
guide and a brand brief per store, with the images hosted on this repo's GitHub Pages.

## Stores

| Store | Vertical | Products | Variants | Images | Prices | Colour layout |
| --- | --- | --- | --- | --- | --- | --- |
| [Lune Atelier](stores/lune-atelier/BRAND.md) | beauty | 40 | 231 | 287 | £10–£85 | colour as an option |
| [Velorne](stores/velorne/BRAND.md) | fashion footwear | 40 | 355 | 90 | £295–£995 | one product per colour |
| [Popwire](stores/popwire/BRAND.md) | fast fashion | 40 | 699 | 173 | £4–£65 | colour as an option |
| [Maison Orlet](stores/maison-orlet/BRAND.md) | high fashion | 40 | 155 | 120 | £160–£2,600 | one product per colour |
| [Ottavina](stores/ottavina/BRAND.md) | high fashion | 40 | 176 | 120 | £220–£2,400 | one product per colour |
| [Glimmerlow](stores/glimmerlow/BRAND.md) | jewellery | 40 | 114 | 91 | £18–£395 | colour as an option |
| [Fiorasso](stores/fiorasso/BRAND.md) | luxury jewellery | 40 | 162 | 102 | £650–£48,000 | one product per colour |
| [Fernhollow Outfitters](stores/fernhollow-outfitters/BRAND.md) | menswear | 40 | 376 | 172 | £25–£495 | colour as an option |
| [Vantor Run](stores/vantor-run/BRAND.md) | sports shoes | 40 | 923 | 135 | £12–£220 | colour as an option |
| [Brickline Supply](stores/brickline-supply/BRAND.md) | streetwear | 40 | 242 | 113 | £18–£320 | one product per colour |

Each store lives in `stores/<store>/`:

| File | What it is |
| --- | --- |
| `products.csv` | Shopify's standard product CSV. Import it under **Products > Import**. |
| `products-rich.csv` | The same rows plus collections, taxonomy attributes, variant metafields and image slots. |
| `products-split-colours.csv`, `products-rich-split-colours.csv` | Only for stores that list colour as an option: the same catalogue with one product per colour. |
| `metafield-definitions.csv`, `collections.csv`, `menus.csv` | Everything a CSV import cannot create. |
| `SETUP-WITH-AI.md` | The order of operations, with a paste-ready prompt per step for an AI assistant connected to your store. |
| `BRAND.md` | The creative brief: voice, palette, photography and customers. |

## Quick start (about 5 minutes)

You need an **empty development store**. The import adds products, collections and menus, and it
does not clear anything first.

1. Pick a store above and download its folder (or clone this repo).
2. In Shopify admin, set the store currency to the one named in the store's `SETUP-WITH-AI.md`
   (**Settings > General > Store defaults**), so prices import as written.
3. Open the store's `SETUP-WITH-AI.md` in an AI assistant connected to your store through an
   MCP server that can write products, metafield definitions, collections and menus. The guide was
   tested with Claude Code and Shopify's plugin for it. Paste its first two prompts: connect, then
   create the metafield definitions (so the import fills typed fields).
4. Go to **Products > Import**, choose `products.csv` and import it. Shopify fetches the images
   from this repo's GitHub Pages in the background, so they appear within a few minutes.
5. Back in the guide, paste the prompts for collections and menus.

No AI assistant? `products.csv` imports on its own, and `products-rich.csv`,
`collections.csv`, `menus.csv` and `metafield-definitions.csv` hold everything else for setting
up by hand.

## Screenshots

Each store straight after a `products.csv` import on Shopify's Horizon theme, before any
collections or menus are set up.

| Maison Orlet | Lune Atelier |
| --- | --- |
| ![Maison Orlet product grid: shirts on mannequins, a leather tote and trousers on hangers, with a sold-out badge](https://github-files.thebarnagency.co.uk/images/screenshots/v0.1/maison-orlet-collection.webp) | ![Lune Atelier product grid: blush, concealer and lip tint packaging on pastel backgrounds, with a sale badge](https://github-files.thebarnagency.co.uk/images/screenshots/v0.1/lune-atelier-collection.webp) |
| ![Maison Orlet product page: an oxblood tiered dress, front, back and fabric close-up, with Italian sizes](https://github-files.thebarnagency.co.uk/images/screenshots/v0.1/maison-orlet-product.webp) | ![Lune Atelier product page: a lip tint with a colour swatch, packshot and twelve shades, one sold out](https://github-files.thebarnagency.co.uk/images/screenshots/v0.1/lune-atelier-product.webp) |

| Ottavina | Fernhollow Outfitters |
| --- | --- |
| ![Ottavina product grid: silk dresses, a velvet opera coat, a wool coat and a blazer on dress forms in warm daylight, with sale and sold-out badges](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/ottavina-collection.webp) | ![Fernhollow Outfitters product grid: preloved chore coats, field jackets and overshirts on dress forms, sizes in the titles, with sale prices](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/fernhollow-outfitters-collection.webp) |
| ![Ottavina product page: a bottle-green wool crepe blazer, front, back and lapel close-up, with Italian sizes, one sold out](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/ottavina-product.webp) | ![Fernhollow Outfitters product page: an ecru canvas chore coat with a cord collar, front, folded and close-up, with sizes and two colours](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/fernhollow-outfitters-product.webp) |

| Brickline Supply | Popwire |
| --- | --- |
| ![Brickline Supply product grid: boxy tees, a half-zip sweat and a long sleeve tee on dress forms, with sale badges](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/brickline-supply-collection.webp) | ![Popwire product grid: a baby tee, jeans on hangers and claw clips, with sale prices](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/popwire-collection.webp) |
| ![Brickline Supply product page: a clay packable liner jacket, front, back and pocket close-up, with sizes S to XXL](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/brickline-supply-product.webp) | ![Popwire product page: a hot-pink satin wrap co-ord top, front, back and neckline close-up, with two colours and UK sizes, one sold out](https://github-files.thebarnagency.co.uk/images/screenshots/v0.2/popwire-product.webp) |

## Images

Every image is a product shot, still life or colour swatch. There are no people and no
packaging text. The CSVs link each image on this repo's GitHub Pages (the `gh-pages` branch,
`images/<version>/<vertical>--<product-handle>--<slot>.webp`), and each Release has one zip of
images per store.

The images were generated locally with ComfyUI, using FLUX.1 [schnell], FLUX.2 [klein] 4B
(both Apache 2.0) and, for upscaling where used, 4x_NMKD-Superscale. Those licences allow the
outputs to be released under CC0.

## No real brands

Every brand, person and product here is fictional. Any resemblance to a real label is a bug, so
please open an issue.

## Edge cases are deliberate

Each catalogue includes long titles, sold-out variants, compare-at prices, single-variant items
and images without alt text, because real stores have them.

## Licence

CC0 1.0 Universal: public domain. Use it for anything, with no need to ask or credit. See
`LICENSE`.
