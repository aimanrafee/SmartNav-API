"Static Geospatial API for SmartNav 2050. Optimized POI and Road networks for Peninsular Malaysia. Designed for offline GPS navigation devices and PWA integration.

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

2. **Filter Road Networks:**
   ```bash
   osmium tags-filter malaysia-latest.osm.pbf w/highway=primary,secondary,tertiary -o data/semenanjung-roads.json --overwrite

📡 API Integration
Access this data in your application using the Fetch API:
const API_URL = '[https://raw.githubusercontent.com/](https://raw.githubusercontent.com/)[YOUR_USERNAME]/SmartNav-API/main/data/semenanjung-poi.json';

fetch(API_URL)
  .then(res => res.json())
  .then(data => console.log("SmartNav Data Loaded Successfully"));

  📜 License & Attribution
Data provided by © OpenStreetMap contributors.

This project is licensed under the Open Database License (ODbL).

---

### 3. Repository Description (For GitHub About Section)
> "Static Geospatial API for SmartNav 2050. Optimized POI and Road networks for Peninsular Malaysia. Designed for offline GPS navigation devices and PWA integration."

---

### 4. Updated `app.js` Logic (English Version)
Here is how your app will interact with your new API:

```javascript
// Function to search for POIs from your own GitHub API
async function searchCustomAPI(query) {
    statusEl.innerText = `Searching local DB: ${query}...`;
    
    try {
        const response = await fetch('https://raw.githubusercontent.com/[YOUR_USERNAME]/SmartNav-API/main/data/semenanjung-poi.json');
        const data = await response.json();
        
        // Find the location in your JSON file
        const destination = data.features.find(item => 
            item.properties.name && item.properties.name.toLowerCase().includes(query.toLowerCase())
        );

        if (destination) {
            const coords = destination.geometry.coordinates;
            map.flyTo({ center: coords, zoom: 17, pitch: 75 });
            speak(`Destination found: ${destination.properties.name}`);
        } else {
            statusEl.innerText = "Location not found in Offline API";
        }
    } catch (err) {
        console.error("API Error:", err);
    }
}
