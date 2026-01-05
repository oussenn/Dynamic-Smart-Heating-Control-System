
<p align="center">
  <img width="1536" height="1024" alt="Logo"
       src="https://github.com/user-attachments/assets/62c251be-bae6-433c-b7f4-8c30bde1b3ac" />
</p>


# Dynamic Smart Heating Control System

A real-time, energy-aware platform that adjusts building heating based on class schedules and live occupancy. The system combines a FastAPI back end, PostgreSQL data store, and a Next.js dashboard with geospatial heatmaps to reduce energy waste across campus buildings.

---

## Overview

- Real-time occupancy and schedule-aware heating decisions delivered over Server-Sent Events (SSE).
- Interactive campus heatmaps for building- and room-level status.
- Analytics dashboards for classes in session, heater state, and historical occupancy trends.
- Modular architecture separating the FastAPI service (`buildocc-bend`) and Next.js frontend (`buildocc`).

Visual references:

<img width="1719" height="862" alt="image" src="https://github.com/user-attachments/assets/1425bedd-184e-4161-b2d0-3d5d21070e02" />

building occupancy dashboard summarizing room utilization.


<img width="270" height="805" alt="image" src="https://github.com/user-attachments/assets/0af6548d-9ef4-4ec3-a8a9-cd0ff23017b1" />

current classes cards highlighting active courses and locations.

---

## Repository Structure

- `buildocc-bend/` — FastAPI backend with PostgreSQL integration, SSE streaming, and visualization utilities.
- `buildocc/` — Next.js + React frontend for dashboards, heatmaps, and control panels.

---

## Tech Stack

| Layer    | Languages        | Frameworks / Libraries                                                              | Services / Tooling      |
|----------|------------------|--------------------------------------------------------------------------------------|-------------------------|
| Backend  | Python           | FastAPI, Uvicorn, psycopg[binary], sse-starlette, NumPy, Matplotlib                 | PostgreSQL, StaticFiles |
| Frontend | JavaScript (some TS)  | Next.js, React, Tailwind CSS, Leaflet, Recharts, Radix UI, clsx, Lucide, React Router DOM | Vercel, ESLint          |


![React](https://github.com/user-attachments/assets/d1feff00-4288-410f-97a4-3f31a9304ec1)   <img width="526" height="526" alt="JavaScript-logo" src="https://github.com/user-attachments/assets/3d95e496-6c76-48f5-a668-8bf1ade4423f" />


<img width="269" height="326" alt="python-logo-only" src="https://github.com/user-attachments/assets/9a711594-f6e0-40ea-9621-adaafacbda8a" />   <img width="405" height="450" alt="pngegg" src="https://github.com/user-attachments/assets/2876d9cd-cf85-4251-8afb-fcdc2a625fa1" />

---

## Features

- Real-time occupancy monitoring via SSE streams.
- Heating logic that combines course schedules with live occupancy signals.
- Interactive campus heatmap with building and room overlays.
- Analytics dashboard with charts for current classes, heater states, and occupancy timelines.
- Backend visualization utilities for diagnostics and reporting.


<img width="954" height="414" alt="image" src="https://github.com/user-attachments/assets/89415451-2bbc-43d0-b21d-220787b1e89d" />
occupancy timeline for Building 4.


<img width="852" height="578" alt="image" src="https://github.com/user-attachments/assets/d569e432-47b0-4ec9-b09f-2778cc8567a4" />

Room selection interface.

<img width="944" height="465" alt="image" src="https://github.com/user-attachments/assets/4f706513-da9e-410a-bf8c-7096766a56f6" />

Campus map interface.


<img width="219" height="222" alt="image" src="https://github.com/user-attachments/assets/8992606a-2c5f-4db8-a0e1-ad2e82b89c2d" />

Heatmap legend.

<img width="949" height="146" alt="image" src="https://github.com/user-attachments/assets/e1f4238b-1c81-41bf-95f5-2760e48d838a" />

Building occupancy cards. 

<img width="901" height="449" alt="image" src="https://github.com/user-attachments/assets/c63fe23f-2ad4-491b-871d-7e4836040752" />

Heater OFF/ON examples.

---

## Getting Started

### Prerequisites

- Node.js 18+
- Python 3.9+
- PostgreSQL
- npm and pip

### Clone the Repository

```bash
git clone https://github.com/oussenn/Dynamic-Smart-Heating-Control-System.git
cd Dynamic-Smart-Heating-Control-System
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



<img width="888" height="278" alt="image" src="https://github.com/user-attachments/assets/ae4cea54-4122-4fe7-b46e-137a652f0348" />


JSON response for Building 8B Room 108. 

<img width="690" height="635" alt="image" src="https://github.com/user-attachments/assets/ae8dd3fa-213b-47ad-b1c0-cc0b1114918a" />


HTML output for Building NAB Room 204. 


<img width="1600" height="202" alt="image" src="https://github.com/user-attachments/assets/745f325b-9a1e-4423-9432-3f01d82da12a" />


JSON output for Building NAB Room 204. 

<img width="1840" height="225" alt="image" src="https://github.com/user-attachments/assets/abab5b40-f087-48f6-98ba-86e746c1e0a5" />

SSE `/events` response payload.

---

## Heatmaps and Occupancy Scenarios


<img width="1750" height="881" alt="image" src="https://github.com/user-attachments/assets/6f2c3e9e-5046-4386-a8de-4e049e7f7f8a" />

Building 4 Room 104 weekday occupancy dashboard.

<img width="1919" height="666" alt="image" src="https://github.com/user-attachments/assets/c7f943fe-20cf-45f2-8ddc-8ee67ae1d475" />

Weekday occupancy map across campus.

<img width="1789" height="852" alt="image" src="https://github.com/user-attachments/assets/b0e8dbad-ff09-4e85-bb1e-df67b215bb14" />


Building 6 Room 8 weekend occupancy dashboard.

<img width="1526" height="734" alt="image" src="https://github.com/user-attachments/assets/80acef4a-081e-4f1e-a4b1-67c378708548" />

Weekend campus occupancy map showing unoccupied buildings.

---

## Architecture and Hardware

<img width="851" height="619" alt="image" src="https://github.com/user-attachments/assets/4d211b94-0072-4c28-8004-d32369b9246b" />


System architecture and data pipeline from sensors to dashboards.


<img width="571" height="505" alt="image" src="https://github.com/user-attachments/assets/a0f79332-02ab-4f2f-bbe7-9c4ad2ee7bc4" />


Atlantic F117P heater (1000 W) used in the deployment.

---

## Heater State and Analytics


<img width="710" height="831" alt="image" src="https://github.com/user-attachments/assets/ba1147c6-6637-4f84-9757-0157e7467028" />


- Figure 44 — Heater OFF state (Building NAB, Room 204).

<img width="812" height="730" alt="image" src="https://github.com/user-attachments/assets/ac4c11de-f2f0-4ad4-bade-b1bdd2d9d1f2" />


- Figure 45 — Heater ON state (Building NAB, Room 204).

<img width="1456" height="723" alt="image" src="https://github.com/user-attachments/assets/1cc780fa-f419-4689-bb38-5a81866bf29e" />

  
- Figure 47 — Temperature and heater state graph (Test Case 1).

<img width="1496" height="736" alt="image" src="https://github.com/user-attachments/assets/e9aab4f1-a4f3-4960-b4b9-d6319e594fa0" />


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
- [ ] Sensor-based occupancy via Arduino
- [ ] Comparative analysis of heating modes
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
