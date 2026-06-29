# Flood Risk Mapping in Pakistan Using Remote Sensing & Change Detection

A geospatial analysis of monsoon flood vulnerability across three high-risk districts in Pakistan using Google Earth Engine and Sentinel-1 SAR satellite imagery. The study combines July 2022 flood extent mapping with 11-year change detection (2014–2025) to support disaster management and resilience planning.

---

## Regions of Study

| Region | Province | Key Vulnerability | Critical Finding |
|---|---|---|---|
| Layyah | Punjab | Indus River overflow, irrigation breaches | Moderate-to-high flood increase in southern zones |
| Dadu | Sindh | Flat terrain, poor drainage, 2022 super floods | Most critical zone, persistent inundation since 2022 |
| Nowshera | KPK | Kabul & Swat rivers, urban expansion | Expanding floodplain with lateral spread over 11 years |

---

## Key Findings

**July 2022 Flood Risk Mapping**
- Layyah: moderate-to-high SAR reflectance along the Indus belt indicating riverine flooding
- Dadu: deep inundation patterns across a wide floodplain, aligns with reports of 70%+ land submersion at peak
- Nowshera: high reflectance along Kabul River floodplain extending into urban and peri-urban zones

**Change Detection (2014–2025)**
- Layyah: moderate surface water increase, driven by intensified monsoon cycles and irrigation failures
- Dadu: significant increase in persistent flood zones, poor post-flood drainage rehabilitation evident
- Nowshera: visible lateral spread of floodplain activity reflecting higher upstream rainfall frequency

---

## Live GEE Code

**Flood Risk Mapping, July 2022**
- [Nowshera](https://code.earthengine.google.com/5ed4681223e5f6ebddd9a04918f7a0f6)
- [Dadu](https://code.earthengine.google.com/eab40dd4883a577579e3a8966b18bd72)
- [Layyah](https://code.earthengine.google.com/f4e357b713cf5be1e00a247facaca36e)

**Flood Change Detection, 2014–2025**
- [Nowshera](https://code.earthengine.google.com/047eaeae1e3c94ca2bb3cf406fd29c72)
- [Dadu](https://code.earthengine.google.com/4e9ad907dad2bd1eeec365396ccebcdc)
- [Layyah](https://code.earthengine.google.com/96ed8c59afcb21ec9f39561673fc3234)

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

## Tools & Technology

| Tool | Purpose |
|---|---|
| Google Earth Engine | Satellite image processing and flood analysis |
| Sentinel-1 SAR | Radar-based imagery, penetrates cloud cover |
| geopandas | Geospatial data handling |
| rasterio | Raster image processing |
| matplotlib | Post-processing visualizations |

---

## Outputs

| File | Description |
|---|---|
| Flood Risk Mapping Imagery.pdf | SAR maps for all 3 regions, July 2022 |
| Flood Change Detection Imagery.pdf | 11-year change maps for all 3 regions (2014–2025) |
| Geospatial Flood Risk Assessment.pdf | Full report with methodology, findings, and citations |

---

## Applications

- Disaster Management: early response and relief coordination
- Policy Making: region-specific flood preparedness strategies
- Agriculture: crop insurance and water management planning
- Urban Planning: identifying high-risk settlement zones

---

## Project Structure

```
├── Flood Risk Mapping Imagery.pdf
├── Flood Change Detection Imagery.pdf
├── Geospatial Flood Risk Assessment (SAR Analysis).pdf
└── README.md
```

---
