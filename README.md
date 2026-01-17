# demand-responsive-vs.-fixed-stop-bus-operation-for-efficiency-emissions
This project uses Dijkstra’s Algorithm with OpenStreetMap data to optimize school bus routes. It compares fixed-stop and demand-responsive models, analyzing distance efficiency and estimating carbon emission reductions.

**Location**: Upland
Nikhil Pediredla
**Topic**: Comparative Analysis of Fixed-Route Bus vs. Demand-Responsive Transit (DRT)  
**Data Source**: OpenStreetMap (Overpass API)

## Project Overview
This MVP explores the "Efficiency Crossover Point" between traditional busing and microtransit for the Upland, CA corridor (Route 66 / Foothill Blvd). It uses Graph Theory and Geospatial Analysis to determine when a flexible fleet of vans emits less CO2 than a fixed-route CNG bus.

## Features
-   **Real-World Data**: Fetches live bus stop coordinates for Upland via the Overpass API.
-   **Simulation Engine**: Python-based event loop (`upland_sim.py`) comparing Carbon footprints based on EPA emission factors.
-   **Interactive Visualization**: HTML5 Canvas app (`index.html`) visualizing the specific Route 66 bounding box and demand points.
-   **Algorithms**:
    -   **Dijkstra's Algorithm**: For shortest path routing.
    -   **Nearest Neighbor TSP**: For optimizing van pools.

## File Structure
-   `mpl_sim.py`: **Core Simulation Kernel**. Runs the efficiency crossover analysis (CLI).
-   `fetch_osm.py`: **Data Pipeline**. Downloads real coordinates from OpenStreetMap to `upland_data.json`.
-   `script.js`: **Visualization Logic**. Renders the map and handles the frontend simulation loop.
-   `index.html`: **Dashboard**. The user interface for the simulation.
-   `upland_data.json`: **Dataset**. Contains the raw Layout of Route 66 stops and demand nodes.

## Usasge

### 1. Data Refresh (Optional)
To fetch the latest bus stop data from OpenStreetMap:
```bash
python3 fetch_osm.py
```

### 2. Run Efficiency Analysis
To see the mathematical proof of the crossover point:
```bash
python3 upland_sim.py
```

### 3. Launch Visualization
To view the map and animated buses:
```bash
# Start local server
python3 -m http.server 8080

# Open in browser
# http://localhost:8080
```

## Key Findings
-   **Low Demand (< 30 pax/hr)**: DRT Vans are superior, saving ~50-60% CO2.
-   **Crossover Point**: Occurs at roughly **35-40 passengers/hour**.
-   **High Demand**: Fixed Route 66 becomes more efficient due to economies of scale.
