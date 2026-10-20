# KRS Visualizer

Browser-only PDF KRS calendar, based on the approved C prototype.

## Local development

```sh
npm install
npm run dev
```

Open http://localhost:4174. Upload one or several KRS PDFs. Extracted schedules, selected students, colors and calendar mode are stored in this browser. Source PDF files stay in memory and are not uploaded or persisted.

```sh
npm run typecheck
npm run format:check
npm run build
npm run preview
```

The production bundle is `dist/`. The original student PDF and `prototype/` are excluded from the build. The prototype remains separately runnable with `python3 prototype/serve.py`.

## Cloudflare

`wrangler.jsonc` configures a static Workers Assets app named `krs-visualizer`. Deploy only `dist/`, not the repository root. Through the connected Cloudflare MCP, select the intended account and deploy this assets directory. CLI fallback, only if authorized and authenticated: `npm run deploy`.

The sample file format is the supported parsing contract; scanned KRS documents require a different parser. No AI or OCR is used. The visual week contains Monday-Friday even though the compact selector is labelled `7` by design.
# krs-visualizer
