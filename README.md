## 🔗 Live Deployment

<div align="center">
➡️ https://Devikapavithran.github.io/Multi-source-intelligence-fusion-dashboard

Click the link above to open the fully interactive live dashboard in your browser. No login, no installation required.

</div>
---

## 📌 Problem Statement

> **Problem Statement 1 — Multi-Source Intelligence Fusion Dashboard**
>
> In modern intelligence operations, decision-makers are overwhelmed by fragmented data arriving from disparate sources. The inability to view **OSINT**, **HUMINT**, and **IMINT** on a single unified interface leads to delayed reaction times and a critical lack of situational awareness.
>
> Analysts currently toggle between database viewers, spreadsheets, and image galleries — preventing a holistic **"common operating picture."**

### The Core Challenges Addressed
| Challenge | Description |
|-----------|-------------|
| **Fragmented Ingestion** | Data siloed across MongoDB, AWS S3, manual spreadsheets, and image galleries |
| **Geospatial Disconnect** | No unified terrain map to anchor intelligence points to physical locations |
| **Static Visualization** | Existing tools lack interactive hover-activated pop-ups for instant data inspection |

---

##  Objectives Achieved

- ✅ Automated OSINT retrieval from cloud-based storage (MongoDB + S3 simulation)
- ✅ Seamless manual ingestion of field reports via drag-and-drop (CSV / JSON / JPG / JPEG)
- ✅ All intelligence nodes visualized as interactive geospatial markers on a terrain map
- ✅ Hover-and-view functionality providing instant IMINT imagery confirmation via pop-up windows
- ✅ Real-time live feed log simulating continuous intelligence stream updates
- ✅ Multi-dimensional filtering by Priority, Region, and Confidence level

---

##  Dashboard Preview

```
┌─────────────────────────────────────────────────────────────────────┐
│  SF-DASH v2.1    STRATEGIC INTELLIGENCE FUSION DASHBOARD   [LIVE]  │
├──────────────┬──────────────────────────────────────┬───────────────┤
│ INTELLIGENCE │                                      │  NODE         │
│ SOURCES      │         TERRAIN MAP                  │  INSPECTOR    │
│              │                                      │               │
│ ● OSINT  12  │   · SECTOR ALPHA                     │  [OSI-001]    │
│ ● HUMINT  7  │         ◉ ·  ·    · SECTOR BRAVO     │  LABEL: ...   │
│ ● IMINT   5  │    ·  ◉      ◉  ·                   │  CONF: HIGH   │
│              │  ·       ·      ·  SECTOR CHARLIE    │  REGION: ...  │
│ FILTERS      │       ·    ◎      ·    ◉             │  [IMINT IMG]  │
│ PRIORITY ▾   │                                      │               │
│ REGION   ▾   │  LAT: 28.6741°N  LON: 77.1021°E     │  LIVE FEED    │
│ CONF.    ▾   │                              + − ⊙  │  LOG...       │
├──────────────┴──────────────────────────────────────┴───────────────┤
│  [↓ EXPORT]  [↻ REFRESH]  [⊗ CLEAR]  [⚠ ALERT ALL]               │
└─────────────────────────────────────────────────────────────────────┘
```

---

##  Features & Functional Requirements

### 1. 📡 Multi-Source Data Ingestion
| Source | Type | Status |
|--------|------|--------|
| MongoDB | OSINT — NoSQL Database Stream | ✅ Simulated Live |
| AWS S3 | OSINT — Cloud Object Storage | ✅ Simulated Live |
| CSV Upload | HUMINT — Field Reports | ✅ Drag & Drop Ready |
| JSON Upload | HUMINT — Structured Reports | ✅ Drag & Drop Ready |
| JPG / JPEG | IMINT — Satellite / UAV Imagery | ✅ Drag & Drop Ready |

### 2. 🗺️ Geospatial Map Interface
- Fixed terrain map rendered in SVG with coordinate grid overlay
- Three operational sectors: **ALPHA**, **BRAVO**, **CHARLIE**
- Real-time LAT/LON coordinate HUD that updates as the cursor moves
- Zoom In / Zoom Out / Reset View controls
- Animated scan-line overlay for operational feel
- All 24 pre-loaded intelligence nodes accurately positioned by latitude/longitude

### 3. 🔴 Intelligence Node Visualization
| Node Type | Color | Count | Description |
|-----------|-------|-------|-------------|
| OSINT | 🔵 Cyan | 12 | Open-source signal nodes |
| HUMINT | 🟢 Green | 7 | Human intelligence field reports |
| IMINT | 🟡 Amber | 5 | Satellite / UAV imagery nodes |
| ALERT | 🔴 Red (pulsing) | 3 | High-priority flagged nodes |

Each node renders with:
- Glowing dot with glow filter effect
- Targeting crosshair reticle lines
- Pulsing ring animation for alert nodes
- Smooth hover scale-up interaction

### 4. 🖱️ Hover-and-View Interactivity
The flagship feature — hovering over any intelligence node instantly triggers a **pop-up tooltip** showing:
- Intelligence type badge (OSINT / HUMINT / IMINT)
- Node ID and label
- Confidence level, Region, Source, Priority
- **For IMINT nodes**: A live-rendered satellite imagery thumbnail with target lock reticle, resolution metadata (GSD: 0.5m), and coordinate overlay — all generated dynamically without leaving the map view

### 5. 🔍 Node Inspector Panel (Right Panel)
Clicking any node populates the full inspector with:
- Complete metadata table (ID, Label, Region, Priority, Source, Timestamp, Coordinates)
- Full-resolution IMINT imagery canvas for satellite nodes
- Target lock reticle with GSD and coordinate burn-in
- Intelligence summary text

### 6. 📋 Live Feed Log
- Auto-scrolling event log in the bottom-right panel
- Simulates real-time intelligence stream updates every 6 seconds
- Color-coded by source type (cyan=OSINT, green=HUMINT, amber=IMINT, grey=SYS)
- Manual **Refresh** button triggers a full poll cycle with log output

### 7. 🔧 Filters & Controls
| Filter | Options |
|--------|---------|
| Priority | ALL / HIGH / MEDIUM / LOW |
| Region | ALL SECTORS / ALPHA / BRAVO / CHARLIE |
| Confidence | ALL / HIGH / MEDIUM / LOW |

Filters apply instantly — the **Visible** stat counter updates in real time.

### 8. 📤 Export
- Clicking **EXPORT** downloads all current node data as a structured `intel_export_[timestamp].json` file
- Contains: node ID, type, coordinates, confidence, priority, label

---

## 🏗️ Technical Architecture

```
┌─────────────────────────────────────────────┐
│           SF-DASH v2.1 Architecture         │
├─────────────────────────────────────────────┤
│                                             │
│  Data Layer          Visualization Layer    │
│  ──────────          ─────────────────      │
│  OSINT (MongoDB)  →  SVG Terrain Map        │
│  OSINT (S3)       →  Geospatial Nodes       │
│  HUMINT (CSV)     →  Hover Tooltips         │
│  HUMINT (JSON)    →  Node Inspector         │
│  IMINT (JPG)      →  Canvas IMINT Render    │
│                                             │
│  Interaction Layer   Feed Layer             │
│  ─────────────────   ──────────             │
│  Source Toggles   →  Live Log Stream        │
│  Filters          →  Alert System           │
│  Zoom/Pan         →  Export Engine          │
│  Drag & Drop      →  Auto Node Placement    │
│                                             │
└─────────────────────────────────────────────┘
```

### Tech Stack
| Layer | Technology |
|-------|------------|
| Markup | HTML5 |
| Styling | CSS3 with CSS Custom Properties (variables) |
| Logic | Vanilla JavaScript (ES6+) |
| Map Rendering | SVG (Scalable Vector Graphics) |
| Imagery Simulation | HTML5 Canvas API |
| Fonts | Google Fonts — Share Tech Mono, Exo 2 |
| Hosting | GitHub Pages |

### Design Principles Applied
- **Zero dependencies** — no external JS libraries, no frameworks, no CDN scripts
- **Single file deployment** — entire application in one `index.html`
- **Responsive rendering** — SVG and layout redraws on window resize
- **Procedural IMINT generation** — satellite imagery thumbnails generated via seeded Canvas API rendering for each unique node
- **Real-time simulation** — live feed log updates, animated scan lines, pulsing alert nodes

---

## 📂 Project Structure

```
Multi-source-intelligence-fusion-dashboard/
│
└── index.html          # Complete application — HTML + CSS + JS in one file
└── README.md           # Project documentation (this file)
```

---

## 🚀 How to Run Locally

No server or installation needed.

```bash
# Option 1 — Just double-click
Open index.html in any modern browser (Chrome, Firefox, Edge)

# Option 2 — Using VS Code Live Server
code .
# Right-click index.html → Open with Live Server
```

**Browser Compatibility:** Chrome 90+ | Firefox 88+ | Edge 90+ | Safari 14+

---

## 📊 Intelligence Node Dataset

The dashboard comes pre-loaded with **24 intelligence nodes** across all three types:

| ID Range | Type | Count | Regions |
|----------|------|-------|---------|
| OSI-001 to OSI-012 | OSINT | 12 | ALPHA, BRAVO, CHARLIE |
| HUM-001 to HUM-007 | HUMINT | 7 | ALPHA, BRAVO, CHARLIE |
| IMI-001 to IMI-005 | IMINT | 5 | ALPHA, BRAVO, CHARLIE |

**Alert Nodes (HIGH Priority — pulsing red):** OSI-001, OSI-004, OSI-006

---

## 🔐 Security & Classification

```
╔══════════════════════════════════════════╗
║  CLASSIFICATION: DEMONSTRATION / RESTRICTED  ║
║  This dashboard is a prototype built for   ║
║  evaluation purposes only. All data,       ║
║  coordinates, and imagery are simulated.   ║
╚══════════════════════════════════════════╝
```

- All node data, coordinates, and imagery are **fully simulated**
- No real intelligence data, classified information, or sensitive coordinates are used
- Imagery is procedurally generated via Canvas API — no real satellite data

---

## 👨‍💻 Developer

**Built by:** Devikapavithran  
**Role:** Senior Cybersecurity Engineer & Full-Stack Developer  
**Submission for:** Multi-Source Intelligence Fusion Dashboard (Problem Statement 1)  
**Stack:** HTML5 · CSS3 · Vanilla JavaScript · SVG · Canvas API · GitHub Pages  

---

## 📋 Functional Requirements Checklist

| Requirement | Status |
|-------------|--------|
| MongoDB OSINT ingestion support | ✅ Implemented (simulated stream) |
| AWS S3 OSINT ingestion support | ✅ Implemented (simulated stream) |
| Manual CSV upload ingestion | ✅ Drag & Drop functional |
| Manual JSON upload ingestion | ✅ Drag & Drop functional |
| JPG/JPEG image upload (IMINT) | ✅ Drag & Drop + auto node placement |
| High-fidelity terrain map | ✅ SVG terrain with sectors & grid |
| Latitude/longitude dot markers | ✅ All 24 nodes precisely placed |
| Hover-activated pop-up modal | ✅ Tooltip with full metadata |
| IMINT imagery in hover pop-up | ✅ Canvas-rendered satellite thumbnail |
| Source toggle (OSINT/HUMINT/IMINT) | ✅ Per-type toggle buttons |
| Multi-filter system | ✅ Priority + Region + Confidence |
| Live feed log | ✅ Auto-updating every 6 seconds |
| Data export | ✅ JSON download |
| Alert system | ✅ Pulsing red nodes + broadcast |
| Zoom controls | ✅ +/− /Reset |
| Real-time coordinate HUD | ✅ Live LAT/LON on cursor move |

---

<div align="center">

**⭐ If this project was useful, consider starring the repository**

`SF-DASH v2.1` · Built with precision · Deployed on GitHub Pages

</div>
