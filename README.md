<img src="assets/icon-512.png" alt="WEM" width="96" align="right" />

# WEM Price Compare — Gemini CLI extension

Connects [Gemini CLI](https://github.com/google-gemini/gemini-cli) to WEM's
public MCP server. Free, read-only, no account, no API key.

```
https://wem3.ai/api/mcp
```

## Install

```bash
gemini extensions install https://github.com/TonyXhufi/wem-gemini-extension
```

Then in Gemini CLI:

```
/wem:compare Dior Fahrenheit Aftershave 100ml
/wem:deal Sony WH-1000XM5
```

## What it adds

Eight read-only tools — keyword and natural-language product search, one-product
detail, side-by-side comparison, lowest-price lookup, multi-retailer offers with
a 90-day price-history low, a price-claim check, and the category taxonomy.

None of them writes, purchases, or takes payment.

Two are worth knowing about. `compare_offers` resolves a product identity — a
barcode (EAN/UPC/GTIN) or a `wem3.ai/pl/{slug}` URL — rather than running a
fresh retailer search, so it answers "is this actually the best price" instead
of "what exists". `verify_offer` checks whether a price you did not get from WEM
is still true before you repeat it, and distinguishes *unverifiable* from
*false* — a claim it cannot check is reported as unchecked, never as refuted.

`GEMINI.md` ships the model the guidance for reading those verdicts correctly.

## Prices and disclosure

Prices returned are indicative snapshots from partner feeds, not live quotes.
The retailer sets the final price at checkout, and WEM never takes payment —
users always complete the purchase on the retailer's own site.

WEM is funded by disclosed affiliate commission, and links returned by these
tools are affiliate-tracked at no extra cost to the buyer.

- Disclosure: <https://wem3.ai/disclosure>
- Privacy: <https://wem3.ai/privacy>
- Setup guide: <https://wem3.ai/extension/ai>

## Licence

MIT — see [LICENSE](LICENSE). The licence covers this manifest and
documentation; the hosted service itself is governed by the terms at
<https://wem3.ai/terms>.

