# HS4002-Corgi-Group-Project

# **HS4002-Corgi-Group-Project**

++**Elderly Healthcare Access in Singapore**++

This repository contains the code and data processing pipeline for the research question

***"How does spatial clustering of elderly populations correlate with access to healthcare services?"***

The goal of this project is to assess whether existing acute health facilities in Singapore are adequately distributed and sufficiently accessible for an ageing society, considering geographical demographics, travel time by public transport, and financial limitations.

++Table of Contents++

1. Definitions
2. Data sources
3. Project Structure
4. Setup
5. Analysis (Reproduction)
6. Key Outputs
7. Limitations

++**Defintions**++

- **Elderly** --> Singaporeans aged 65 and above. Chosen as it is the official benchmark for policies like Age Well SG and Silver Support Scheme.
  - Residents aged 65+ per subzone (SingStat, June 2026). *Note: Data covers Citizens + PRs.*
- **Healthcare Services** --> Acute hospitals (public and private), offering emergency and specialist care required for chronic illnesses. Polyclinics and GPs are excluded.
  - All 20 MOH acute hospitals located via OpenStreetMap (OEX).
- **Accessibility(geographic)** --> Acute hospitals (public and private), offering emergency and specialist care required for chronic illnesses. Polyclinics and GPs are excluded.
  - 
  1. Straight-line distance (km) from home to nearest acute hospital.
  1. Binary classification: Has PT access if a bus/MRT stop is within 400m of home.
- **Financial Limitation** --> Low income
  - Share of residents living in HDB 1–2-room flats (Census 2020), a standard small-area proxy for low income/public rental.

++**Data Sources**++

- **Demographics:** Singapore Census 2020 (via SingStat).
  - Provides resident counts by age group at the planning area and subzone level.
- **Healthcare Facilities:** Ministry of Health (MOH) list of Acute Hospitals (2026),
  - geocoded using OpenStreetMap data via the `oex` tool.
- **Transport Infrastructure:** Land Transport Authority (LTA) DataMall / OpenStreetMap.
  - Provides locations of bus stops and MRT/LRT stations to calculate walking distances.

1. Project structure/Index

```
.
├── code/
│   ├── elderly_healthcare_access.ipynb
│   ├── initial_cleaning.ipynb
│   └── packages.txt
├── data/
│   ├── processed/
│   │   ├── .gitkeep
│   │   ├── elderly_home_points.gpkg
│   │   ├── subzone_elderly_access.csv
│   │   └── subzone_elderly_access.gpkg
│   └── raw/
│       ├── oex/
│       ├── .gitkeep
│       ├── census2020_subzone_dwelling....
│       ├── census_2026_subzone_age_sex...
│       ├── moh_acute_hospitals.csv
│       └── mp2019_subzone_no_sea.geoj...
── output/
│   ├── figures/
│   │   ├── .gitkeep
│   │   ├── 01_elderly_share_and_count.png
│   │   ├── 02_lisa_elderly_share.png
│   │   ├── 03_acute_hospitals.png
│   │   ├── 04_distance_and_pt_access.png
│   │   └── 05_bivariate_lisa_elderly_vs_dis...
│   ── tables/
│       ├── census_clean_long.csv
│       └── census_clean_wide.csv
├── .DS_Store
── README.md
└── git.ignore

```

++**Setup**++

- Key libraries include: `geopandas`, `pandas`, `numpy`, `matplotlib`, `plotnine`, `esda` (for spatial autocorrelation), `libpysal`, and `scipy`.eADCX D CDC
- Preparing Data
  - Ensure the `data/raw/` folder contains the necessary files:
    - `census_2026_subzone_age_sex.csv`
    - `census2020_subzone_dwelling.csv`
    - `mp2019_subzone_no_sea.geojson` (URA Master Plan boundaries)
    - `oex/` folder containing OSM exports for hospitals, transport stops, and residential buildings.
    - `moh_acute_hospitals.csv`

++**Analysis (Reproduction)**++

1. **Clean the census:** Aggregates population data to the subzone level and calculates the share of elderly residents.
2. **Map the elderly population:** Visualizes the spatial distribution of the 65+ population.
3. **Spatial Clustering (LISA):** Calculates Local Indicators of Spatial Association to identify "High-High" (elderly hotspots) and "Low-Low" clusters.
4. **Acute Hospitals:** Maps the location of public and private acute hospitals.
5. **Accessibility Calculation:**

- Calculates straight-line distance from residential building centroids to the nearest hospital.
- Determines public transport accessibility (within 400m walk).

1. **Financial Proxy:** Merges census dwelling data to identify low-income areas (HDB 1-2 room flats).
2. **Correlation Analysis:**

- Spearman correlations between elderly share/income and access metrics.
- Bivariate LISA to explore spatial relationships between elderly density and distance to hospitals.

1. **Priority Subzones:** Identifies areas with high elderly need, poor access, and/or low income.

++**Key Outputs**++

- **Figures:**
  - `01_elderly_share_and_count.png`: Choropleth maps of elderly population share and count.
  - `02_lisa_elderly_share.png`: Map of significant elderly clusters (High-High, Low-Low, etc.).
  - `03_acute_hospitals.png`: Map of hospital locations overlaid with elderly density.
  - `04_distance_and_pt_access.png`: Choropleths showing distance to nearest hospital and % with PT access.
  - `05_bivariate_lisa_elderly_vs_distance.png`: Bivariate cluster map showing the relationship between elderly share and neighbor's distance to hospital.
- **Tables:**
  - `global_moran.csv`: Global Moran’s I statistics for elderly clustering.
  - `spearman_need_vs_access.csv`: Correlation coefficients between need (elderly share, income) and access (distance, PT access).
  - `access_by_lisa_cluster.csv`: Median access metrics broken down by elderly cluster type.
  - `priority_subzones.csv`: List of subzones flagged as high priority due to combined high need and low access.

++**Limitations**++

- **Elderly Definition:** Uses Residents (Citizens + PRs) aged 65+, not just Citizens.
- **Travel Time Proxy:** Uses straight-line distance instead of network-based routing (walking/driving time). This ignores road networks, transfers, and waiting times.
- **PT Access:** Only checks if a stop is within 400m of *home*. It does not verify if that stop connects conveniently to a hospital.
- **Nearest Hospital:** Assumes patients go to the geometrically nearest hospital. In reality, patients may be tied to specific regional health clusters or prefer private/public sectors based on cost/subsidy.
- **Financial Proxy:** Uses all-age dwelling data from 2020 as a proxy for elderly income. It does not account for specific elderly subsidies (Pioneer/Merdeka generations).
- **MAUP (Modifiable Areal Unit Problem):** Results depend on subzone boundaries.

