Data Preparation (QGIS) → Database (PostgreSQL+PostGIS) → API (Python/Node.js) → Web Map (Leaflet.js)
```

### QGIS e Setup
- Clean and prepare archaeological site data
- Test spatial queries and styling
- Export to PostgreSQL/PostGIS database


### Architecture
- **Backend:** Python (Flask/FastAPI) or Node.js serves GeoJSON via API
- **Frontend:** Leaflet.js displays the map in the browser
- **Database:** PostGIS stores spatial data

## Two Deployment Approaches

### Option A: Full Stack (Recommended for Complex Needs)

**Architecture:**
```
PostgreSQL+PostGIS (AWS RDS) 
    ↓
Python API (FastAPI/Flask) on AWS Lambda/EC2
    ↓
Leaflet.js frontend (S3 + CloudFront)
```

**When to use:** 
- 500+ sites with filtering/search
- Dynamic data that updates frequently
- Complex queries (date ranges, site types, excavation status)

### Option B: Static GeoJSON (Simpler & Cheaper!) -- Start with this?

**Architecture:**
```
QGIS → Export GeoJSON → Host on S3/GitHub Pages
    ↓
Leaflet.js loads GeoJSON directly in browser
```

**When to use:**
- <500 sites with moderate attribute data
- Data updates monthly or less
- Want minimal infrastructure costs (~$1-5/month)