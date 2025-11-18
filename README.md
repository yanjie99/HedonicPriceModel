# Modelling Spatial Heterogeneity in Singapore's HDB Resale Market: A comparative Analysis of OLS and Euclidean Distance-Based GWR

This repository contains the full analytical workflow, data-processing scripts, and modelling code for this project.
This project investigates spatial variations in housing price determinants across Singapore's public housing (HDB) market using a combination of **global** and **local** spatial regression techniques.

📌## **Project Overview**
Housing prices in Singapore exhibit pronounced spatial variation driven by accessibility, amenities, built-environment characteristics, and neighbourhood differences. Traditional global regression models (e.g., OLS) assume spatial stationarity, which often fails in a highly differentiated urban landscape like Singapore.

This project develops a comparative framework:
- **Global OLS hedonic modelling**
- **Local Euclidean Distance-based Geographically Weighted Regression (ED-based GWR)**(adaptive kernel, nearest-neighbour bandwidths)

## 📂 **Repository Structure**
```
  │code/
  ├── 00DataPreprocessing.ipynb
  ├── 01DataPreparation.ipynb
  ├── 02Prepare Analysis-ready HDB features.ipynb
  ├── 03Exploratory Spatial Analysis OLS.ipynb
  ├── 03Exploratory Spatial Analysis OLS & Moran's I.ipynb
  ├── 04Local Modeling (GWR).ipynb
  ├── SpatialJoin_datapreprocess_OLS_GWR.ipynb
  │
  ├data/                   # raw & cleaned datasets
  ├── figures/             # generated maps, diagnostics, visuals
  ├── results/             # OLS & GWR outputs, CSVs, summaries
  │
  └── README.md
```

## 📊 **Key Research Questions**
1. How do structual, locational, and accessibility attributes influence HDB resale prices?
2. Do these relationships vary across space, and to what extent?
3. Can ED-based GWR improve explanatory power and reduce spatial autocorrelation compared to OLS model?
4. How do local coefficients and local R^2 reveal subzone-level housing market heterogeneity?

## 🧰 **Methodology Summary**
1. **Data Processing & Integration**
Datasets include:
- HDB resale transactions (2023)
- Subzone boundaries (Master Plan 2019, Singapore)
- Accessibility metrics (Raw data processed):
- - Distance to nearest MRT station
  - Distance to nearest healthcare facility (hospital, older house)
  - Distance to nearest recreaional facility (sports centre, recreation spot)
  - Bus stop counts within 400m each HDB flat
- Housing attributes (HDB type, floor area, building age, storey)

Processing tasks:
- Spatial join (subzone boundaries, each HDB transaction)
- Euclidean distance calculations
- Variable engineering (log resale price)
- Construction of analysis-ready dataset

Relevant notebooks:
`00DataPreprocessing.ipynb`, `01DataPreparation.ipynb`, `02Prepare Analysis-ready HDB features.ipynb`.

2. **Global Spatial Analysis (OLS + Moran's I)**
Performed tasks:
- Global OLS model
- Diagnostics:
- - R^2, adjusted R^2, AICc
  - VIF multicollinearity checks
  - Residual analysis
 
- Global Moran's I on OLS residuals (Detects spatial autocorrelation indicating OLS deficiency)

Notebook:
`03Exploratory Spatial Analysis OLS.ipynb`, `03Exploratory Spatial Analysis OLS & Moran's I.ipynb`

3. **Local Spatial Modelling (ED-Based GWR Model)**
Key features:
- Adaptive bisquare kernel
- Optimal bandwidth selection using AICc
- Subzone-level coefficient estimates
- Maps of local R^2, t-statistics, and parameter surfaces

Notebook:
`04Local Modeling (GWR).ipynb`

📈 **Main Findings (Summary)**
- ED-GWR dramatically improves model fit (R^2 increases from 0.762 to 0.978).
- Spatial autocorrelation in OLS residuals is largely eliminated under GWR.
- Housing price drivers vary substantially across Singapore, particularly in central vs. outer subzones.
- Local R^2 reveals strong heterogeneity, identifying areas where accessibility or structual attributes dominate price formation.

🗂 **Reproducibility Guide**
**Requirements**
Recommended environment:
- Python 3.10+
- GeoPandas
- libpysal, esda
- mgwr
- shapely, pyproj
- contextily
- pandas, numpy, matplotlib

Install dependencies:
$$pip install -r requirements.txt$$



