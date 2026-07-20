# Changelog

## v1.1.0 (April 2026) — Audit & Hardening

### Security
- Added `esc()` XSS sanitization helper, applied to all data-derived innerHTML
- PIN inputs masked as password type, reveal on focus
- All admin functions gated with `if(!IS_ADMIN) return`

### Performance
- `curD()`/`prevD()` results cached with dirty flag invalidation
- `debouncedApply()` (150ms) for year selector dropdowns
- Chart loading spinner states (`.cw.loading`)
- Duplicate CSS rules removed

### Reliability
- Error boundary around main render chain (try-catch + toast)
- `dc()` called before every `new Chart()` (fixed 3 leaked instances)
- Upload validation with success/error toasts
- `saveAndDownload()` cleans UI state before HTML capture

### UX
- Toast notification system replaces all `alert()` calls
- Version indicator (v1.1.0) in footer
- Overview tab forced as default on every login

---

## v1.0.0 (April 2026) — Feature Complete

### Features
- PIN-gated multi-brand login (BrandPulse homepage)
- Admin panel with brand/PIN management + save to file
- 5 dashboard tabs: Overview, SKU Analysis, Dealer Analysis, Regional, Matrix
- Interactive Philippines SVG choropleth with heatmap coloring
- Click-to-filter: map region → global dashboard filter
- Drill-down panel: slide-in side panel with top dealers/SKUs per region
- Smart Insights & Recommendations engine
- Self-service data update: Upload Excel → Save & Download → redeploy
- Responsive design: desktop, tablet, mobile, touch devices
- BrandPulse branding with SVG pulse icon
- "Powered by Iontech, Inc." footer

### Data
- 62,984 rows across 5 years (2021–2025)
- 7 Philippine regions mapped
- City-level pin overlays
- Gzip-compressed base64 data embedding
