<img src="assets/icon-512.png" alt="WEM" width="96" align="right" />

# WEM Price Compare — Gemini CLI extension

Connects [Gemini CLI](https://github.com/google-gemini/gemini-cli) to WEM's
public MCP server. Free, read-only, no account.

## Install

```bash
gemini extensions install https://github.com/TonyXhufi/wem-gemini-extension
```

Then in Gemini CLI:

```
/wem:compare Dior Fahrenheit Aftershave 100ml
/wem:deal Sony WH-1000XM5
```

## What you get

The extension points Gemini CLI at `https://wem3.ai/api/mcp`, which exposes
eight read-only tools. Nothing writes, purchases, or takes payment.

| Tool | What it does |
|---|---|
| `search_products` | Keyword search across connected retailers |
| `semantic_search` | Find products from a natural-language description |
| `get_product` | Full detail for one product, by provider and ID |
| `compare_products` | Compare 2–5 products side by side |
| `find_lowest_price` | Single lowest-priced match under stated constraints |
| `compare_offers` | Multi-retailer offers for one product, cheapest first, with a 90-day price-history low |
| `verify_offer` | Check whether a price claim is still true before repeating it |
| `get_categories` | Category taxonomy with approximate price ranges |

## Limits

60 requests/min per IP, 500 product lookups/day per IP, 1000/day across all
callers. These protect the upstream retailer API quota shared with wem3.ai.
`compare_offers`, `verify_offer` and `get_categories` read WEM's own catalogue
and do not count against the lookup quota.

## Using it outside Gemini CLI

The same MCP server works in Claude, Cursor, VS Code, or any Streamable HTTP
MCP client:

```json
{
  "mcpServers": {
    "wem": {
      "url": "https://wem3.ai/api/mcp"
    }
  }
}
```

No account, no API key — the server is public and stateless. Setup guide:
<https://wem3.ai/extension/ai>

## Disclosure

WEM is funded by disclosed affiliate commission. Links returned by the tools
are affiliate-tracked; the retailer sets the final price and checkout always
completes on the retailer's site. Privacy: https://wem3.ai/privacy ·
Disclosure: https://wem3.ai/disclosure
