# 🌍 Climate & Air Quality Trends Analysis
## 🚀 Project Overview

This project analyzes **climate and air quality trends** using historical and live datasets from multiple sources such as meteorological stations, IoT sensors, and open government data.
The goal is to provide insights into air pollution levels, temperature patterns, and environmental risks over time to support data-driven environmental monitoring and decision-making.
## 🎯 Objectives

- Collect and integrate air quality and climate datasets.

- Perform trend analysis and identify anomalies over time.

- Visualize air quality indices, temperature, humidity, and pollutant levels.

- Correlate climate factors with pollution and seasonal effects.

- Build interactive dashboards for monitoring and decision support.

## 🧠 Key Features

✅ Collects climate and air quality data from multiple sources.

✅ Preprocesses data to handle missing values and inconsistencies.
  
✅ Performs statistical and trend analysis on temperature, pollutants, and AQI.

✅ Generates visualizations for spatial and temporal patterns.

✅ Supports predictive modeling of air quality trends.

✅ Deploys interactive dashboards (Power BI / Streamlit) for monitoring.

🛠️ Tools & Technologies
| Category	    |Tools / Libraries|
|--------------|-------------------|
| Data Collection	                 |Pandas, Requests, OpenAQ API, NOAA API|
|Data Cleaning & Transformation    |Pandas, NumPy, Geopandas|
|Analysis & Modeling	             |Scikit-learn, Statsmodels|
|Visualization                     |Power BI, Matplotlib, Seaborn, Plotly|
|Database / Storage                |PostgreSQL, CSV, Parquet|
|Deployment                        |Streamlit, Flask, Airflow|

## ⚙️ Workflow
## 🌍 Power BI Report Spec: Climate & Air Quality Trends Analysis
### 1️⃣ Report Overview

The Power BI report visualizes climate and air quality trends using historical and live data. It supports monitoring, trend analysis, and anomaly detection for environmental decision-making.

**Purpose:**

- Track AQI (Air Quality Index) trends across regions.

- Monitor temperature, humidity, and pollutant levels.

- Identify hotspots and seasonal changes in air quality.

- Support predictive modeling insights.
### 2️⃣ Data Sources
|Source	                             |Type	            |Description
|------------------------------------|------------------|----------------------------------------------------------------------|
|OpenAQ API                          |	JSON / API	    |Real-time pollutant data (PM2.5, PM10, CO, NO2, SO2)|
|NOAA / Meteorological Stations      |	CSV / API	      |Historical climate data (temperature, humidity, wind speed)|
|Local IoT Sensors                   |	CSV	            |Hyperlocal air quality readings|
|Processed Metrics                   |	CSV / Parquet   |Aggregated metrics like daily AQI, pollutant averages, temperature trends|

### 3️⃣ Data Model

- Fact Table: `Fact_AirQuality`

   - Date, City, AQI, PM2.5, PM10, CO, NO2, SO2, Temperature, Humidity, WindSpeed

- Dimension Tables:

  - `Dim_City` (CityID, CityName, Region)

  - `Dim_Date` (Date, Year, Month, Day, Weekday)

  - `Dim_Pollutant` (PollutantID, Name, Unit, Threshold)

Relationships:

- `Fact_AirQuality.CityID → Dim_City.CityID`

- `Fact_AirQuality.Date → Dim_Date.Date`

- `Fact_AirQuality.PollutantID → Dim_Pollutant.PollutantID`

### 4️⃣ Key KPIs & Measures

| KPI / Measure                  | DAX Formula Example                                                 | Purpose                        |
| ------------------------------ | ------------------------------------------------------------------- | ------------------------------ |
| Average AQI                    | `AVERAGE(Fact_AirQuality[AQI])`                                     | Track air quality trends       |
| Max Pollutant Level            | `MAX(Fact_AirQuality[PM2.5])`                                       | Identify peak pollution events |
| Daily AQI Change               | `Fact_AirQuality[AQI] - CALCULATE(LASTDATE(Fact_AirQuality[Date]))` | Trend monitoring               |
| Hazardous Day Count            | `COUNTROWS(FILTER(Fact_AirQuality, Fact_AirQuality[AQI] > 150))`    | Alert generation               |
| Temperature vs AQI Correlation | `CORREL(Fact_AirQuality[Temperature], Fact_AirQuality[AQI])`        | Environmental factor analysis  |

### 5️⃣ Visualizations

| Page                  | Visual                  | Description                                |
| --------------------- | ----------------------- | ------------------------------------------ |
| **Overview**          | Line Chart              | Daily AQI trends across regions            |
| **Pollutants**        | Multi-row Card / Table  | PM2.5, PM10, CO, NO2, SO2 values           |
| **Spatial Analysis**  | Filled Map              | Geographic AQI hotspots                    |
| **Climate Trends**    | Line Chart / Area Chart | Temperature, Humidity, WindSpeed over time |
| **Seasonal Analysis** | Clustered Bar           | Average pollutant levels by season         |
| **Alerts & KPI**      | Card                    | Count of days exceeding AQI threshold      |



### 6️⃣ Filters & Slicers

- Date Range (Day / Week / Month / Year)

- City / Region Selector

- Pollutant Type (PM2.5, PM10, CO, NO2, SO2)

- AQI Category (Good, Moderate, Unhealthy, Hazardous)


### 7️⃣ Dashboard Layout

- **Top Section:** KPIs & Summary Cards

- **Middle Section:** Trend Line Charts (AQI, Climate Parameters)

- **Bottom Section:** Map & Alerts Visuals

- **Sidebar / Slicers:** Date, Region, Pollutant Filters


### 8️⃣ Automation & Refresh

- Daily ETL refresh to update datasets.

- Power BI Service scheduled refresh for dashboards.

- Email or Teams alerts for AQI above threshold.

### 9️⃣ Notes / Recommendations

- Use **direct query mode** for real-time IoT or API-based datasets.

- Pre-aggregate historical data for performance efficiency.

- Highlight hazardous days using conditional formatting.

- Integrate predictive AQI trends if models are available.

## 📁 Project Structure
### 📦 climate-air-quality-analysis

```plaintext
├── data/                    # Raw and processed datasets
├── notebooks/               # Jupyter notebooks for EDA and analysis
├── scripts/                 # Python scripts for ETL, cleaning, and analysis
│   ├── load_data.py
│   ├── clean_data.py
│   ├── feature_engineering.py
│   ├── trend_analysis.py
│   ├── visualize_results.py
├── dashboard/               # Power BI / Streamlit dashboard files
├── models/                  # Optional predictive AQI model
├── docs/                    # Workflow and Power BI spec files
├── requirements.txt         # Python dependencies
└── README.md                # Project documentation
```
