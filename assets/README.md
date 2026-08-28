# Gallery assets for the Gemini CLI extension

## Why these exist as image files rather than a manifest field

`gemini-extension.json` has **no icon, logo or image field**. Google's own
extension reference (`google-gemini/gemini-cli/docs/extensions/reference.md`)
lists the complete set — `name`, `version`, `description`, `mcpServers`,
`contextFileName`, `excludeTools`, `migratedTo`, `plan`, `settings`, `themes` —
and nothing there carries artwork. The manifest genuinely is read by the
gallery (the card on geminicli.com/extensions shows our `description` verbatim),
so the placeholder tile is not a manifest problem to fix; the artwork comes
from the GitHub repository's own metadata.

## The files

| File | Size | Use |
| --- | --- | --- |
| `social-preview-1280x640.png` | 1280×640 | GitHub **Settings → General → Social preview** on `TonyXhufi/wem-gemini-extension`. This is the Open Graph image gallery sites scrape, and the most likely source of the card tile. |
| `icon-512.png` | 512×512 | Square app icon — MCP directories, README badges, the press kit. |
| `icon-1024.png` | 1024×1024 | Same mark where a larger square is required. |

All three use the **mark** (the three bars from the wordmark's E, white on
`#FF6600`), not the WEM wordmark. That is deliberate: a wordmark is illegible
once a gallery scales it to a 32px tile, whereas the mark survives. Bar
geometry is lifted from `public/favicon.png` — 56% of width, 8.8% stroke,
centres 20.7% apart — so the tile and the site favicon can never disagree.

The banner uses square corners and sits the mark on `#0B0B0B`: rounded corners
belong to an app icon, and baking them into a full-bleed banner reads as a
rendering mistake. The mark is 420px (~66% of banner height) because at 300 it
vanished once the gallery scaled it to a card thumbnail.

## Regenerating

The generator lives in the commit that added this directory; the source SVG is
the single source of truth. Keep the orange and the near-black exact — the
wordmark is the only mark WEM uses, and a stacked or cropped variant of it has
never been approved.

## Worth knowing

The social preview is a **web-UI-only setting** on GitHub — there is no REST or
GraphQL endpoint for it, so it cannot be scripted and is not something CI can
drift. Set it by hand once.

Gallery refresh is on the gallery's own crawl schedule, not ours: expect the
tile to change on their next index, not immediately after the upload.
