# BPH Portal (BrandPulse)

Multi-brand sales analytics dashboard built for Iontech, Inc.

**Live**: [raffyrojo.github.io/bph-portal](https://raffyrojo.github.io/bph-portal/)

## Quick Start
1. Open `index.html` (or `bph_portal.html`) in a browser
2. Select a brand and enter its PIN, then click "Enter Dashboard"
3. Admin access is via the "Admin Access" link on the homepage

> Note: brand and admin PINs are set inside the app and are not published here.

## Folder Structure
```
bph-portal/
├── CLAUDE.md              # Cowork instructions (Claude reads this first)
├── README.md              # This file
├── builds/
│   └── bph_portal.html    # Production file (~900KB)
├── context/
│   ├── architecture.md    # System architecture, data format, design tokens
│   ├── known-issues.md    # Bug tracker and regression risks
│   └── workflows.md       # Step-by-step guides for common tasks
├── data/
│   ├── UGREEN_SALES_REPORT_2021.xlsx
│   ├── UGREEN_SALES_REPORT_2022.xlsx
│   ├── UGREEN_SALES_REPORT_2023.xlsx
│   ├── UGREEN_SALES_REPORT_2024.xlsx
│   └── UGREEN_SALES_REPORT_2025.xlsx
└── docs/
    └── changelog.md       # Version history
```

## Tech Stack
- Vanilla HTML/CSS/JS (no frameworks)
- Chart.js 4.4.1 (CDN)
- SheetJS/XLSX (CDN)
- Gzip compression via browser-native DecompressionStream/CompressionStream

## Self-Service Workflow
Update the app → edit index.html on GitHub (keep bph_portal.html in sync) → commit to main → GitHub Pages auto-deploys in ~1 min. No developer needed.
