# Temperature and Mortality in Italy — Python

## Project Overview

The objective is to study the relationship between **climatic conditions and mortality in Italy** over the period **2015–2024**.

The project combines temperature data from the **ERA5 reanalysis dataset** with weekly mortality data from the **World Mortality Dataset**.

The analysis progressively covers:

1. Climate data extraction and preparation.
2. Temperature visualization.
3. Mortality time-series analysis.
4. Estimation of expected mortality.
5. Excess mortality analysis.
6. Exploration of the temperature–mortality relationship.

## Objectives

The main objectives are to:

* Extract temperature data for Italy from ERA5.
* Transform hourly temperature observations into daily and weekly indicators.
* Visualize temperature patterns over time.
* Analyze weekly mortality in Italy.
* Estimate an expected mortality baseline using pre-pandemic data.
* Calculate excess mortality during summer 2022.
* Explore the relationship between temperature and mortality.

## Data Sources

### ERA5 Climate Data

Temperature data comes from the **ERA5 reanalysis dataset**.

The analysis uses **2-meter air temperature** for Italy.

The geographical area used for extraction covers:

* Latitude: 37 to 46
* Longitude: 9 to 18.5

The study covers the period **2015–2024**, with a specific focus on **summer 2022**.

### World Mortality Dataset

Weekly mortality data comes from the **World Mortality Dataset**.

The analysis filters the dataset using the ISO3 country code:

```text
ITA
```

corresponding to Italy.

## Data Preparation

### Temperature Data

The ERA5 temperature data is processed through several steps:

1. Downloading hourly temperature data.
2. Converting temperature from Kelvin to Celsius.
3. Computing daily averages.
4. Applying latitude-based spatial weighting using the cosine of latitude.
5. Computing the spatial mean for Italy.
6. Aggregating observations into weekly averages.
7. Exporting the processed data as CSV files.

## Temperature Visualization

Several visualizations were produced to explore temperature patterns.

### Summer 2022

Daily temperatures from **June 1 to August 31, 2022** are visualized to examine the evolution of temperature during the summer.

### Weekly Temperature Series

A weekly time series covering **2015–2024** was constructed.

The weekly aggregation reduces daily variability and makes longer-term seasonal patterns easier to identify.

The summer of 2022 is highlighted to facilitate comparison with the rest of the period.

## Mortality Analysis

The World Mortality Dataset was filtered to retain observations for Italy.

The data was cleaned by:

* Removing unnecessary geographic columns.
* Renaming variables for consistency.
* Reconstructing weekly start dates using the ISO calendar.

A weekly mortality time series was then created to visualize mortality evolution over the available period.

## Expected Mortality Baseline

A baseline model was estimated using mortality data from the **pre-pandemic period**.

The model uses observations from **2015–2019** and takes the following form:

```text
mortality ~ year + C(week)
```

The model therefore includes:

* A linear year effect to represent the long-term trend.
* Week fixed effects to account for weekly seasonality.

The model is then used to estimate expected mortality during **summer 2022**.

## Excess Mortality

Excess mortality is calculated as:

```text
Excess mortality = Observed mortality − Predicted mortality
```

Observed and predicted mortality are first compared visually.

The analysis shows that observed mortality rises above the estimated baseline during summer 2022, with the largest differences occurring during July.

The project reports an excess mortality peak of **more than 4,000 additional deaths around mid-July 2022**.

## Temperature–Mortality Relationship

The final analysis combines temperature and mortality data.

Mortality observations are transformed into a daily series through interpolation and merged with daily temperature observations.

Temperature values are then divided into **15 bins**, and mean mortality is calculated for each temperature interval.

A scatter plot is used to visualize the relationship between:

* Mean temperature
* Mean mortality

This provides a graphical exploration of how mortality varies across different temperature ranges.

## Technologies and Libraries

The project was developed in **Python** using:

* Python
* NumPy
* Pandas
* Xarray
* Matplotlib
* Seaborn
* Cartopy
* CDS API
* Statsmodels

## Key Skills Demonstrated

* Climate data acquisition
* API-based data retrieval
* NetCDF data processing
* Time-series analysis
* Spatial aggregation
* Data cleaning and transformation
* Statistical modeling
* Baseline estimation
* Excess mortality calculation
* Exploratory data visualization
* Relationship analysis using scatter plots

## Project Structure

```text
project/
│
├── project2.ipynb
├── README.md
└── data/
```

## Academic Context

**Course:** Data Visualization
**Software:** Python
**Project:** Project II — Temperature and Mortality in Italy

## Authors

* Bintou Daouda GARANGO
* Hariane TOGNIBO
* N’gagnin Jean Luc OTODJI

# US County Population Visualization — Python

## Project Overview

This project was developed as part of the **Data Visualization** course. It analyzes the distribution of the U.S. population at the county level using **2010 NHGIS census data**.

The analysis focuses on the 48 contiguous U.S. states and examines both total population and population composition by racial group.

The project combines **static visualizations, geospatial analysis, interactive maps and an interactive dashboard** using Python.

## Objectives

The main objectives are to:

* Collect population and geographic data from NHGIS.
* Prepare and clean county-level spatial data.
* Analyze population composition by racial group.
* Visualize county population differences across the United States.
* Create static and interactive geographical visualizations.
* Develop an interactive dashboard for exploring individual counties.

## Data Sources

The project uses data from the **National Historical Geographic Information System (NHGIS)**.

### Geographic data

A 2020 county shapefile was obtained through the NHGIS API. The analysis was restricted to the **48 contiguous states**, excluding Alaska, Hawaii and U.S. territories.

After filtering, the dataset contains **3,108 counties**.

### Population data

Population data comes from the **2010 NHGIS CW8 table**.

The population was grouped into five categories:

* White
* Black or African American
* American Indian and Alaska Native
* Asian and Pacific Islander
* Other

Male and female population counts were combined to obtain total population by racial group.

The two datasets were joined using the **GISJOIN** identifier.

## Data Preparation

Several preprocessing steps were performed:

1. Downloading geographic and population data through the NHGIS API.
2. Extracting and loading the county shapefile.
3. Filtering the dataset to the 48 contiguous states.
4. Checking the validity of spatial geometries.
5. Correcting invalid geometries using `buffer(0)`.
6. Aggregating population counts by racial group.
7. Joining population and geographic data using `GISJOIN`.
8. Computing total county population.

The final geographic dataset contains **3,108 observations**.

## Visualizations

### 1. Los Angeles County

The first task focuses on **Los Angeles County**.

Two horizontal bar charts were created:

* Absolute population by racial group.
* Relative population shares by racial group.

The analysis also includes a validation step using the 2010 population of Los Angeles County.

### 2. Choropleth Map

A static choropleth map was created to represent **total county population** across the contiguous United States.

Population values were classified into **seven quantiles**, allowing differences between highly populated and less populated counties to be visualized despite the strong asymmetry of the population distribution.

### 3. Interactive Folium Map

The static map was extended into an interactive map using **Folium**, based on Leaflet.

Users can:

* Hover over counties to view their name and total population.
* Click on counties to obtain additional information.
* Zoom and navigate across the United States.

### 4. Interactive Panel Dashboard

The final task combines the interactive map and population charts into a **Panel dashboard**.

The dashboard includes two interconnected selections:

* State
* County

When a state is selected, the list of available counties is updated automatically. Selecting a county then updates the corresponding population composition charts.

The dashboard also displays the selected county's identifier.

## Technologies and Libraries

The project was developed in **Python** using:

* Python
* Pandas
* NumPy
* GeoPandas
* Matplotlib
* Folium
* Branca
* Mapclassify
* IPUMSpy
* Panel

## Key Skills Demonstrated

* Data acquisition through an API
* Data cleaning and preprocessing
* Geospatial data manipulation
* Spatial joins
* Exploratory data visualization
* Choropleth mapping
* Interactive mapping
* Dashboard development
* Geographic data analysis
* Interactive data exploration

## Project Structure

```text
project/
│
├── project1.ipynb
├── README.md
└── data/
```

## Academic Context

**Course:** Data Visualization
**Software:** Python
**Project:** Project I — NHGIS and U.S. County Population

## Authors

* Bintou Daouda GARANGO
* Hariane TOGNIBO
* N’gagnin Jean Luc OTODJI

