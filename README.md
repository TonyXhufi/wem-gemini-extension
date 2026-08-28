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

## Publishing checklist (WEM maintainers)

This directory is the SOURCE for a small standalone public repo
(suggested name: `wem-gemini-extension`). To publish:

1. Create the public repo and copy this directory's contents to its root.
2. **Add the `gemini-cli-extension` GitHub topic** (repo → About → Topics).
   The extensions gallery indexes by that topic — without it the extension
   NEVER appears, and nothing warns you. This is the single most-forgotten
   step.
3. Create a GitHub Release (the CLI installs from releases).
4. Verify discovery: the repo should appear under
   github.com/topics/gemini-cli-extension within a few minutes.

No review, no fee — Google explicitly does not vet extensions. Keep
`gemini-extension.json` here and in the public repo in sync; the MCP URL is
the only load-bearing line.

## Disclosure

WEM is funded by disclosed affiliate commission. Links returned by the tools
are affiliate-tracked; the retailer sets the final price and checkout always
completes on the retailer's site. Privacy: https://wem3.ai/privacy ·
Disclosure: https://wem3.ai/disclosure
