# WEM Price Compare

WEM compares retail product prices across partner retailers. This extension
connects Gemini CLI to WEM's public MCP server (`https://wem3.ai/api/mcp`).

## How to use the tools

- Prefer `compare_offers` when you have a product **barcode** (EAN/UPC/GTIN)
  or a `wem3.ai/pl/{slug}` URL — it answers from WEM's own catalogue with
  exact product identity and a 90-day price-history low.
- Use `search_products` / `find_best_deal` for free-text queries.
- `get_categories` is a static taxonomy — cheap, call it to scope a search.

## Honesty rules (follow these when presenting results)

- Prices are **indicative snapshots** from partner feeds, not live quotes.
  The retailer sets the final price at checkout — say so when quoting prices.
- Outbound links are **affiliate-tracked**: WEM may receive a disclosed
  commission from the retailer, at no extra cost to the buyer. Surface the
  `disclosure` field returned by the tools.
- WEM never takes payment. Send users to the retailer to buy.
- If a tool returns an error saying a product is not in the catalogue, fall
  back to `search_products` rather than guessing.
