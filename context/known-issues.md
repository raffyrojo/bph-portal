# Known Issues & Remediation Status

## Fixed (v1.1.0)

| Issue | Status | Fix Applied |
|---|---|---|
| Chart.js memory leak (orphaned instances) | FIXED | dc() called before every new Chart() |
| XSS via innerHTML (unsanitized Excel data) | FIXED | esc() helper applied to tooltips + drill-down |
| alert() blocked in sandboxed environments | FIXED | Replaced with toast() notification system |
| saveAndDownload captures open modals | FIXED | UI state cleaned before outerHTML capture |
| Brand PINs not persisting in downloaded file | FIXED | Marker-based replacement (BP_START/BP_END) |
| Delete brand fails (inline onclick escaping) | FIXED | DOM createElement with event delegation |
| Year dropdown invisible (white on white) | FIXED | .yr-sel option{color:#1a2138;background:#fff} |
| Drill-down panel shows ₱0 (stale data) | FIXED | openRegPanel moved after applyF() |
| confirm() blocked in sandbox | FIXED | Custom inline confirmation UI |
| localStorage errors in sandbox | FIXED | All calls wrapped in try-catch |

## Open Issues

| Issue | Severity | Notes |
|---|---|---|
| PINs plaintext in HTML source | Medium | Visible via View Source. Consider SHA-256 hashing. |
| No table virtualization | Low | 500+ rows render at once. Consider virtual scroll for large datasets. |
| No undo for admin deletions | Low | Brand deletion is permanent. Consider soft-delete or confirmation + undo. |
| 900KB file size | Low | Mostly compressed data. Could split CSS/JS into separate files if needed. |
| No loading skeleton on initial boot | Low | Brief blank screen before data decompresses. |
| curD/prevD cache not invalidated on tab switch | Low | Cache correctly invalidated on applyF, but not on tab-only switches. |

## Regression Risks

When editing, watch for:
1. **Brace/paren imbalance** — single-file minified JS is fragile. Always verify counts.
2. **BP_START/BP_END markers** — saveAndDownload depends on these exact strings. Don't rename them.
3. **outerHTML capture** — any new modal/panel must be closed in the cleanup block of saveAndDownload.
4. **RPATHS object** — SVG paths for the Philippines map. Editing breaks the map silently.
5. **Double chart creation** — some render functions create charts in if/else branches. Both branches need dc().
