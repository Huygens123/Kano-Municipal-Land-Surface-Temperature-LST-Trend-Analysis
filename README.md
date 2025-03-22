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
These results suggest that regional climate factors may be the dominant influence on LST patterns in the study area, potentially overshadowing the effects of land cover differences. The similar patterns across different land covers indicate that macro-scale climate drivers affect the entire study area in a relatively uniform manner. However, all these will be verified further in the satistical analysis section
2. ### Statistical Analysis:
     # Mann-Kendall Trend Analysis of Land Surface Temperature in Kano Municipal (2013-2024)
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
![Mann-Kendall trend](https://github.com/user-attachments/assets/9ff3cbac-e260-4603-bb10-0bf41201d6e4)
#### Findings
1. **No Statistically Significant Trends**: All land cover types show p-values greater than 0.05, indicating that there are no statistically significant monotonic trends in LST for any land cover type over the study period.

2. **Slight Directional Tendencies**:
   - Small positive slopes in BUA (0.0027 units/time), Crop (0.0071 units/time), Shrub (0.0076 units/time), and Forest (0.0027 units/time) areas suggest very slight warming, though not statistically significant
   - Small negative slopes in Bare (-0.0038 units/time) and Grass (-0.0087 units/time) areas suggest very slight cooling, though not statistically significant

3. **Kendall's Tau Values**: All Kendall's tau values are close to zero, further confirming weak correlations between temperature and time.
Based on the Mann-Kendall analysis, we cannot conclude that there have been significant changes in Land Surface Temperature in Kano Municipal across any of the six land cover types during the 2013-2024 period. Further analysis using additional statistical methods may provide complementary insights.

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
*(Include sample visualizations here)*

## Future Work
- Extend the analysis to include more recent data
- Incorporate additional variables such as vegetation indices
- Compare with climate model projections
- Develop predictive models for future LST trends

## References
- *Add relevant references to literature and data sources*

## Contributors
- *Your Name* - *Your Affiliation*

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- *Add acknowledgments for data providers, funding sources, etc.*
