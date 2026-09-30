# NYC Yellow Taxi Trip Analysis 2023

## Project Overview

This project applies **Exploratory Data Analysis (EDA)** to the **2023 New York City Yellow Taxi trip dataset** to identify demand patterns, fare and revenue trends, passenger behaviour, payment preferences, surcharge patterns, and location-based operational insights.

The project was completed as part of the **Programming for ML and AI** module of the **Executive Post Graduate Programme in Applied AI and Agentic AI**.

The analysis demonstrates how large transportation datasets can be cleaned, explored, visualised, and converted into practical recommendations for fleet deployment, pricing, routing, and demand planning.

## Business Objective

The main objectives were to:

- Understand taxi demand across hours, weekdays, weekends, months, and locations.
- Analyse the relationship between trip distance, fare amount, tips, and passenger count.
- Identify high-demand pickup and drop-off zones.
- Examine payment methods, surcharges, vendor pricing, and revenue patterns.
- Develop data-driven recommendations for fleet positioning, dispatching, and pricing.

## Dataset

The project uses the **NYC Yellow Taxi Trip Records for 2023**. The source files are stored in **Parquet (`.parquet`) format**.

The data includes fields such as:

- Pickup and drop-off date and time
- Pickup and drop-off location IDs
- Trip distance
- Fare and total amount
- Rate code
- Payment type
- Tip amount
- Tolls and surcharges
- Driver-reported passenger count

Each monthly Parquet file contains approximately **3 million records**. To process the data efficiently, a **5% random sample** was selected from every hour of each day across the monthly files. The sampled files were then combined into a DataFrame containing **3,374,086 rows and 19 columns**.

## Tools and Libraries

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- GeoPandas
- Jupyter Notebook
- Parquet

Versions used during the assignment:

- NumPy: 2.5.3
- Pandas: 3.0.6
- Matplotlib: 3.11.2
- Seaborn: 0.13.2
- GeoPandas: 1.1.4

## Project Workflow

### 1. Data Sampling and Preparation

- Loaded monthly Yellow Taxi Parquet files.
- Processed records day by day and hour by hour.
- Randomly sampled 5% of the records from each hour.
- Combined the sampled records into one yearly DataFrame.
- Reset the DataFrame index and removed temporary columns that were no longer required.
- Consolidated duplicate airport fee columns into one standardised field.

### 2. Data Cleaning

- Calculated the percentage of missing values in each column.
- Filled missing `passenger_count` and `RatecodeID` values using the mode.
- Filled missing `congestion_surcharge` values using the median.
- Removed invalid payment type records.
- Removed unrealistic trip-distance and fare combinations.
- Retained zero-tip records because tipping is optional.
- Removed inconsistent trips with zero distance but different pickup and drop-off locations.

### 3. Exploratory Data Analysis

The analysis covered:

- Pickup demand by hour, weekday, and month
- Monthly and quarterly revenue trends
- Relationship between trip distance and fare amount
- Relationship between trip distance and tip amount
- Distribution of payment types
- Pickup and drop-off activity by taxi zone
- Busy hours and weekday-versus-weekend traffic
- Daytime and nighttime revenue share
- Fare per mile by hour, weekday, passenger count, and vendor
- Vendor pricing across distance tiers
- Tip percentage patterns
- Passenger-count trends
- Surcharge frequency and revenue contribution

### 4. Geospatial Analysis

- Loaded the NYC taxi-zone shapefile using GeoPandas.
- Merged taxi-zone data with trip records using `LocationID` and `PULocationID`.
- Calculated trip counts by zone.
- Visualised pickup activity across NYC taxi zones.

## Key Findings

- Taxi demand followed a predictable daily pattern, with the highest pickup volumes during evening rush hours.
- The busiest hour was **6 PM (18:00)** in the sampled dataset.
- Early morning, particularly between **4 AM and 5 AM**, had the lowest demand.
- Revenue was relatively stable, with May and October recording the highest levels and February and August the lowest.
- Trip distance and fare amount had a positive relationship.
- Credit cards were the dominant payment method, with cash as the second most common method.
- Airports, transit hubs, business districts, tourist locations, and entertainment areas generated high trip activity.
- Daytime trips contributed **87.94%** of revenue, while nighttime trips contributed **12.06%**.
- Medium-distance trips had the highest average tip percentage.
- Solo travellers tipped more on average than larger passenger groups.
- Evening trips had the highest average tip percentage.
- Vendor 2 generated a higher fare per mile than Vendor 1, especially for short trips.
- Congestion surcharges made a significant revenue contribution because they were both frequent and relatively high in value.

## Business Recommendations

### Fleet Deployment

- Position more taxis near airports, transit hubs, business districts, tourist attractions, and entertainment areas.
- Increase taxi availability during morning and evening rush hours.
- Provide additional coverage in nightlife districts during evenings and weekends.
- Reposition taxis from low-demand areas to nearby high-demand zones.

### Demand Planning

- Use historical hourly, daily, and monthly patterns to forecast demand.
- Monitor pickup and drop-off activity by zone.
- Reduce idle time by aligning fleet availability with expected demand.

### Pricing

- Review surcharge usage regularly and apply additional charges only when demand justifies them.
- Monitor vendor pricing and market conditions.
- Evaluate the reasons behind vendor-level fare-per-mile differences.
- Test and refine pricing strategies using trip and revenue data.

### Customer and Operational Experience

- Improve service coverage in underserved high-demand areas.
- Consider ride-sharing options in locations with frequent group travel.
- Communicate surcharges clearly to passengers.
- Combine historical data with real-time demand monitoring for dispatch decisions.

## Repository Structure

```text
EDA/
├── notebooks/             # Jupyter notebooks used for the analysis
├── reports/               # Final analysis report
├── images/                # Charts, maps, and visualisations
├── requirements.txt       # Python dependencies
└── README.md              # Project documentation
```

> Large datasets should not be committed directly to GitHub. Add raw data files to `.gitignore` and provide official download instructions instead.

## How to Run the Project

1. Clone the repository:

```bash
git clone https://www.github.com/EDA
cd EDA
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
```

3. Install the required libraries:

```bash
pip install -r requirements.txt
```

4. Place the required Parquet files and taxi-zone shapefile in the appropriate data folders.

5. Open the Jupyter Notebook and run the cells in sequence:

```bash
jupyter notebook
```

## Suggested `requirements.txt`

```text
numpy==2.5.3
pandas==3.0.6
matplotlib==3.11.2
seaborn==0.13.2
geopandas==1.1.4
jupyter
pyarrow
```

## Skills Demonstrated

- Python programming
- Large-dataset sampling
- Data cleaning and preprocessing
- Missing-value treatment
- Outlier handling
- Exploratory Data Analysis
- Data visualisation
- Geospatial analysis
- Business insight generation
- Data-driven recommendation development

## Learning Experience

This assignment provided a valuable hands-on learning experience in applying Python and EDA techniques to a large, real-world transportation dataset. It strengthened practical understanding of data preparation, analysis, visualisation, and the conversion of technical findings into meaningful business recommendations.

## Contact

If you are working on a similar EDA, Python, Pandas, data-cleaning, or visualisation project and need help, feel free to connect with me.

## Disclaimer

This repository is intended for educational purposes. Dataset usage is subject to the terms and conditions of the original data provider.
