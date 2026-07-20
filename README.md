# BPH Portal (BrandPulse)

Multi-brand sales analytics dashboard built for Iontech, Inc.

**Live**: [bph-portal.netlify.app](https://bph-portal.netlify.app)

## Quick Start
1. Open `builds/bph_portal.html` in a browser
2. Select a brand (UGREEN/1234, Logitech/5678, JBL/9999)
3. Enter the PIN and click "Enter Dashboard"
4. Admin access: click "Admin Access" on homepage, PIN: 3102

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
Upload new data → Save File → Deploy to Netlify. No developer needed.
