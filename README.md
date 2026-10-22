# Portray — connected digital studio

Dark, lime-accented agency website with a persistent Three.js globe, scroll-driven camera composition and animated 3D service illustrations.

## Development

Use Node.js 22.12+ (validated with Node.js 24).

```sh
npm ci
npm run dev -- --port 3000
```

## Netlify deployment

```sh
npm run build
```

Upload the contents of `dist` to Netlify Drop. The ready-to-upload `portray-netlify.zip` has `index.html` at its root; extract it and drop that folder into your existing Netlify site's Deploys screen. No server, environment variables or secrets are needed. The GitHub ZIP is a build artifact; source changes need a fresh build before replacing it.

## Content and data

- Brand logo, accent `#B5FF55`, service categories, agency metrics, FAQs and contact `ap@portray.agency` were obtained from https://portray.agency/ on 22 October 2026. Additional service and process summaries are editorial copy based on those categories.
- Booking links to the agency's existing booking section. Contact links use email; there is no simulated booking or submission flow.
- Land geometry comes from the public-domain Natural Earth dataset distributed through `world-atlas`, decoded using `topojson-client`.
- Globe arcs and city endpoints are illustrative, not transaction geolocation. Light pulses are an animation.
- The transaction panel requests https://mempool.space/api/mempool/recent every 20 seconds while the page is visible. It displays only valid returned transaction IDs and actual fees in satoshis, linking to their explorer pages. Pending transactions are not labeled as confirmed. It never invents transfer values, fiat prices or transaction records.
- If the API is unreachable or returns invalid/empty data, the panel explicitly switches to visualization mode and states that the live feed is unavailable. The current cloud proxy blocks the API, so rendering was tested with a clearly isolated test fixture and the unavailable behavior was also tested. Actual provider availability must be checked from the deployed browser.
- Fonts, geometry and visual assets are bundled locally. WebGL failures use actual render captures as static fallbacks. Reduced-motion preferences disable continuous object animation. Off-screen service renders pause.

## Validation

Validated Chromium desktop/mobile layouts, actual WebGL globe rendering and changing frames, scroll-directed globe movement, all five service dialogs and email links, keyboard-operated process tabs, FAQ expansion, mobile navigation, reduced-motion behavior, mock API response handling, API failure behavior and production build. Browser checks live outside the checkout; no test fixtures are shipped in production.
