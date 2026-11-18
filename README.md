***"How does spatial clustering of elderly populations correlate with access to acute healthcare services?"***

All the code in this repository aims to answer this research question. 

***Description of repository***

```
.
├── code/
│   ├── .DS_Store
│   ├── Version_1.ipynb --> this is the first version of our code, which we presented in week 8
│   ├── Version_2.ipynb --> this is the second version of our code, which we presented in week 12
│   └── packages.txt --> contains the packages we used to run our code
├── data/
│   ├── processed/ --> this is the data we got after cleaning the census
│   │   ├── ...
│   │   ├── elderly_home_points.gpkg
│   │   ├── subzone_elderly_access.csv
│   │   └── subzone_elderly_access.gpkg
│   └── raw/
│       ├── oex/
│       │   ├── ... --> this is the data we pulled from open street maps.
│       ├── .gitkeep
│       ├── census2020_subzone_dwelling.csv (from Singstats)
│       ├── census_2026_subzone_age_sex.csv (from Singstats)
│       ├── moh_acute_hospitals.csv (created by combining hospital names with their location data)
│       └── mp2019_subzone_no_sea.geojson (from URA)
├── output/
│   ├── figures/
│   │   ├── Version_1/ 
│   │   │   └── ... --> the figures from week 8 are not relevant to our final analysis, but you can look
│   │   ├── Version_2/
│   │   │   ├── 01_map_elderly_share.png
│   │   │   ├── 02_map_distance.png
│   │   │   └── 03_boxplot_distance_by_region.png
│   ├── tables/
│   │   ├── Version_1/
│   │   │   └── ... --> the tables from week 8 are not relevant to our final analysis, but you can look
│   │   ├── Version_2/
│   │   │   ├── course_descriptives.csv
│   │   │   ├── course_elderly_by_distance.csv
│   │   │   ├── course_elderly_by_region.csv
│   │   │   └── course_spearman.csv
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

