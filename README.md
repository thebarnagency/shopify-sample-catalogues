# shopify-sample-catalogues

Realistic, fictional sample catalogues for Shopify development stores. Each store has products,
variants, metafields, collections, navigation menus and images, so you can test a theme, an app
or a workflow against a store that looks lived in. Everything here is data: CSV files, a setup
guide and a brand brief per store, with the images hosted on this repo's Releases.

## Stores

| Store | Vertical | Products | Variants | Images | Prices | Colour layout |
| --- | --- | --- | --- | --- | --- | --- |
| [Lune Atelier](stores/lune-atelier/BRAND.md) | beauty | 40 | 231 | 287 | £10–£85 | colour as an option |
| [Maison Orlet](stores/maison-orlet/BRAND.md) | high fashion | 40 | 155 | 120 | £160–£2,600 | one product per colour |

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
   from this repo's Release in the background, so they appear within a few minutes.
5. Back in the guide, paste the prompts for collections and menus.

No AI assistant? `products.csv` imports on its own, and `products-rich.csv`,
`collections.csv`, `menus.csv` and `metafield-definitions.csv` hold everything else for setting
up by hand.

## Images

Every image is a product shot, still life or colour swatch. There are no people and no
packaging text. Each Release has one file per image (named
`<vertical>--<product-handle>--<slot>.webp`) and one zip per store.

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
