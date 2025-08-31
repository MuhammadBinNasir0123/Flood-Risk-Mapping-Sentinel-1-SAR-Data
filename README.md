# 🌊 Flood Risk Mapping in Pakistan Using Remote Sensing & Change Detection

## 📌 Project Overview  
This project analyzes **monsoon flood risks in Pakistan** using **Google Earth Engine (GEE)** and **Sentinel-1 SAR satellite imagery**.  
The study covers **Layyah, Dadu, and Nowshera**, focusing on:  
- **Before & After Flood Maps (July 2022)**  
- **Change Detection Analysis (2014–2025)**  
- **Urban/Rural vulnerability, terrain impact, and population exposure**  

---

## 🚀 Key Highlights  
- Generated **flood extent maps** using Sentinel-1 SAR data  
- Conducted **flood change detection (2014–2025)** across 3 regions  
- Produced **uniform, report-ready maps** with legends & titles  
- Extracted **data-driven insights** on regional vulnerability  
- Applied findings to **disaster management & resilience planning**  

---

## 🗺️ Regions of Study  
| Region       | Why Selected | Key Findings |  
|--------------|-------------|--------------|  
| **Layyah (Punjab)** | Agricultural hub prone to Indus flooding | High rural exposure, crop damage risk |  
| **Dadu (Sindh)**   | Downstream floodplain, high-risk zone | Severe inundation, displacement hotspots |  
| **Nowshera (KPK)** | Mountain-fed river system | Flash floods, rapid terrain-driven risks |  

---

## 📈 Outputs  
- 🌐 **Before vs After Flood Maps (July 2022)**  
- 🛰️ **Flood Change Detection Maps (2014–2025)**  
- 🎨 **Legends & Standardized Orientation** for comparability  
- 👥 **Population & Terrain overlays** for deeper insights  

---

## 🛠️ Tools & Tech  
- **Google Earth Engine (Code Editor)**  
- **Sentinel-1 SAR Imagery**  
- Optional Python libraries for post-processing:  
  - `geopandas`  
  - `rasterio`  
  - `matplotlib`  

---

🎯 Impact & Applications

Disaster Management → Early response & relief planning

Policy Making → Region-specific preparedness strategies

Agriculture → Crop insurance & water management insights

Urban Planning → Identifying high-risk settlement zones

## 💻 Sample GEE Code Snippet
Here’s a simplified snippet used for **Nowshera (July 2022)** flood mapping:

```javascript
// Define region of interest
var nowshera = ee.Geometry.Rectangle([71.800, 33.900, 72.400, 34.300]);
Map.centerObject(nowshera, 9);

// Load Sentinel-1 SAR image (July 2022)
var nowsheraImage = ee.ImageCollection('COPERNICUS/S1_GRD')
  .filterBounds(nowshera)
  .filterDate('2022-07-01', '2022-07-31')
  .filter(ee.Filter.listContains('transmitterReceiverPolarisation', 'VV'))
  .filter(ee.Filter.eq('instrumentMode', 'IW'))
  .select('VV')
  .mean()
  .clip(nowshera);

