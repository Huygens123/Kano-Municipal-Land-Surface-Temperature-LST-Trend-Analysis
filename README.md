# Kano Municipal Land Surface Temperature (LST) Trend Analysis (2013-2024)

## Overview
This repository contains a comprehensive analysis of Land Surface Temperature (LST) trends in Kano Municipal, Nigeria from 2013 to 2024 using Landsat 8 imagery. The analysis examines LST variations across different land use categories and employs multiple statistical methods to identify significant trends and patterns.

## Project Objectives
- Analyze the LST trends in Kano Municipal over an 11-year period (2013-2024)
- Identify land use specific temperature patterns and their changes over time
- Determine the statistical significance of observed trends
- Examine spatial distribution of temperature changes in the study area
- Assess extreme temperature events and their frequency

## Data
- **Boundary Data**: Boundary data from [FAO](https://developers.google.com/earth-engine/datasets/catalog/FAO_GAUL_SIMPLIFIED_500m_2015_level2)
- **Primary Data**: [Landsat 8 satellite imagery (2013-2024)](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_TOA) 
- **Land Use Classification**: Built-Up Area (BUA), Bare land, Cropland, Tree cover, Shrubland, and Grassland from [ESA WorldCover 10m v100](https://developers.google.com/earth-engine/datasets/catalog/ESA_WorldCover_v100)
- **Points of Interest (POI)**: LST values extracted for various land use categories

## Methodology
The study employed multiple analytical approaches to ensure robust results:
1. **Data Collection**: Landsat 8 imagery was retrievd for the years 2013 to 2024 using google earth engine (GEE).
2. **Land Surface Temperature Calculation**: THe rtrieved Landsat image collection was processed and used to calculate LST from 2013 to 2024. The resulting images were in form of image collection
3. **Land Use POI**:
   - Identification of different land use categories using the ESA 10m Land Cover classification
   - Selection of Points of Interest (POI) for each land use type (in QGIS)
   - Extraction of LST values at these points
4. **Statistical Analysis**:
   - **Mann-Kendall Test**: Non-parametric test used to assess the significance of trends in LST over time.
   - **Quantile Regression Analysis (QR)**: Analysis of trends across different temperature percentiles.
   - **Seasonal Decomposition Analysis**: Separation of time series into seasonal, trend, and residual components.
   - **Extreme Value Analysis**: Assessed the extreme values of LST and their return periods.
   - **Spatial Pattern Analysis**: Investigated the spatial distribution of LST across different land use categories.
     
## Results
The results of the study is as follows:
1. ### Land Surface Temperature Results (LST):
   - **Temperature Range**: All land cover types show LST values generally ranging between 15-40°C
   - **Temporal Pattern**: Similar seasonal fluctuations are evident across all land cover types
   - **Anomaly**: A significant temperature drop occurred around 2015-2016 across all land cover types
   - **Consistency**: The overall pattern of temperature variation remains consistent across different land cover categories
   - **Peaks**: Maximum temperatures approach 40°C during peak periods
   - **Seasonality**: Clear seasonal cycles are visible throughout the study period
   - **Recent Trends**: No dramatic long-term increasing or decreasing trend is immediately apparent from visual inspection
The trend is shown below:

These results suggest that regional climate factors may be the dominant influence on LST patterns in the study area, potentially overshadowing the effects of land cover differences. The similar patterns across different land covers indicate that macro-scale climate drivers affect the entire study area in a relatively uniform manner. However, all these will be verified further in the satistical analysis section
2. ### Mann-Kendall Trend Analysis of Land Surface Temperature in Kano Municipal (2013-2024)
   The Mann-Kendall test was applied to LST data for six land cover types in Kano Municipal. The results indicate:
   
**Mann-Kendall Regional Test is used to analyze trends across different the POI**
| Land Cover Type | Trend | p-value | Kendall's tau | Sen's slope |
|----------------|-------|---------|---------------|-------------|
| BUA (Built-Up Area) | no trend | 0.587291 | 0.031175 | 0.002730 |
| Crop Area | no trend | 0.406233 | 0.047649 | 0.007090 |
| Bare Area | no trend | 0.550236 | -0.034303 | -0.003772 |
| Shrub Area | no trend | 0.266555 | 0.063706 | 0.007570 |
| Grass Area | no trend | 0.319998 | -0.057033 | -0.008678 |
| Forest Area | no trend | 0.696706 | 0.022417 | 0.002724 |

  **Seasonal Kendall Test**
| Land Cover Type | Trend | p-value | Sen's slope |
|----------------|-------|---------|-------------|
| BUA (Built-Up Area) | no trend | 0.212256 | 0.109019 |
| Crop Area | no trend | 0.429521 | 0.086180 |
| Bare Area | no trend | 0.298678 | -0.080193 |
| Shrub Area | no trend | 0.157410 | 0.098044 |
| Grass Area | no trend | 0.279667 | -0.105406 |
| Forest Area | no trend | 0.382570 | 0.093140 |

The time series plots with Mann-Kendall trend is shown below:

#### Findings
- **No Statistically Significant Trends**: All land cover types show p-values greater than 0.05, indicating that there are no statistically significant monotonic trends in LST for any land cover type over the study period.
- **Slight Directional Tendencies**:
   - Small positive slopes in BUA (0.0027 units/time), Crop (0.0071 units/time), Shrub (0.0076 units/time), and Forest (0.0027 units/time) areas suggest very slight warming, though not statistically significant
   - Small negative slopes in Bare (-0.0038 units/time) and Grass (-0.0087 units/time) areas suggest very slight cooling, though not statistically significant
- **Kendall's Tau Values**: All Kendall's tau values are close to zero, further confirming weak correlations between temperature and time.
Based on the Mann-Kendall analysis, we cannot conclude that there have been significant changes in Land Surface Temperature in Kano Municipal across any of the six land cover types during the 2013-2024 period. Further analysis using additional statistical methods may provide complementary insights.
3. ### Quantile Regeression Analysis (QR)
# Quantile Regression Analysis of Land Surface Temperature in Kano Municipal (2013-2024)
Quantile regression was applied to examine potential trends across five different quantiles (0.1, 0.25, 0.5, 0.75, and 0.9) of the LST distribution for each land cover type. This approach helps identify whether different parts of the temperature distribution (e.g., extreme low temperatures vs. extreme high temperatures) are changing at different rates.

#### Built-Up Area (BUA)
| Quantile | Slope |
|----------|-------|
| 0.1 | -0.036685 |
| 0.25 | 0.005649 |
| 0.5 | 0.001117 |
| 0.75 | 0.022049 |
| 0.9 | 0.053643 |

**Findings**: 
- Lower temperatures (Q0.1) show a decreasing trend (-0.037 units/time)
- Higher temperatures (Q0.9) show an increasing trend (0.054 units/time)
- Middle temperatures (Q0.5) remain relatively stable (0.001 units/time)
- F-statistic and p-value indicate no significant difference in slopes across quantiles

#### Crop Area
| Quantile | Slope |
|----------|-------|
| 0.1 | 0.109705 |
| 0.25 | 0.003067 |
| 0.5 | 0.006783 |
| 0.75 | -0.014914 |
| 0.9 | 0.041339 |

**Findings**: 
- Lower temperatures (Q0.1) show a strong increasing trend (0.110 units/time)
- Upper-middle temperatures (Q0.75) show a slight decreasing trend (-0.015 units/time)
- No significant difference in slopes across quantiles

#### Bare Area
| Quantile | Slope |
|----------|-------|
| 0.1 | 0.106268 |
| 0.25 | -0.001544 |
| 0.5 | -0.007960 |
| 0.75 | -0.014389 |
| 0.9 | -0.013223 |

**Findings**: 
- Lower temperatures (Q0.1) show a substantial increasing trend (0.106 units/time)
- Middle and higher temperatures show slight decreasing trends
- Suggests narrowing of temperature distribution over time

#### Shrub Area
| Quantile | Slope |
|----------|-------|
| 0.1 | 0.108318 |
| 0.25 | 0.008513 |
| 0.5 | 0.007601 |
| 0.75 | 0.016550 |
| 0.9 | 0.013116 |

**Findings**: 
- All quantiles show positive slopes, indicating warming across the entire distribution
- Lower temperatures (Q0.1) are increasing most rapidly (0.108 units/time)
- No significant difference in slopes across quantiles

#### Grass Area
| Quantile | Slope |
|----------|-------|
| 0.1 | 0.059229 |
| 0.25 | -0.006993 |
| 0.5 | -0.026785 |
| 0.75 | -0.011483 |
| 0.9 | 0.036976 |

**Findings**: 
- U-shaped pattern with increasing trends in lower (Q0.1) and higher (Q0.9) temperatures
- Middle temperatures (Q0.5) show the strongest decreasing trend (-0.027 units/time)
- Suggests increasing temperature variability over time

#### Forest Area
| Quantile | Slope |
|----------|-------|
| 0.1 | 0.036815 |
| 0.25 | 0.000877 |
| 0.5 | -0.006637 |
| 0.75 | -0.015854 |
| 0.9 | 0.027920 |

**Findings**: 
- Similar U-shaped pattern to grass area
- Lower (Q0.1) and higher (Q0.9) temperatures show increasing trends
- Upper-middle temperatures (Q0.75) show the strongest decreasing trend (-0.016 units/time)
The quantile regression analysis show the changes in LST distributions across different land cover types in Kano Municipal between 2013-2024. Althoug, these changes are not statistically significant, the consistent patterns across land cover types—particularly the increases in lower quantile temperatures—merit continued monitoring and may have implications for urban planning, agriculture, and ecosystem management in the region.

4. ### Seasonal Decomposition Analysis
The analysis decomposes observed time series data into trend, seasonal, and residual components to understand the temporal patterns in vegetation cover.

**Variance Explained by Components**

| Cover Type | Trend (%) | Seasonality (%) | Residuals (%) |
|------------|-----------|----------------|--------------|
| BUA        | 49.21     | 8.77           | 38.17        |
| Forest     | 37.48     | 8.67           | 46.33        |
| Grass      | 44.55     | 8.91           | 37.87        |
| Shrub      | 44.82     | 8.85           | 37.96        |
| Bare       | 44.63     | 8.98           | 36.24        |
| Crop       | 47.24     | 8.85           | 39.17        |

**Findings**
- Trend:
   - All vegetation types show similar long-term trend patterns with peaks around 2018 and 2024
   - Forest has the lowest trend component (37.48%)
   - Run has the highest trend component (49.21%)
- Seasonal:
   - All vegetation types display consistent seasonal patterns
   - Seasonality explains approximately 8-9% of variance across all types
   - Regular oscillation indicates predictable annual growth cycles
- Residual Component:
   - Forest has the highest residual component (46.33%)
   - Bare has the lowest residual component (36.24%)
   - A significant drop in residuals visible around 2016 across all types
The decomposition analysis shows that the seasonal patterns are consistent across vegetation types and the relative importance of trend and random fluctuations varies. Forest areas show higher unexplained variance, suggesting more complex dynamics, while Run areas demonstrate stronger trend dominance.

5. ### Extreme Event Analysis of Land Surface Temperature in Kano Municipal (2013-2024)
The analysis tracks temperature anomalies and identifies both high and low extreme events based on percentile thresholds.

- **Findings**
   - **Crop**: The analysis revealed an upper threshold (95th percentile) of 40.69° and a lower threshold (5th percentile) of 19.65° for crop. Extreme low events were concentrated in 2014-2015, while multiple extreme high temperature events were observed in 2019, 2020, and 2024.
   - **Forest**: Forest showed slightly different thresholds with an upper value of 39.95° and a lower value of 23.09°. Extreme high events were observed in 2015, 2018-2021, and 2024, while extreme low events clustered around 2018-2019.
   - **Vegetation**: Additional analysis by vegetation type showed grass environments with thresholds of 38.33° (upper) and 19.42° (lower), while shrub environments recorded thresholds of 38.66° (upper) and 19.37° (lower). Both vegetation types experienced identical numbers of extreme events, with low extremes concentrated in 2014-2015 and high extremes appearing in 2019-2020 and 2024.
   - **BUA and Bareland**: The analysis revealed that BUA and Barelan have several significant patterns in extreme temperature events with both of them have consistent numbers of extreme low temperature events from 2014 through 2024, with an increase between 2013 and 2014 that persisted thereafter. Low temperature extremes reached significant magnitudes, dropping to approximately 14°C in 2014 and near 2°C in 2016.

The consistent patterns across different environments suggest regional climate shifts affecting multiple ecosystems simultaneously. The clustering of extreme events and their recent intensification warrant further investigation for climate change impact assessment, ecological research, and agricultural planning.

The consistent pattern of extreme low events since 2014 and the clustering of extreme high events may indicate broader regional climate shifts. The data suggests potential changes in climate variability that warrant further investigation, particularly given the recent extreme high temperature events observed in 2024.

6. ### Spatial Pattern Analysis
This analysis examines temperature patterns, correlations between locations, and underlying data structure through principal component analysis (PCA).

**Findings**
- Forest and Crop areas show the highest average temperatures (approximately 31.5°C), while Grass areas recorded the lowest (approximately 29.5°C). Shrub, Bare Land, and Built-Up areas fall in the middle range (approximately 30°C).
- Forest and Crop areas display the highest temperature variability (standard deviation ~5.8), while Shrub, Bare Land, and Grass show the lowest (standard deviation ~5.1-5.2). Built-Up areas show moderate variability (standard deviation ~5.4).
- All locations show very high correlations (0.86-0.98). The strongest correlations exist between Bare Land with Shrub and Grass (both 0.98), and between Grass and Shrub (0.97). The weakest correlation is between Built-Up Area and Crop (0.86).
- The first principal component explains approximately 95% of variance, with cumulative explained variance reaching ~99% with just two components.

## Repository Structure
```
├── data/
│   └── poi/            # Extracted point data for different land uses
├── results/
│   ├── figures/        # Generated plots and maps
│   ├── tables/         # Statistical results tables
│   └── maps/           # Spatial distribution maps
├── docs/               # Project documentation
└── notebooks/          # Jupyter notebooks with analysis workflow
```

## Tools and Technologies
- **Remote Sensing**: QGIS, Google Earth Engine
- **Data Analysis**: Python (pandas, numpy, scipy)
- **Statistical Analysis**: Python (trend, extreme value packages)
- **Visualization**: Matplotlib, Seaborn, geemap

## Results Visualization
1. **Land Surface Temperature Trend (LST)**
![Land Surface Temperature (LST) Trend](https://github.com/user-attachments/assets/034bc1fa-aa9b-4ef9-b97f-b2a8b074eac7)

2. **Mann-Kendal Analysis**
![Mann-Kendall trend](https://github.com/user-attachments/assets/c54b852c-aa6f-4539-b7a7-3372a9b7a2f2)

3. **Quantile Regression Analysis**
![quantile Regression for Bare](https://github.com/user-attachments/assets/281afa52-36ea-4dc7-8e6a-c51d03744bb5)
![quantile Regression for Shrub](https://github.com/user-attachments/assets/380c6e05-27d2-468e-b014-1b7a58ad2ba2)
![quantile Regression for Grass](https://github.com/user-attachments/assets/3f793e62-8889-4c05-8f54-fa31e1b2a83e)
![quantile Regression for Forest](https://github.com/user-attachments/assets/6f9b7d30-2c10-4ace-867f-a99c0bb9d8c9)
![quantile Regression for Crop](https://github.com/user-attachments/assets/e672ff02-54f3-4540-bd4b-a9c1c22d57be)
![quantile Regression for Bua](https://github.com/user-attachments/assets/32d5871c-b981-4a8f-8c78-467a704c80b0)
  
4. **Seasonal Decomposition Analysis**:
![seasonal decomposition for Shrub](https://github.com/user-attachments/assets/279f8911-09d1-437c-922d-bf08dc85f808)
![seasonal decomposition for Grass](https://github.com/user-attachments/assets/442d6dfe-eff7-4302-a089-8648b9e9bc1f)
![seasonal decomposition for Forest](https://github.com/user-attachments/assets/40f1ec16-cc7a-47e8-8bc5-6619a1d9be5f)
![seasonal decomposition for Crop](https://github.com/user-attachments/assets/cfce0efd-31ae-4f5a-967d-072345ed77d5)
![seasonal decomposition for Bua](https://github.com/user-attachments/assets/d44364df-4df4-49cf-b469-dae8e5677fb6)
![seasonal decomposition for Bare](https://github.com/user-attachments/assets/24d2a340-38ac-48b2-b099-c68fe5b63708)

5. **Extreme Values Analysis*:
![extreme values timeseries Grass](https://github.com/user-attachments/assets/b5573448-12f3-48a5-a665-bd303b03d14f)
![extreme values timeseries Forest](https://github.com/user-attachments/assets/2d291e47-a40b-48aa-9627-23c7e0810bca)
![extreme values timeseries Crop](https://github.com/user-attachments/assets/6d1ed630-1429-4893-b09a-0b0ff90b6825)
![extreme values timeseries Bua](https://github.com/user-attachments/assets/fa8c745e-9610-4f7b-8de7-9a9911250614)
![extreme values timeseries Bare](https://github.com/user-attachments/assets/f3cb7059-5fe2-47f0-88a7-3979dbb7408d)
![extreme values timeseries Shrub](https://github.com/user-attachments/assets/6a2d75b9-5226-4372-8e23-6b743b71ed3f)

## References
- de Beurs, K.M., & Henebry, G.M. (2004). Trend analysis of the Pathfinder AVHRR Land (PAL) NDVI data for the deserts of Central Asia. IEEE Geoscience and Remote Sensing Letters, 1(4), 282-286.
- Parey, S., Malek, F., Laurent, C., & Dacunha-Castelle, D. (2007). Trends and climate evolution: Statistical approach for very high temperatures in France. Climatic Change, 81(3-4), 331-352.
- Metz, M., Rocchini, D., & Neteler, M. (2014). Surface temperatures at the continental scale: Tracking changes with remote sensing at unprecedented detail. Remote Sensing, 6(5), 3822-3840.
- Li, H., Zhou, Y., Jia, G., Zhao, K., & Dong, J. (2022). Quantifying the response of surface urban heat island to urbanization using the annual temperature cycle. Geophysical Research Letters, 49(7), e2021GL097673

## Contributors
- *Abdulquawiyy Adisa Owolabi*
