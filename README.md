# 📊 Day Parting Dashboard — Amazon Orders

A single-file, zero-dependency analytics dashboard for Amazon sellers. Upload your order report and instantly analyze performance by hour, day of week, timezone, geography, product, and channel — all in a clean pastel UI.

![Dashboard Preview](assets/preview.png)

---

## ✨ Features

### 6 Dashboard Views

| View | Description |
|------|-------------|
| **Overview** | Hourly + DOW bar charts, weekday vs weekend comparison, top 5 converting hours |
| **Hour Heatmap** | Day-of-week × hour matrix with peak highlights and timezone insights |
| **Geography** | U.S. choropleth state map + top 25 cities table |
| **Products** | Revenue, orders, units, and AOV by ASIN and SKU |
| **Channels** | Fulfillment (FBA vs FBM) and sales channel donut charts + tables |
| **Trends** | Daily orders timeline, daily revenue timeline, rolling 7-day hourly pattern |

### Key Capabilities

- **Foolproof timezone conversion** — all times derived from raw UTC milliseconds, no browser locale interference. Switch between Pacific, Mountain, Central, and Eastern and every chart updates instantly.
- **State name normalization** — merges all Amazon report variants (`California`, `CALIFORNIA`, `Ca`, `ca`, `CA`) into standard 2-letter abbreviations automatically.
- **Smart file parsing** — auto-detects tab-delimited (`.txt`) and comma-delimited (`.csv`) Amazon order report formats.
- **Live filters** — Timezone, Date Range, ASIN, SKU, Fulfillment Channel, Sales Channel, and State all update every visual simultaneously.
- **Heatmap insights** — automatically surfaces busiest day, top 3 peak hours, best day+hour combo, and slowest day in the selected timezone.

---

## 🚀 Getting Started

### Requirements

None. This is a single HTML file — no build tools, no npm, no server required.

External libraries are loaded via CDN:
- [Chart.js 4.4.1](https://www.chartjs.org/) — charts
- [PapaParse 5.4.1](https://www.papaparse.com/) — CSV/TSV parsing
- [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans) — typography (Google Fonts)

### Installation

```bash
git clone https://github.com/your-username/dayparting-dashboard.git
cd dayparting-dashboard
```

Then open `dayparting-dashboard.html` in any modern browser. No server needed.

### File Structure

```
dayparting-dashboard/
├── dayparting-dashboard.html   # Main dashboard (self-contained)
├── favicon-v3.png              # Browser tab icon (place in same folder)
├── README.md                   # This file
└── assets/
    └── preview.png             # Optional screenshot for README
```

> **Important:** `favicon-v3.png` must be in the same directory as the HTML file for the tab icon to appear.

---

## 📂 Uploading Your Data

1. Open the dashboard — the upload modal appears automatically.
2. Click **Choose File** or drag and drop your Amazon order report.
3. Supported formats:
   - **Tab-delimited `.txt`** — standard Amazon Seller Central order report
   - **Comma-delimited `.csv`** — any CSV export with the same headers

### Required Column Headers

The dashboard expects standard Amazon order report columns:

| Column | Used For |
|--------|----------|
| `amazon-order-id` | Order count (deduplication) |
| `purchase-date` | All time-based analysis (UTC ISO 8601) |
| `fulfillment-channel` | FBA vs FBM breakdown |
| `sales-channel` | Channel performance |
| `asin` | Product-level analysis |
| `sku` | SKU-level analysis |
| `quantity` | Units sold |
| `item-price` | Revenue calculation |
| `ship-city` | City-level geo table |
| `ship-state` | State choropleth map |
| `order-status` | Displayed in filter options |

To download your order report from Seller Central:
> **Reports → Fulfillment → Amazon Fulfilled Shipments** or **Orders → Order Reports**

---

## 🔍 Filters

All filters apply simultaneously across every view.

| Filter | Options |
|--------|---------|
| **Timezone** | Pacific (UTC−8), Mountain (UTC−7), Central (UTC−6), Eastern (UTC−5) |
| **Date From / To** | Calendar date range picker |
| **ASIN** | Populated from your data |
| **SKU** | Populated from your data |
| **Fulfillment Channel** | Amazon (FBA), Merchant (FBM), etc. |
| **Sales Channel** | Amazon.com, Non-Amazon, etc. |
| **State** | All normalized U.S. state abbreviations |

---

## 📐 Metrics Defined

| Metric | Formula |
|--------|---------|
| **Total Orders** | Count of unique `amazon-order-id` values |
| **Units Sold** | Sum of `quantity` |
| **Revenue** | Sum of `item-price × quantity` |
| **AOV** | Revenue ÷ Total Orders |

---

## 🎨 Design System

| Token | Value |
|-------|-------|
| Background | `#FAFAFA` |
| Card | `#FFFFFF` |
| Text | `#333333` |
| Accent Blue | `#A7C7E7` |
| Accent Green | `#BEE3DB` |
| Accent Purple | `#D8B4E2` |
| Accent Peach | `#FFD6C9` |
| Accent Yellow | `#FFF3B0` |
| Font | Plus Jakarta Sans (Google Fonts) |
| Mono Font | DM Mono (Google Fonts) |

---

## 🌐 Browser Support

| Browser | Support |
|---------|---------|
| Chrome 90+ | ✅ Recommended |
| Firefox 88+ | ✅ |
| Safari 14+ | ✅ |
| Edge 90+ | ✅ |
| Internet Explorer | ❌ Not supported |

---

## 🔒 Privacy

All data processing happens **entirely in your browser**. No order data is ever uploaded to any server — the file is parsed locally using JavaScript and never leaves your machine.

---

## 📅 Changelog

### v1.0.0
- Initial release
- 6-view dashboard: Overview, Heatmap, Geography, Products, Channels, Trends
- Foolproof UTC timezone conversion for all 4 U.S. time zones
- State name normalization (full names, abbreviations, mixed case)
- U.S. SVG choropleth map with hover tooltips
- Heatmap insights panel (busiest day, top hours, slowest day)
- Auto-detecting CSV/TSV file parser with drag-and-drop upload
- Favicon support (`favicon-v3.png`)

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first.

```bash
# Fork the repo, then:
git checkout -b feature/your-feature
git commit -m "Add your feature"
git push origin feature/your-feature
# Open a Pull Request
```

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

*Built for Amazon sellers who want fast, local, no-login analytics.*
