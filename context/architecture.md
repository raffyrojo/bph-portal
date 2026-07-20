# Architecture Reference

## Dashboard Tabs

| Tab | ID | Key Functions | Charts |
|---|---|---|---|
| Overview | p-overview | renderKPI(), renderRec(), renderOV() | cNet, cASP, cDept, cRYR, cDlr, cGrp, cTC |
| SKU Analysis | p-sku | renderSKU() | cScat (scatter) |
| Dealer Analysis | p-dealer | renderDealer() | cDlrT (trend) |
| Regional | p-region | renderReg(), renderMap(), renderRegInsights(), renderRegTrend(), renderRegTable() | cRegT |
| Matrix View | p-matrix | renderMatrix() | none (heatmap table) |

## Key Global Variables

| Variable | Purpose |
|---|---|
| `raw` | Full dataset (all rows, all years) |
| `fd` | Filtered dataset (after applyF) |
| `curYr` | Selected current year |
| `cmpYr` | Selected comparison year (null = no comparison) |
| `CURRENT_BRAND` | Logged-in brand (set at login, locks all filters) |
| `selectedReg` | Selected region from map click (null = all) |
| `BRAND_PINS` | Object mapping brand names to PIN strings |
| `ADMIN_PIN` | Admin access PIN string |
| `IS_ADMIN` | Boolean flag, true only during admin session |
| `CH` | Object storing Chart.js instances for destroy/recreate |

## Field Mapping (Excel → Internal)

| Internal Field | Source Column (2021-2022) | Source Column (2023+) |
|---|---|---|
| date | Billing Date | Billing Date |
| dealer | Name | Customer Name |
| grp | Sales Group | Sales Representative |
| net | Quota Amount / Net Amount | Quota Amount / Net Amount |
| reg | Derived from Delivery Address | Derived from Delivery Address |
| brand | Derived via detectBrand() | Derived via detectBrand() |

## Compressed Data Format

```json
{
  "l": {
    "d": ["dealer names..."],
    "g": ["groups..."],
    "k": ["categories..."],
    "s": ["SKUs..."],
    "p": ["products..."],
    "r": ["regions..."],
    "t": ["departments..."]
  },
  "r": [
    ["2025-01-15", 0, 1, 2, 3, 4, 100, 5000, 4800, 0, 1],
    // [date, dealer_idx, grp_idx, cat_idx, sku_idx, prod_idx, qty, gross, net, reg_idx, dept_idx]
  ]
}
```

## Regions

| Region | Coverage |
|---|---|
| NCR | Metro Manila |
| Central Luzon | Pampanga, Bulacan, Tarlac, Zambales, etc. |
| CALABARZON | Cavite, Laguna, Batangas, Rizal, Quezon |
| North Luzon | Ilocos, CAR, Cagayan Valley |
| Bicol | Camarines, Albay, Sorsogon |
| Visayas | Cebu, Panay, Negros, Leyte, Samar, Bohol |
| Mindanao | Full southern island |

## Design System

| Token | Value |
|---|---|
| Primary Navy | #1b2559 |
| Accent Blue | #0ea5e9 |
| Nav Gradient | #0f172a → #1b2559 → #1e3a5f |
| Success | #059669 |
| Error | #e11d48 |
| Warning | #d97706 |
| Font Primary | Plus Jakarta Sans |
| Font Mono | JetBrains Mono |
| Border Radius | 12px (cards), 8px (inputs), 20px (full) |
