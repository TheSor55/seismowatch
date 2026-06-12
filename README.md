<div align="center">

<img src="https://raw.githubusercontent.com/github/explore/main/topics/leaflet/leaflet.png" width="60" alt="SeismoWatch"/>

# SeismoWatch

### Realtime Global Earthquake & Tsunami Monitor

[![Live Demo](https://img.shields.io/badge/🔴_Live_Demo-Visit_Site-00d4ff?style=for-the-badge)](https://[your-username].github.io/seismowatch/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)
[![Static HTML](https://img.shields.io/badge/No_Backend-Static_HTML-22c55e?style=for-the-badge)]()
[![Data Sources](https://img.shields.io/badge/Sources-5_APIs-f97316?style=for-the-badge)]()

**Monitor earthquakes and tsunami warnings worldwide in realtime — single HTML file, no server required.**

[🔴 Live Demo](https://[your-username].github.io/seismowatch/) · [🐛 Report Bug](../../issues) · [💡 Request Feature](../../issues)

![SeismoWatch Screenshot](https://via.placeholder.com/900x450/0a0e1a/00d4ff?text=SeismoWatch+Dashboard)

</div>

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔴 **WebSocket Realtime** | Live push from EMSC WebSocket — no polling delay |
| ⏱ **Auto Polling** | Fetches new data every 60 seconds with countdown |
| 🗺 **Interactive Map** | Leaflet + CartoDB Dark tile — zoom, pan, click popups |
| 🔥 **Ring of Fire** | Accurate Pacific Rim overlay from real coordinates |
| 🌊 **Tsunami Warnings** | NOAA/PTWC + GDACS alerts, updated every 2 minutes |
| 📊 **Analytics Drawer** | Magnitude distribution & 24h timeline (collapsible) |
| 🔔 **Smart Alerts** | Toast notifications for M5.0+ and new tsunami warnings |
| 🧹 **Auto Deduplication** | Merges overlapping events across all sources |
| 📱 **Mobile Responsive** | Optimized layout for phones and tablets |
| 🌐 **CORS Fallback** | Multi-proxy chain ensures data loads on GitHub Pages |

---

## 📡 Data Sources

| Source | Protocol | Coverage | Interval |
|--------|----------|----------|----------|
| [USGS](https://earthquake.usgs.gov/fdsnws/) | REST / GeoJSON | Global | 60s |
| [EMSC](https://www.seismicportal.eu) | REST + **WebSocket** | Global / Europe | Realtime |
| [GEOFON](https://geofon.gfz-potsdam.de/fdsnws/) | REST / JSON (proxy) | Global | 60s |
| [NOAA/PTWC](https://www.tsunami.gov) | RSS / XML | Pacific Ocean | 2min |
| [GDACS](https://www.gdacs.org) | RSS / XML | Indian Ocean + Atlantic | 2min |

---

## 🚀 Deploy on GitHub Pages

### Option A — Fork & Enable Pages (easiest)

1. Click **Fork** on this repo
2. Go to **Settings → Pages**
3. Set **Branch: main / Folder: / (root)** → Save
4. Visit `https://[your-username].github.io/seismowatch/` after ~2 minutes

### Option B — Upload your own copy

```bash
# Create a new GitHub repo named "seismowatch"
# Then upload these 3 files:

index.html      ← rename from earthquake_dashboard.html
.nojekyll       ← empty file, prevents Jekyll processing
README.md       ← this file
```

> ⚠️ **Do not skip `.nojekyll`** — without it, GitHub Pages may break JavaScript assets.

---

## 🛠 Tech Stack

```
Leaflet.js  1.9.4  — Interactive map rendering
Chart.js    4.4.1  — Analytics charts
CartoDB           — Dark map tile provider
Vanilla JS ES2020 — All logic, no frameworks
```

No Node.js. No npm. No build step.
Open `index.html` directly in any browser.

---

## 📁 Repository Structure

```
seismowatch/
├── index.html      # Entire dashboard — self-contained, ~100KB
├── .nojekyll       # Disables Jekyll on GitHub Pages
└── README.md       # This file
```

---

## ⚙️ Configuration

Open `index.html` and find these constants near the top of the `<script>` block:

```javascript
// Polling interval (milliseconds)
setInterval(() => fetchAll(), 60000);       // earthquake data — every 60s
setInterval(fetchTsunami, 120000);          // tsunami data   — every 2min

// Alert threshold
const big = newEvs.filter(e => e.mag >= 5.0);  // toast when M5.0+

// Map default view [lat, lng, zoom]
leafletMap = L.map('leafletMap', { center: [20, 10], zoom: 2 });
```

---

## 🤝 Contributing

Contributions are welcome! Areas that would benefit most:

- 🗺 **New data sources** — TMD (Thailand), JMA (Japan), GeoNet (New Zealand)
- 🌐 **i18n support** — English / Thai / Japanese UI toggle  
- 📱 **Mobile UX** — swipe gestures, bottom sheet improvements
- 🎨 **Map themes** — additional tile layer options
- 🔧 **CORS proxy** — self-hosted proxy option for reliability

### How to contribute

```bash
# 1. Fork this repo
# 2. Make changes to index.html
# 3. Open a Pull Request — no build process needed
```

---

## ⚠️ Limitations

- **TMD (Thai Meteorological Dept.)** has no public API — Thai events appear via USGS/EMSC instead
- **GEOFON** has CORS restrictions — data is fetched through a public proxy (may add slight delay)
- **Tsunami warnings** are informational only, sourced from NOAA/GDACS — not an official alert system
- Realtime WebSocket requires an active internet connection — no offline mode

---

## 📄 License

[MIT](LICENSE) — Free to use, modify, and distribute.

---

<div align="center">

**SeismoWatch** is built entirely with open data and open source tools.

Data provided by [USGS](https://earthquake.usgs.gov) · [EMSC](https://www.emsc-csem.org) · [GEOFON](https://geofon.gfz-potsdam.de) · [NOAA/PTWC](https://www.tsunami.gov) · [GDACS](https://www.gdacs.org)

⭐ Star this repo if you find it useful!

</div>
