# Geospatial Commute Flow Dashboard

An interactive geospatial dashboard visualizing Bay Area commute routes using a 3D PyDeck ArcLayer map, built as part of Exercise No. 5 (Big Data Visualization in Geoinformatics) for the Geospatial Big Data Analysis course at Bharati Vidyapeeth Institute of Environment Education and Research (BVIEER), Pune.

## Purpose

The dashboard explores origin-destination commute patterns for downtown San Francisco, answering the question: **where do people who work in downtown San Francisco travel from, and how large are these commute flows?** Each arc on the map connects a home location to a work location, with arc width scaled to the flow magnitude and arc color distinguishing origin from destination. A supporting bar chart ranks the ten largest commute flows to highlight the most significant routes that the map alone cannot easily convey through numbers.

## Dataset

- **Source:** Bay Area commute-route CSV (`bay_area_commute_routes.csv`), loaded directly from a public GitHub-hosted dataset.
- **Filtering:** Records were kept only where both the home and work coordinates fall inside a defined downtown San Francisco bounding box (west: -122.4314, south: 37.7665, east: -122.3871, north: 37.8058).

### Key variables

| Field | Meaning | Use in visualization |
|---|---|---|
| `lng_h` | Home longitude | Source X coordinate |
| `lat_h` | Home latitude | Source Y coordinate |
| `lng_w` | Work longitude | Target X coordinate |
| `lat_w` | Work latitude | Target Y coordinate |
| `S000` | Flow / job count | Arc width and tooltip value |

## Dashboard contents

1. **Interactive 3D Commute Flow Map** (`arc_layer_map.html`) — A PyDeck ArcLayer map where arc width represents the `S000` flow value, orange-red marks home (source) locations, and green marks work (target) locations. The view supports zoom, pan, rotation (bearing), and tilt (pitch), with hover tooltips showing job counts per route.
2. **Top 10 Largest Commute Flows** (`extra_visualization.html`) — An interactive Plotly horizontal bar chart ranking the ten commute routes with the highest `S000` values, giving a precise, readable complement to the spatial map.

Both visualizations are combined into a single landing page, `index.html`, using embedded iframes.

## How to view

- **Live dashboard:** https://smiley1go.github.io/3D_ArcLayer/
- **Analysis notebook (Google Colab):** https://colab.research.google.com/drive/1hnebEnb9V7n2r2aPEo4Nu0oaud3rea88?usp=sharing

Open the live dashboard link in any modern browser. No installation is required — the map and chart are fully interactive (zoom, pan, rotate, hover) directly on the page.

## Repository contents

```
3D_ArcLayer/
├── index.html                  # Dashboard landing page (embeds both visualizations)
├── arc_layer_map.html          # PyDeck 3D ArcLayer commute flow map
├── extra_visualization.html    # Plotly bar chart — top 10 commute flows
├── README.md                   # This file
└── (analysis notebook linked above via Google Colab)
```

## Tools used

- Python, Pandas
- PyDeck (deck.gl ArcLayer)
- Plotly Express
- Google Colab
- GitHub Pages

## Author

Joshby Joshy — M.Sc. Geoinformatics, BVIEER, Pune
Course: Geospatial Big Data Analysis | Course Coordinator: Dr. Aravinth R
