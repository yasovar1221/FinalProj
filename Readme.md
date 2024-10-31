
# Wildfire Smoke Impact Estimator

This project is designed to create an annual estimate of wildfire smoke impact for a specified city. The estimate will be used to develop a predictive model to forecast smoke impacts in future years. 

## Project Overview

The goal of this project is to estimate the wildfire smoke impact in your assigned city based on historical fire data. The estimate is based on wildfires occurring within a 650-mile radius of your city from 1961 to 2021, and only during the annual fire season from May 1st to October 31st. The project includes reading and processing geospatial wildfire data, estimating smoke impact, and validating the estimate against available Air Quality Index (AQI) data from the US EPA. Finally, a predictive model will forecast smoke impacts for the years 2025-2050.

---

## Main Functions

### 1. `read_wildfire_data(file_path)`
- **Purpose**: Reads wildfire data from a specified file path in GeoJSON or ArcGIS format.
- **Input**: File path to the wildfire data file.
- **Output**: A data structure (e.g., a DataFrame or dictionary) containing the relevant wildfire information.
- **Notes**: You can use Python libraries like `geopandas` or `pandas` to handle the data, depending on your preference.

### 2. `filter_fires_by_distance(city_coordinates, max_distance, wildfire_data)`
- **Purpose**: Filters the wildfire data to include only fires within a specified distance (650 miles) from the given city coordinates.
- **Input**: City coordinates (latitude and longitude), maximum distance in miles, and the wildfire data.
- **Output**: A filtered dataset containing only relevant wildfires.
- **Notes**: The function uses geodetic distance calculations to ensure accuracy.

### 3. `define_fire_season(wildfire_data)`
- **Purpose**: Filters the wildfire data to include only fires that occurred during the annual fire season (May 1st to October 31st).
- **Input**: The wildfire data.
- **Output**: A dataset containing only fires within the specified fire season.

### 4. `calculate_smoke_impact(city_coordinates, wildfire_data)`
- **Purpose**: Estimates the smoke impact for the city based on the size, duration, and distance of each wildfire.
- **Input**: City coordinates and the filtered wildfire data.
- **Output**: A smoke impact estimate for each year in the dataset.
- **Notes**: The smoke impact formula should consider fire size and distance from the city. The estimate can be cumulative or amortized over the fire season, depending on your chosen methodology.

### 5. `compare_with_aqi_data(city, start_year, end_year)`
- **Purpose**: Compares the smoke impact estimate with available AQI data from the US EPA.
- **Input**: City name, start year, and end year for the comparison.
- **Output**: A comparison analysis between the smoke impact estimate and AQI data.
- **Notes**: Requires access to the US EPA Air Quality System (AQS) API. You will need to request and use an API key.

### 6. `request_aqi_data(api_key, city_county, start_date, end_date)`
- **Purpose**: Requests AQI data from the US EPA AQS API for a specified date range and location.
- **Input**: API key, city or county name, start date, and end date.
- **Output**: AQI data for the specified parameters.
- **Notes**: Make sure to handle API requests and responses efficiently.

### 7. `develop_predictive_model(smoke_estimate_data)`
- **Purpose**: Develops a predictive model to forecast smoke impact estimates for the years 2025-2050.
- **Input**: Smoke impact data from past years.
- **Output**: A predictive model and forecast data.
- **Notes**: Ensure the model captures uncertainty and provides realistic future estimates.

### 8. `validate_model(predictions, actual_data)`
- **Purpose**: Validates the predictive model by comparing the forecasted estimates with actual data (if available).
- **Input**: Model predictions and actual data for comparison.
- **Output**: Model performance metrics and validation analysis.
- **Notes**: Use appropriate metrics to evaluate model accuracy and reliability.

---

## Additional Information

- **Geodetic Distance Computation**: If you're not familiar with GIS tools, use the provided example code or Python libraries like `geopy` to calculate distances accurately.
- **Data Simplification**: The project uses simplified assumptions, such as estimating smoke impact without precise fire start and end dates, to make the analysis feasible.
- **US EPA AQI Data**: Understanding the nature of AQI measures and their limitations is crucial for comparing them with your smoke estimate.

---

## Setup Instructions

1. **Install Required Libraries**:
   ```bash
   pip install geopandas pandas geopy requests```
2. **Request an API Key**: 
		Visit the US EPA AQS API portal and request an API key for accessing AQI data.
---

## License

This project includes code and data that are licensed under various open-source licenses. Please refer to the individual files and data sources for specific licensing information.

- Sample code provided by [Dr. David McDonald](#) is licensed under **CC-BY 4.0**.
- Data retrieved from external sources, such as the US EPA and fire data archives, are subject to their respective licenses.

---

## Acknowledgments

- **Dr. David McDonald**: For providing sample code and guidance throughout this project.
- **ChatGPT**: For assisting in generating some of the code functions used in this project.
- **The Wikimedia Foundation**: For providing access to data and APIs.

## Notes

- **Data Availability**: Ensure that you have access to the required wildfire and AQI datasets before running the analysis.
- **Model Limitations**: The predictive model is an estimate and should be treated as such. Be sure to highlight any limitations or areas for future improvement in your analysis.

For questions or issues, please contact the course instructor or refer to the course materials for guidance.


