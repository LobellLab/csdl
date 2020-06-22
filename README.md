# Corn Soy Data Layer

This repo contains code that walks through key steps to create and validate the Corn-Soy Data Layer (CSDL), a map that classifies corn and soybean in 13 states in the US Midwest from 1999-2018 at 30m resolution. Although the USDA's Cropland Data Layer (CDL) offers crop type maps across the conterminous US from 2008 onward, such maps are missing in many Midwestern states or are uneven in quality before 2008. To fill these data gaps, we used the now-public Landsat archive and cloud computing services to map corn and soybean, the primary crops in the Midwest, back to 1999.

## Dataset

Our dataset can be accessed through one of two ways:
- Google Earth Engine asset [here](https://code.earthengine.google.com/?asset=projects/lobell-lab/us_croptype_hindcast/CSDL)
- Zenodo repo housing GeoTIFFs [here](https://zenodo.org/record/3742743#.XoxGc9NKhTY)

When using the dataset, please cite: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3742743.svg)](https://doi.org/10.5281/zenodo.3742743)

## Code dependencies

* To sample training points: R version 3.5.1, dplyr 0.8.0.1, sf 0.6-3, raster 2.6-7, rgdal 1.3-4, salustools 0.1.0, sp 1.3-1

* To train our classifier and create the final maps: Google Earth Engine

* To perform analyses: Python 3.7.3, numpy 1.16.4, pandas 0.24.2, matplotlib 3.1.0, sklearn 0.21.2,  plotly 4.5.0

## Map creation

1. Sample a set of training coordinates. [[R Markdown file](https://github.com/LobellLab/csdl/blob/master/create_map/1_sampleTrainingGrid.Rmd)]
2. Export Landsat harmonic regression features. [[Earth Engine script](https://code.earthengine.google.com/?scriptPath=users%2Fsherrie%2Fcsdl%3A1_exportLandsatHarmonics)]
3. After feature selection, assemble data into a dataframe for ingestion into GEE. [[Jupyter notebook](https://github.com/LobellLab/csdl/blob/master/create_map/3_assembleDataFrame.ipynb)]
4. Train random forest classifier in GEE. [[Earth Engine script](https://code.earthengine.google.com/?scriptPath=users%2Fsherrie%2Fcsdl%3A4_createClassifiedMap)]

## Map validation and error analysis

1. Aggregated CSDL versus county-level NASS statistics. [[Jupyter notebook](https://github.com/LobellLab/csdl/blob/master/validate_map/1_NASSvsCSDLvsCDL.ipynb)]
2. County-level CSDL time trends versus NASS time trends. [[Jupyter notebook](https://github.com/LobellLab/csdl/blob/master/validate_map/2_countyTimeTrends.ipynb)]
3. Validate CSDL against ARMS crop rotation statistics. [[Jupyter notebook](https://github.com/LobellLab/csdl/blob/master/validate_map/3_cropRotation.ipynb)]
4. Landsat availability over the years. [[Jupyter notebook](https://github.com/LobellLab/csdl/blob/master/validate_map/4_LandsatAvailability.ipynb)]

