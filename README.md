# 🛰️ SmartNav-API (Peninsular Malaysia Edition)

"Static Geospatial API for SmartNav 2050. Optimized POI and Road networks for Peninsular Malaysia. Designed for offline GPS navigation devices and PWA integration."

## 🚀 Key Features
* **Data Source**: OpenStreetMap (OSM) Malaysia, Singapore, and Brunei.
* **Format**: GeoJSON & Vector Tiles (PWA Optimized).
* **Focus Area**: Peninsular Malaysia (Roads & POIs).
* **Offline Ready**: Built for aggressive Service Worker caching.

## 📁 Data Structure
* `/data/semenanjung-poi.json`: Contains curated POIs (Fuel Stations, Hospitals, Convenience Stores).
* `/data/semenanjung-roads.json`: Road network graph for turn-by-turn routing logic.

## 🛠️ Data Processing Guide
If you have the `malaysia-latest.osm.pbf` file, use **Osmium Tool** to update the API:

1. **Filter POIs:**
```bash
osmium tags-filter malaysia-latest.osm.pbf n/amenity=fuel,hospital n/shop=convenience -o data/semenanjung-poi.json --overwrite

2. Filter Road Networks:

osmium tags-filter malaysia-latest.osm.pbf w/highway=primary,secondary,tertiary -o data/semenanjung-roads.json --overwrite
```

📡 API Integration
Access this data in your application using the Fetch API:
const API_URL = '[https://raw.githubusercontent.com/aimanrafee/SmartNav-API/main/data/semenanjung-poi.json](https://raw.githubusercontent.com/aimanrafee/SmartNav-API/main/data/semenanjung-poi.json)';

fetch(API_URL) ```bash
  .then(res => res.json())
  .then(data => console.log("SmartNav Data Loaded Successfully")); ```

  📜 License & Attribution
Data provided by © OpenStreetMap contributors. This project is licensed under the Open Database License (ODbL).
