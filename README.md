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
1. ### Land Surface Temperature Map:
   ![LST Yearly Map](results/maps/Yearly_LST.png)
1. ### Land Surface Temperature Results (LST):
   - **Temperature Range**: All land cover types show LST values generally ranging between 20-40°C
   - **Temporal Pattern**: Similar seasonal fluctuations are evident across all land cover types
   - **Anomaly**: A significant temperature drop occurred around 2015-2016 across all land cover types
   - **Consistency**: The overall pattern of temperature variation remains consistent across different land cover categories
   - **Peaks**: Maximum temperatures approach 40°C during peak periods
   - **Seasonality**: Clear seasonal cycles are visible throughout the study period
   - **Recent Trends**: No dramatic long-term increasing or decreasing trend is immediately apparent from visual inspection
These results suggest that regional climate factors may be the dominant influence on LST patterns in the study area, potentially overshadowing the effects of land cover differences. The similar patterns across different land covers indicate that macro-scale climate drivers affect the entire study area in a relatively uniform manner. However, all these will be verified further in the satistical analysis section
2. ### Mann-Kendall Trend Analysis of Land Surface Temperature in Kano Municipal (2013-2024)
   The Mann-Kendall test was applied to LST data for six land cover types in Kano Municipal. The results indicate:
**Mann-Kendall Regional Test is used to analyze trends across different the POI**
- `Trend`: Indicates the direction and significance of the trend
- `p-value`: Determines statistical significance (p < 0.05 indicates a significant trend)
- `Kendall's tau`: Measures the strength and direction of the association
- `Sen's slope`: Estimates the magnitude of the trend

| Land Cover Type | Trend     | p-value   | Kendall's tau | Sen's slope |
|----------------|-----------|-----------|--------------|------------|
| Built-up       | No trend  | 0.806360  | -0.018987    | -0.004439  |
| Crop           | No trend  | 0.574880  | 0.043038     | 0.010216   |
| Bareland       | No trend  | 0.324794  | 0.075316     | 0.020615   |
| Shrub          | No trend  | 0.768008  | -0.022785    | -0.006097  |
| Grassland      | No trend  | 0.552434  | 0.045570     | 0.010915   |
| Forest         | No trend  | 0.422640  | 0.061392     | 0.013715   |

None of the land cover types show a statistically significant trend in Land Surface Temperature. This is evident from the high p-values (all > 0.05), which suggest that the observed variations in temperature could be due to random fluctuations rather than a consistent trend.

  **Seasonal Kendall Test**
| Land Cover Type | Trend      | p-value   | Sen's slope |
|----------------|------------|-----------|-------------|
| Built-up       | No trend   | 0.068292  | 0.112608    |
| Crop           | Increasing | 0.009204  | 0.211109    |
| Bareland       | Increasing | 0.000189  | 0.296801    |
| Shrub          | No trend   | 0.385323  | 0.080833    |
| Grassland      | No trend   | 0.082518  | 0.234221    |
| Forest         | Increasing | 0.004172  | 0.283901    |

Three land cover types (Bareland, Forest, and Crop) show statistically significant increasing Land Surface Temperature trends. Bareland exhibits the most pronounced temperature increase. Built-up and Grassland areas are on the border of statistical significance. Shrub areas show no significant temperature trend. The significant warming in Bareland, Forest, and Crop areas could mean that the local climate change effects, Land use and land cover changes and potential urban heat island or deforestation impacts.
3.  Quantile Regeression Analysis (QR)
Quantile regression was applied to examine potential trends across five different quantiles (0.1, 0.25, 0.5, 0.75, and 0.9) of the LST distribution for each land cover type. This approach helps identify whether different parts of the temperature distribution (e.g., extreme low temperatures vs. extreme high temperatures) are changing at different rates.
Quantile Regression Analysis of Land Cover Types

| Land Cover Type | Q(0.1) Slope | Q(0.25) Slope | Q(0.5) Slope | Q(0.75) Slope | Q(0.9) Slope | 
|----------------|--------------|--------------|--------------|---------------|--------------|
| Bareland       | 0.048749     | 0.043977     | 0.042057     | 0.023058      | -0.022647    |
| Forest         | 0.046793     | 0.029460     | 0.029967     | 0.022883      | -0.012253    |
| Crop           | 0.008713     | 0.029358     | 0.030498     | 0.025632      | -0.024453    |
| Shrub          | 0.011303     | 0.029743     | 0.022076     | 0.008930      | -0.026201    |
| Built up       | 0.015008     | 0.023755     | 0.022609     | 0.007201      | -0.008581    |
| Grass          | -0.028710    | 0.000478     | 0.012926     | 0.027618      | -0.018106    |


Most land cover types show positive slopes in lower to mid quantiles (Q(0.1) to Q(0.5)) and consistent negative slopes appear in the highest quantile (Q(0.9)). Bareland shows the most pronounced slope variations at Q(0.1): 0.048749 while Grassland is the only type with a negative slope at Q(0.1): -0.028710 meanwhile, Crop peaks at Q(0.5) with a slope of 0.030498

The quantile regression analysis show the changes in LST distributions across different land cover types in Kano Municipal between 2013-2024. Although, these changes are not statistically significant, the consistent patterns across land cover types—particularly the increases in lower quantile temperatures—merit continued monitoring and may have implications for urban planning, agriculture, and ecosystem management in the region.

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
- Trend
   - Highest in Shrub (63.66%) and Bareland (62.34%)
   - Lowest in Built-up areas (52.62%) and Forest (53.97%)
- Seasonal Variance
   - Consistently low across all land cover types
   - Ranges from 1.57% to 3.63%
- Residual Variance
   - Varies from 16.14% to 24.81%
   - Highest in Built-up areas (24.81%)
   - Lowest in Grass and Bareland (18.67%)

5. ### Extreme Event Analysis of Land Surface Temperature
The analysis tracks temperature anomalies and identifies both high and low extreme events based on percentile thresholds.

| Land Cover Type | Upper Threshold (95th percentile) | Lower Threshold (5th percentile) |
|----------------|-----------------------------------|----------------------------------|
| Forest | 35.76°C | 23.88°C |
| Grass | 41.43°C | 25.70°C |
| Shrub | 39.37°C | 27.21°C |
| Bareland | 40.96°C | 28.21°C |
| Crop | 40.46°C | 27.96°C |
| Built-up Areas | 38.25°C | 26.07°C |

- **Findings**
   - **Crop**: The analysis revealed an upper threshold (95th percentile) of 40.46°C and a lower threshold (5th percentile) of 27.96°C for crop. Extreme low event occured in late 2015 which was about 14.8°C and it then concentrated in early 2022, while extreme high temperature events were concentrated between 2019 and 2020.
   - **Forest**: Forest showed slightly different thresholds with an upper value of 35.76° and a lower value of 23.88°. Extreme high events were clustered in 2019 to 2020, while extreme low events reched minimum (21.5°C in 2022 and 22°C in 2023.
   - **Grass and Shrub**: The analysis revealed that grass environments with thresholds of 41.43° (upper) and 25.70° (lower), while shrub environments recorded thresholds of 39.37°C (upper) and 27.21°C (lower). Both vegetation types experienced identical high extreme events 2019, with low extremes appearing in 2023 (Shrub) and late 2015 for forest,
   - **BUA and Bareland**: The analysis revealed that both BUA and Barelan have several similar patterns in extreme temperature events with both of them have consistent numbers of extreme high temperature events from 2018 through 2020. Low temperature extremes reached significant magnitudes, dropping to approximately 22.5°C in 2022 and near 25°C in 2023.

The consistent patterns across different environments suggest regional climate shifts affecting multiple ecosystems simultaneously. The clustering of extreme events and their recent intensification warrant further investigation for climate change impact assessment, ecological research, and agricultural planning.

6. ### Spatial Pattern Analysis
This analysis examines temperature patterns, correlations between locations, and underlying data structure through principal component analysis (PCA).
**Findings**
- Forest and Crop areas show the highest average temperatures (about 31.5°C), while Grass areas recorded the lowest (approximately 29.5°C). Shrub, Bare Land, and Built-Up areas fall in the middle range (approximately 30°C).
- Forest and Crop areas display the highest temperature variability (standard deviation ~5.8), while Shrub, Bare Land, and Grass show the lowest (standard deviation ~5.1-5.2). Built-Up areas show moderate variability (standard deviation ~5.4).
- All locations show very high correlations (0.86-0.98). The strongest correlations exist between Bare Land with Shrub and Grass (both 0.98), and between Grass and Shrub (0.97). The weakest correlation is between Built-Up Area and Crop (0.86).
- The first principal component explains approximately 90% of the total variance, with cumulative explained variance reaching ~99% with just two components.
  
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
![Temperature_Distibution_by_LandUse](https://github.com/user-attachments/assets/27552604-e149-454d-bac5-5b23b37b3bf1)

2. **Mann-Kendal Analysis**
![LST_Trend_Analysis](https://github.com/user-attachments/assets/3eebefb5-60ed-4a98-a0f6-d2b536d4f380)

3. **Quantile Regression Analysis**
![quantile Regression for Crop](https://github.com/user-attachments/assets/628b3530-70fa-4caf-b366-35647839bb5b)
![quantile Regression for Built up](https://github.com/user-attachments/assets/d445d99a-319a-483c-a052-e51653aef347)
![quantile Regression for Bareland](https://github.com/user-attachments/assets/1a54d610-d65f-4a2c-9d8e-b4816f4ab252)
![quantile Regression for Shrub](https://github.com/user-attachments/assets/e260b9b6-9980-43c9-8dd2-9d593577daff)
![quantile Regression for Grass](https://github.com/user-attachments/assets/8dfa3b74-089d-4134-bf44-91b6a7732ba6)
![quantile Regression for Forest](https://github.com/user-attachments/assets/ad003ea3-280c-49b0-8fa7-58038229d673)

  
5. **Seasonal Decomposition Analysis**:
![seasonal decomposition for Crop](https://github.com/user-attachments/assets/c73f1391-a862-43a3-a0f8-ba2671fe6740)
![seasonal decomposition for Built up](https://github.com/user-attachments/assets/9bf1690b-61c7-4dc6-91a3-c9a7053edd53)
![seasonal decomposition for Bareland](https://github.com/user-attachments/assets/919cbc4d-1971-4197-ae8f-07747b6ab78b)
![seasonal decomposition for Grass](https://github.com/user-attachments/assets/29fbe6d4-a6d8-47e3-aa3d-e46c02b48901)
![seasonal decomposition for Shrub](https://github.com/user-attachments/assets/3c0c5217-c160-4d94-8a0a-e233f47533fd)
![seasonal decomposition for Forest](https://github.com/user-attachments/assets/cd49eb09-cddc-45c9-8b01-289366b2ebd7)

6. **Extreme Values Analysis**:

![extreme values timeseries Forest](https://github.com/user-attachments/assets/3ca92753-a202-467e-b1d0-5f037350ac71)
![extreme values timeseries Crop](https://github.com/user-attachments/assets/d178138b-4958-41ed-b0c4-074acf9c76d2)
![extreme values timeseries Built up](https://github.com/user-attachments/assets/a12249c6-cb2b-458d-b35c-a1f8ffcdae87)
![extreme values timeseries Bareland](https://github.com/user-attachments/assets/b8d22261-b4fa-4e4a-86a1-ab5053bf9221)
![extreme values timeseries Shrub](https://github.com/user-attachments/assets/7fea497c-84da-4a64-9e39-bae0ac5f63f9)
![extreme values timeseries Grass](https://github.com/user-attachments/assets/305a1dc5-0d48-4099-b4e6-b3e1eb3165dd)

6. **Spatial Patterns**

![Average temperature by location](https://github.com/user-attachments/assets/31cb78ba-82fd-47da-8747-c3a61ec0a1f0)
![Temperature variability](https://github.com/user-attachments/assets/1011d0a0-fa5e-4072-9224-5ac51eda933a)
![First Two Principal Components](https://github.com/user-attachments/assets/2bb67243-16a7-4172-827b-07207a9f19ac)
![Explained PCA](https://github.com/user-attachments/assets/ca0abb67-a1d5-40ac-8c4b-73dd7257e06a)
![Correlation](https://github.com/user-attachments/assets/ccb82f7d-9c58-4c63-90fc-3c3fc3261dca)

## References
- de Beurs, K.M., & Henebry, G.M. (2004). Trend analysis of the Pathfinder AVHRR Land (PAL) NDVI data for the deserts of Central Asia. IEEE Geoscience and Remote Sensing Letters, 1(4), 282-286.
- Parey, S., Malek, F., Laurent, C., & Dacunha-Castelle, D. (2007). Trends and climate evolution: Statistical approach for very high temperatures in France. Climatic Change, 81(3-4), 331-352.
- Metz, M., Rocchini, D., & Neteler, M. (2014). Surface temperatures at the continental scale: Tracking changes with remote sensing at unprecedented detail. Remote Sensing, 6(5), 3822-3840.
- Li, H., Zhou, Y., Jia, G., Zhao, K., & Dong, J. (2022). Quantifying the response of surface urban heat island to urbanization using the annual temperature cycle. Geophysical Research Letters, 49(7), e2021GL097673

## Author
- *Abdulquawiyy Adisa Owolabi*
