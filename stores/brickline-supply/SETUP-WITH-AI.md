# Set up Brickline Supply with an AI assistant

Brickline Supply is a fictional streetwear store: 40 products, 242 variants, 16 collections and 2 menus, priced in GBP. This guide takes an empty Shopify store to the finished catalogue. You import the products CSV yourself, and an AI assistant connected to your store does the rest from the CSV files in this folder.

## Files

| File | What it holds |
| --- | --- |
| `products.csv` | Shopify's standard product CSV. Import it under **Products > Import**. |
| `products-rich.csv` | The same rows plus collections, taxonomy attributes, variant metafields and image slots. The assistant reads this one. |
| `metafield-definitions.csv` | The custom fields to create before importing. |
| `collections.csv` | Every collection, with the rules for automated ones. |
| `menus.csv` | The navigation menus, one row per link. |

## Before you start

- Use an **empty development store**. The import adds products, collections and menus.
- Set the store currency to **GBP** under **Settings > General > Store defaults**, so prices import as written.
- Connect an AI assistant to the store through an MCP server that can read and write products, metafield definitions, collections and navigation menus. This guide was tested with Claude Code and Shopify's plugin for it, which signs in to the store through Shopify CLI when the first prompt asks it to connect.
- Every image is hosted on this project's GitHub Pages, so Shopify fetches the pictures while it imports the CSV. You need no image files on your computer.

Run the steps in order. Each prompt is written to be pasted as is; attach or paste the file it names.

## 1. Connect the assistant

> Connect to my Shopify store `your-store.myshopify.com`. Ask for the access this setup needs: read and write products, metafield definitions, collections, navigation menus and online store publishing. Once connected, confirm by telling me the store name, its currency and how many products it has. Don't create or change anything yet.

## 2. Create the metafield definitions

`metafield-definitions.csv` lists 6 product fields. Creating them first means the CSV import fills typed fields instead of loose values.

> Here is `metafield-definitions.csv`. For each row, create a metafield definition with that owner (product or variant), namespace, key, name, type and description. Where `choices` is filled in, add a choices validation with those values (they are separated by `; `). Skip any definition that already exists with the same type, and tell me if one exists with a different type. Finish with a table of what you created.

## 3. Import the products

In the Shopify admin, go to **Products > Import**, choose `products.csv` and import it. You should end up with 40 products and 242 variants. Shopify fetches the 113 images in the background, so they can take a few minutes to appear.

If you'd rather have the assistant do it, ask it to create the products from `products-rich.csv`. That is slower, but it can also set the variant fields in the same pass.

The "Also available in" field (`custom.colour_siblings`) is filled by the import: it lists the URL handles of the same design in its other colours, for a theme to show as colour links.

## 4. Create the collections

`collections.csv` has 7 manual collections and 9 automated collections. Products join manual collections through the `Collections` column of `products-rich.csv`.

> Here are `collections.csv` and `products-rich.csv`. Create each collection in `collections.csv` with its handle, title, description and sort order. For `smart` rows, make it an automated collection: `rules` are Shopify rule terms (column, relation, condition) separated by `; `, and `match` says whether products must meet all of them or any. For `manual` rows, add every product whose `Collections` cell in `products-rich.csv` lists that collection's handle (the cell is on each product's first row, handles separated by `; `). Publish every collection to the Online Store. Finish with a table of collections and how many products each holds.

## 5. Build the menus

`menus.csv` describes `main-menu` (Main menu), `footer` (Footer menu). A new store already has `main-menu` and `footer`, so the assistant replaces their links.

> Here is `menus.csv`. For each `menu_handle`, update the menu with that handle (create it if it doesn't exist) so its links match the file exactly, removing links that aren't listed. `position` gives the order and nesting: `2.1` is the first child of item `2`. `link_type` is `collection` (the target is a collection handle), `catalog` (all products), `search`, `home` or `url` (a group heading when the target is `#`). Show me each menu as a nested list when you're done.

## 6. Optional: taxonomy attributes

Every product already has its Standard Product Taxonomy category. `products-rich.csv` also lists its category attributes (`Category Attributes`, such as `color=gray`) and which options match a taxonomy attribute (`Option Links`, such as `Size=size`). These power the search and filter features that read category metafields.

> Using `products-rich.csv`, set each product's category metafields from its `Category Attributes` column (attribute handle = value handles, separated by commas), enabling the standard definitions you need first. Then link each option named in `Option Links` to that category metafield. Do this for a few products first and show me the result before doing the rest.

## 7. Check the result

> Check the store against these numbers and tell me about any difference: 40 products, 242 variants, 16 collections (new-in, jackets, trousers, knitwear, t-shirts, shirts, shoes, accessories, sale, brand-brickline, brand-fellwick-outdoor, brand-corvo-workwear, brand-sable-run, brand-tessel-studio, brand-moorfoot, responsible-production), and the menus main-menu, footer. Also confirm every product is active and published to the Online Store.

## Deliberate edge cases

Some products are odd on purpose, so themes and apps can be tested against them. The `Edge Cases` column of `products-rich.csv` marks them: `long_title`, `sold_out_variant`, `sold_out_product`, `compare_at` (on sale), `single_variant` and `missing_alt` (images without alt text). Don't let the assistant "fix" them.
