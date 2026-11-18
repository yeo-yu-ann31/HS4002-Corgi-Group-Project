***"How does spatial clustering of elderly populations correlate with access to acute healthcare services?"***

All the code in this repository aims to answer this research question. 

***Description of repository***

```
.
├── code/
│   ├── Version_1.ipynb --> this is the first version of our code, which we presented in week 8
│   ├── Version_2.ipynb --> this is the second version of our code, which we presented in week 12
│   └── packages.txt --> contains the packages we used to run our code
├── data/
│   ├── processed/ --> this is the data we got after cleaning the census
│   └── raw/
│       ├── oex/ --> this is the data we pulled from open street maps.
│       ├── census2020_subzone_dwelling.csv (from Singstats)
│       ├── census_2026_subzone_age_sex.csv (from Singstats)
│       ├── moh_acute_hospitals.csv (created by combining hospital names with their location data)
│       └── mp2019_subzone_no_sea.geojson (from URA)
├── output/
│   ├── figures/
│   │   ├── Version_1/ --> the figures from week 8 are not relevant to our final analysis, but you can look if curious
│   │   ├── Version_2/
│   │   │   ├── 01_map_elderly_share.png --> choropleth map of elderly share by subzone
│   │   │   ├── 02_map_distance.png --> choropleth map of distance of elderly to nearest hospital
│   │   │   └── 03_boxplot_distance_by_region.png --> boxplot of distance of elderly to nearest hospital by region
│   ├── tables/
│   │   ├── Version_1/ --> again you can look if curious
│   │   ├── Version_2/
│   │   │   ├── course_descriptives.csv --> shows summary statistics and skewness
│   │   │   ├── course_elderly_by_distance_band.csv --> shows the distance of different elderly to the nearest hospital
│   │   │   ├── course_elderly_by_region.csv --> shows the % of elderly per region
│   │   │   └── course_spearman.csv --> spearman correlations between elderly concentration and access
│   ├── census_clean_long.csv
│   └── census_clean_wide.csv
├── .DS_Store
├── README.md
└── git.ignore

```

***Order in which to run notebooks***

1. Run code/Version_1.ipynb.
- This notebook shows you the initial analysis we conducted in week 8. After feedback from Professor Ma, we decided to shift our focus from spatial analysis to OLS and logit regression instead.
- What is important to look at here is how we cleaned the census (Section 1), as well as how the geographical datasets were created (see Section 2). Please do also take notice of the variables created here, as they are re-used in the next notebook.
  
2. Run code/Version_2.ipynb.
- This notebook shows our final analysis, which is meant to accompany our final report.

