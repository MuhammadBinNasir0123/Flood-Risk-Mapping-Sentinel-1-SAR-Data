# Flood Risk Mapping in Pakistan Using Remote Sensing & Change Detection

A geospatial analysis of monsoon flood risks across three high-vulnerability regions in Pakistan using Google Earth Engine and Sentinel-1 SAR satellite imagery.

---

## Project Overview

This project maps flood extent and detects long-term flood patterns across Layyah, Dadu, and Nowshera — three of Pakistan's most flood-prone regions. Using radar-based SAR imagery, the analysis cuts through cloud cover to produce accurate before/after flood maps and 11-year change detection results.

The findings support disaster management, agricultural planning, and policy-level resilience strategies.

---

## Regions of Study

| Region | Province | Why Selected | Key Finding |
|---|---|---|---|
| Layyah | Punjab | Agricultural hub prone to Indus River flooding | High rural exposure, significant crop damage risk |
| Dadu | Sindh | Downstream floodplain, historically high-risk | Severe inundation, major displacement hotspots |
| Nowshera | KPK | Mountain-fed river system | Flash floods driven by rapid terrain runoff |

---

## Key Outputs

- Before & After flood extent maps — July 2022 monsoon event
- Flood change detection maps — 2014 to 2025 across all three regions
- Population and terrain overlays for vulnerability assessment
- Standardized map layouts with legends for report-ready comparability
- Comprehensive geospatial report with data-driven regional insights

---

## Tools & Technology

| Tool | Purpose |
|---|---|
| Google Earth Engine | Satellite image processing and analysis |
| Sentinel-1 SAR | Radar-based flood mapping (cloud-penetrating) |
| geopandas | Geospatial data handling |
| rasterio | Raster image processing |
| matplotlib | Post-processing visualizations |

---

## Sample GEE Code

```javascript
// Define region of interest
var nowshera = ee.Geometry.Rectangle([71.800, 33.900, 72.400, 34.300]);
Map.centerObject(nowshera, 9);

// Load Sentinel-1 SAR imagery (July 2022)
var nowsheraImage = ee.ImageCollection('COPERNICUS/S1_GRD')
  .filterBounds(nowshera)
  .filterDate('2022-07-01', '2022-07-31')
  .filter(ee.Filter.listContains('transmitterReceiverPolarisation', 'VV'))
  .filter(ee.Filter.eq('instrumentMode', 'IW'))
  .select('VV')
  .mean()
  .clip(nowshera);
```

---

## Applications

- **Disaster Management** — Supports early response and relief coordination
- **Policy Making** — Enables region-specific flood preparedness strategies
- **Agriculture** — Informs crop insurance and water management planning
- **Urban Planning** — Identifies high-risk settlement zones for safer development

---

## Project Structure

```
├── Flood Change Detection Code (2014-2025).js     # GEE script for change detection
├── Flood Change Detection Imagery.pdf             # Output maps — change detection
├── Flood Risk Mapping Code (July 2022).js         # GEE script for 2022 flood mapping
├── Flood Risk Mapping Imagery.pdf                 # Output maps — July 2022 floods
├── Geospatial Flood Risk Assessment (SAR).pdf     # Full analysis report
└── README.md                                      # Project documentation
```

---
