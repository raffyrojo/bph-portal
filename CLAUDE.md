# BrandPulse — BPH Portal

## What this is
A single-file HTML sales analytics dashboard for multi-brand performance tracking. Built for Iontech, Inc. (Philippines). Currently serves UGREEN Philippines sales data (62,984 rows, 2021–2025). Deployed at bph-portal.netlify.app.

## Architecture
- **Single HTML file** (~900KB) containing all CSS, JS, and gzip-compressed base64 data
- **Stack**: Vanilla JS, Chart.js 4.4.1, SheetJS (XLSX), Plus Jakarta Sans + JetBrains Mono fonts (CDN)
- **No build tools, no frameworks, no backend** — fully self-contained, works offline after first load
- **Data**: Gzip-compressed → base64-encoded → embedded in JS variable `B64`, decompressed via browser-native `DecompressionStream`

## File locations
- `builds/bph_portal.html` — the production file (edit this)
- `data/` — Excel source files (UGREEN_SALES_REPORT_2021-2025.xlsx)
- `context/` — architecture docs, field mappings, known issues
- `docs/` — changelogs, audit reports

## Key conventions

### Data flow
Raw Excel → `parseRows()` unpacks to `{date, yr, mo, dealer, grp, cat, sku, prod, qty, gross, net, reg, dept, brand}` → compressed to B64 string → embedded in HTML

### Brand detection
`detectBrand()` checks SKU/product for keywords. Defaults to "UGREEN" for unrecognized products. Other brands: Logitech, JBL, Anker, Baseus, Samsung, Apple.

### PIN system
- Brand PINs stored between `/*BP_START*/` and `/*BP_END*/` comment markers
- Admin PIN stored between `/*AP_START*/` and `/*AP_END*/` markers
- `saveAndDownload()` uses these markers to persist PINs into downloaded files
- PINs also cached in localStorage with try-catch fallback

### Save & Download
`saveAndDownload()` recompresses `raw` data via `CompressionStream("gzip")`, replaces B64 string in `outerHTML`, replaces PIN markers, and downloads the new file. **Critical**: UI state must be cleaned (modals closed, homepage shown) before `outerHTML` capture.

### Filter system
`applyF()` is the central filter function. Filters by: year, months (multi-select), sales group, dealer, category, brand (`CURRENT_BRAND`), and region (`selectedReg`). All chart/table renders cascade from `applyF()`.

### Regional map
SVG-based Philippines choropleth. 7 regions with real geographic paths in `RPATHS`. Click-to-filter triggers `selectReg()` → `applyF()` → full dashboard re-render. Drill-down panel slides from right via `openRegPanel()`.

## When editing
- Always validate balanced braces/parens after changes
- Run `dc("chartId")` before every `new Chart()` to prevent memory leaks
- Sanitize user-provided strings with `esc()` before innerHTML
- Use `toast(msg, type)` instead of `alert()` — types: "ok", "err", or omit for info
- Use `debouncedApply()` for filter dropdowns, `applyF()` for direct calls
- Test that `saveAndDownload()` produces a working file (open the download, verify data loads)

## Known limitations
- PINs are plaintext in HTML source (visible via View Source)
- No server — all changes require file download + redeploy
- Large datasets (>100K rows) may slow initial decompression
- Tables render all rows (no virtualization)

## Current version
v1.1.0 — Last updated from Claude.ai conversation, April 2026
