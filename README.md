# Dynamic Smart Heating Control System

A real-time, energy-aware platform that adjusts building heating based on class schedules and live occupancy. The system combines a FastAPI back end, PostgreSQL data store, and a Next.js dashboard with geospatial heatmaps to reduce energy waste across campus buildings.

---

## Overview

- Real-time occupancy and schedule-aware heating decisions delivered over Server-Sent Events (SSE).
- Interactive campus heatmaps for building- and room-level status.
- Analytics dashboards for classes in session, heater state, and historical occupancy trends.
- Modular architecture separating the FastAPI service (`buildocc-bend`) and Next.js frontend (`buildocc`).

Visual references: Figure 22 (building occupancy dashboard summarizing room utilization) and Figure 25 (current classes cards highlighting active courses and locations).

---

## Repository Structure

- `buildocc-bend/` — FastAPI backend with PostgreSQL integration, SSE streaming, and visualization utilities.
- `buildocc/` — Next.js + React frontend for dashboards, heatmaps, and control panels.

---

## Tech Stack

| Layer    | Languages        | Frameworks / Libraries                                                              | Services / Tooling      |
|----------|------------------|--------------------------------------------------------------------------------------|-------------------------|
| Backend  | Python           | FastAPI, Uvicorn, psycopg[binary], sse-starlette, NumPy, Matplotlib                 | PostgreSQL, StaticFiles |
| Frontend | TypeScript, JS   | Next.js, React, Tailwind CSS, Leaflet, Recharts, Radix UI, clsx, Lucide, React Router DOM | Vercel, ESLint          |

Visual references: Figure 29 (Python runtime snapshot), Figure 30 (FastAPI stack diagram), Figure 31 (back-end interface view).

---

## Features

- Real-time occupancy monitoring via SSE streams.
- Heating logic that combines course schedules with live occupancy signals.
- Interactive campus heatmap with building and room overlays.
- Analytics dashboard with charts for current classes, heater states, and occupancy timelines.
- Backend visualization utilities for diagnostics and reporting.

Visual references: Figure 23 (occupancy timeline for Building 4), Figure 24 (room selection interface), Figure 26 (campus map interface), Figure 27 (heatmap legend), Figure 28 (building occupancy cards), Figures 32 and 33 (heater OFF/ON examples).

---

## Getting Started

### Prerequisites

- Node.js 18+
- Python 3.9+
- PostgreSQL
- npm and pip

### Clone the Repository

```bash
git clone https://github.com/oussenn/CapstoneProject.git
cd CapstoneProject
```

---

## Backend Setup (`buildocc-bend`)

```bash
cd buildocc-bend
python -m venv venv
venv\Scripts\activate          # On macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
python app.py
```

Ensure PostgreSQL is running and the connection settings in the backend configuration match your environment.

---

## Frontend Setup (`buildocc`)

```bash
cd buildocc
npm install
npm run dev
```

Open `http://localhost:3000` to view the dashboard.

---

## Backend Endpoints and Data Flow

- **SSE stream**: Broadcasts occupancy, heater state, and schedule-aligned updates to the frontend.
- **JSON APIs**: Provide building, room, and class data for heatmaps and dashboards.
- **Static assets**: Served for embedded reports and diagnostics.

Visual references: Figure 34 (JSON response for Building 8B Room 108), Figure 35 (HTML output for Building NAB Room 204), Figure 36 (JSON output for Building NAB Room 204), Figure 46 (SSE `/events` response payload).

---

## Heatmaps and Occupancy Scenarios

- Figure 40 — Building 4 Room 104 weekday occupancy dashboard.  
- Figure 41 — Weekday occupancy map across campus.  
- Figure 42 — Building 6 Room 8 weekend occupancy dashboard.  
- Figure 43 — Weekend campus occupancy map showing unoccupied buildings.

---

## Architecture and Hardware

- Figure 38 — System architecture and data pipeline from sensors to dashboards.  
- Figure 37 — Atlantic F117P heater (1000 W) used in the deployment.

---

## Heater State and Analytics

- Figure 44 — Heater OFF state (Building NAB, Room 204).  
- Figure 45 — Heater ON state (Building NAB, Room 204).  
- Figure 47 — Temperature and heater state graph (Test Case 1).  
- Figure 48 — Temperature and heater state graph (Test Case 2).

---

## Directory Details

### `buildocc-bend/`

- `app.py`: FastAPI entry point and service bootstrap.
- `db/`: PostgreSQL connection and query logic.
- `routes/`: REST and SSE endpoints.
- `sse/`: Streaming utilities for real-time updates.
- `static/`: Shared assets for diagnostics and reports.
- `utils/`: Visualization and data helpers (NumPy/Matplotlib).

### `buildocc/`

- `pages/`: Next.js routes and views.
- `components/`: Reusable UI (charts, cards, controls, layout).
- `styles/`: Tailwind and PostCSS configuration.
- `public/`: Static frontend assets.
- `lib/`: Client utilities for fetching SSE/JSON data.

---

## Roadmap

- [x] Class schedule integration via PostgreSQL
- [x] Occupancy dashboard with heatmap overlays
- [x] SSE-based backend streaming
- [ ] Integrated visual gallery page for dashboards, maps, and heater states
- [ ] Sensor-based occupancy via Arduino
- [ ] Comparative analysis of heating modes
- [ ] Thermodynamic modeling by room size
- [ ] External API integration (GoCampus)

---

## Academic Context

Developed as a capstone project at Al Akhawayn University to optimize campus energy consumption by regulating heating based on occupancy patterns and environmental signals.

- Supervisor: Dr. Moulay El Hassan El Azhari
- Co-supervisor: Dr. Ahmed Fiaz
- Project Lead: Oussama Ennaciri

---

## License

Academic and research use. For commercial use, contact the author.

---

## Acknowledgements

- Dr. Moulay El Hassan El Azhari for mentorship and guidance
- Dr. Ahmed Fiaz for co-supervision and technical feedback
- Computer Science and Engineering faculty
- Peers who contributed feedback during testing

---

## Contact

**Oussama Ennaciri**  
o.ennaciri@aui.ma  
Al Akhawayn University
