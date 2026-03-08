# Flash Game

A web-based Flash game gallery that allows users to play classic Flash games directly in the browser.

## Games

Games metadata is stored in `games.json`, and the SWF player is loaded dynamically via a configurable base URL.

- (To be added)

## Local run

`index.html` and `game.html` are static pages.

- Open `index.html` directly.
- Click a game card to open `game.html`.

## Vercel deployment

1. Install and login to Vercel CLI.
2. Deploy from this directory:
   - `vercel`
3. For production:
   - `vercel --prod`

Deployment target is static-only and does not include SWF binaries in the repository.

### SWF base URL configuration

`game.html` reads SWF base URL in this order:

1. Query parameter: `?swfBase=...`
2. Global variable: `window.__SWF_BASE_URL__`
3. `<meta name="swf-base-url" ...>` value (default `/swf/`)

Examples:

- Local: `/game.html?slug=bubble-shooter`
- External storage: `/game.html?slug=bubble-shooter&swfBase=https://cdn.example.com/swf/`
- Runtime override by global variable:

```js
window.__SWF_BASE_URL__ = 'https://cdn.example.com/swf/';
```

If this site moves to a managed static build pipeline, you can replace the meta value globally and keep the same URLs.

## Why SWF is not stored in this repo

Vercel Hobby/Free deployment and Vercel Blob limits make storing the full SWF corpus (약 14GB) in this repo impractical under a no-cost constraint.

## License

MIT
