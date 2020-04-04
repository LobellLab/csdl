# Corn Soy Data Layer

This repo contains code that walks through the steps to create the Corn-Soy Data Layer (CSDL), a map that classifies corn and soybean in 13 states in the US Midwest from 1999-2018 at 30m resolution. Although the USDA's Cropland Data Layer (CDL) offers crop type maps across the conterminous US from 2008 onward, such maps are missing in many Midwestern states or are uneven in quality before 2008. To fill these data gaps, we used the now-public Landsat archive and cloud computing services to map corn and soybean, the primary crops in the Midwest, back to 1999.

## Dataset

Our dataset can be found on Zenodo at ...

## Code dependencies

* To sample training points: R version 3.5.1, sf 0.6-3, raster 2.6-7, rgdal 1.3-4

* To train our classifier and create the final maps: Google Earth Engine

* To perform analyses: Python

## Map creation

1. Sample a set of training coordinates. [[R Markdown file](TBD)]
2. Export Landsat harmonic regression features and weather features. [[Earth Engine script](TBD)]
3. After feature selection, assemble data into a dataframe for ingestion into GEE. [[Jupyter notebook](TBD)]
4. Train random forest classifier in GEE. [[Earth Engine script](TBD)]

## Map validation and error analysis

1. CSDL versus point-level CDL labels. [[Jupyter notebook](TBD)]
2. Aggregated CSDL versus county-level NASS statistics. [[Jupyter notebook](TBD)]
2. County-level CSDL time trends versus NASS time trends. [[Jupyter notebook](TBD)]
3. Validate CSDL against ARMS crop rotation statistics. [[Jupyter notebook](TBD)]
4. Landsat availability over the years. [[Jupyter notebook](TBD)]

