# Data Visualization Projects — Python and R

## Overview

This repository brings together two projects.

The first project explores the geographic distribution of the U.S. population at county level using NHGIS census data. 
The second investigates temperature and mortality patterns in Italy between 2015 and 2024 by combining climate and mortality datasets.

Together, these projects demonstrate the use of data visualization for both **spatial analysis** and **time-series analysis**, as well as
the integration of visualization with data preparation, statistical modeling and interactive exploration.

---

## Projects

### 1. U.S. County Population Visualization

**Objective**

Analyze the distribution of the U.S. population across counties in 2010, with a particular focus on racial composition and geographic differences.

**Data**

The project uses:

* **NHGIS** population data for 2010
* County-level geographic data
* Population counts by racial group
* Geographic identifiers used to connect demographic and spatial data

The analysis covers the 48 contiguous U.S. states and includes **3,108 counties** after geographic filtering.

**Main analyses and visualizations**

* Population distribution in Los Angeles County
* Absolute and relative population comparisons by racial group
* Static county-level choropleth maps
* Interactive geographic visualization with **Folium**
* Interactive dashboard with **Panel**
* State and county selection for dynamic exploration

**Data processing**

The workflow includes:

* Data extraction through the NHGIS API
* Data cleaning and transformation with Pandas
* Geographic data processing with GeoPandas
* Spatial joining of population and geographic datasets
* Correction of invalid geometries
* Classification of population values for choropleth mapping

### 2. Temperature and Mortality in Italy

**Objective**

Study the relationship between climatic conditions and mortality in Italy over the period **2015–2024**, combining temperature data with weekly mortality data.

**Data**

The project combines:

* **ERA5 reanalysis** temperature data
* 2-meter air temperature measurements
* **World Mortality Dataset**
* Weekly mortality data for Italy

The analysis covers Italy between **2015 and 2024**, with a specific focus on summer 2022.

**Main analyses and visualizations**

* Daily temperature analysis for summer 2022
* Weekly temperature aggregation from 2015 to 2024
* Spatial temperature maps
* Temperature time-series visualizations
* Weekly mortality trends
* Expected mortality estimation
* Excess mortality analysis
* Exploration of the relationship between temperature and mortality

**Statistical analysis**

Expected mortality is estimated using pre-pandemic data from **2015–2019**, with a model incorporating:

* Year
* Week of the year

Excess mortality is then calculated by comparing observed mortality with the estimated baseline.

The final analysis examines mortality levels across temperature intervals to explore how mortality varies with temperature.

## Skills Demonstrated

These projects allowed me to develop practical skills in:

* Data cleaning and preprocessing
* Exploratory data analysis
* Data visualization
* Spatial data analysis
* Geographic information systems (GIS)
* Interactive visualization
* Dashboard development
* Time-series analysis
* Statistical modeling
* Baseline and excess mortality analysis
* API-based data collection
* Combining heterogeneous datasets
* Communicating analytical results through visualizations

---

## Project Structure

```text
Data-Visualization-Projects/
│
├── projet1python_Amoussou_Garango_Tognibo.ipynb
├── projet2python_Amoussou_Garango_Tognibo.ipynb
└── README.md
```

### Project I

`projet1python_Amoussou_Garango_Tognibo.ipynb`

**U.S. County Population Visualization**

### Project II

`projet2python_Amoussou_Garango_Tognibo.ipynb`

**Temperature and Mortality in Italy**

---

## Academic Context

These projects were developed as part of the **Data Visualization** course during my Master's studies in **Econometrics and Statistics – Data Science**.

They illustrate how Python can be used to transform raw data into informative visualizations and analytical outputs, from geographic population analysis to climate and mortality studies.

---

## Authors

* **Bintou Daouda GARANGO**
* **Hariane TOGNIBO**
* **Orianne AMOUSSOU**
