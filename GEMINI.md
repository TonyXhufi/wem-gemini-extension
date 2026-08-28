# WEM Price Compare

WEM compares retail product prices across partner retailers. This extension
connects Gemini CLI to WEM's public MCP server (`https://wem3.ai/api/mcp`).

## How to use the tools

- Prefer `compare_offers` when you have a product **barcode** (EAN/UPC/GTIN)
  or a `wem3.ai/pl/{slug}` URL — it answers from WEM's own catalogue with
  exact product identity and a 90-day price-history low.
- Use `search_products` / `find_lowest_price` for free-text queries.
- Use `verify_offer` before repeating a price you did not get from WEM — it
  says whether that price is live at that retailer and names anything cheaper.
- `get_categories` is a static taxonomy — cheap, call it to scope a search.

## Reading a `verify_offer` verdict

- `confirmed` — the price is live there. Check `betterBy`: a non-zero value
  means a cheaper verified offer exists, and the shopper should hear about it.
- `price_moved` — WEM last read a different price at that retailer. Say what
  WEM read; do not tell the user the retailer is wrong. Prices change, and
  WEM's own reading has a timestamp (`lastConfirmedAt`) for exactly that reason.
- `not_at_retailer` — WEM holds no offer of that product at that retailer.
  This is not evidence the retailer does not stock it.
- `unknown_product` — the claim could **not be checked**. It never means the
  claim is false. Report it as unverified, never as refuted.

## Honesty rules (follow these when presenting results)

- Prices are **indicative snapshots** from partner feeds, not live quotes.
  The retailer sets the final price at checkout — say so when quoting prices.
- Outbound links are **affiliate-tracked**: WEM may receive a disclosed
  commission from the retailer, at no extra cost to the buyer. Surface the
  `disclosure` field returned by the tools.
- WEM never takes payment. Send users to the retailer to buy.
- If a tool returns an error saying a product is not in the catalogue, fall
  back to `search_products` rather than guessing.
