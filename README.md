# 🛰️ SmartNav-API (Peninsular Malaysia Edition)

**SmartNav-API** is a static geospatial database optimized for the **SmartNav 2050** navigation system. This API is designed to function 100% offline for GPS-enabled devices using a lightweight data structure.

## 🚀 Key Features
- **Data Source**: OpenStreetMap (OSM) Malaysia, Singapore, and Brunei.
- **Format**: GeoJSON & Vector Tiles (PWA Optimized).
- **Focus Area**: Peninsular Malaysia (Roads & POIs).
- **Offline Ready**: Built for aggressive Service Worker caching.

## 📁 Data Structure
- `/data/semenanjung-poi.json`: Contains curated POIs (Fuel Stations, Hospitals, Convenience Stores).
- `/data/semenanjung-roads.json`: Road network graph for turn-by-turn routing logic.

## 🛠️ Data Processing Guide
If you have the `malaysia-latest.osm.pbf` file, use **Osmium Tool** to update the API:

1. **Filter POIs:**
   ```bash
   osmium tags-filter malaysia-latest.osm.pbf n/amenity=fuel,hospital n/shop=convenience -o data/semenanjung-poi.json --overwrite
