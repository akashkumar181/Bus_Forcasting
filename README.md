# Bus Passenger-Demand Forecasting

### AI & Machine Learning | ALGIONS AI LABS PRIVATE LIMITED

## 1. Project Overview

Bus Passenger-Demand Forecasting is a machine learning-based decision-support system designed to predict passenger demand for different bus routes and departure dates/times.

The project helps bus operators understand travel demand, identify peak periods, optimize seat allocation and make better transportation scheduling decisions.

The solution uses historical trip-level data, booking information, route characteristics, calendar features and weather forecast features to estimate the expected number of passengers for an upcoming trip.

The project includes data preprocessing, exploratory data analysis, feature engineering, machine learning model development, evaluation and an interactive Streamlit dashboard.

**Important:** The current assessment dataset is synthetic and generated for demonstration and reproducibility. It does not represent actual company booking records.

## 2. Business Problem

Bus operators face challenges in estimating passenger demand across different routes and departure times.

Underestimating demand can lead to insufficient seating capacity, while overestimating demand can result in underutilized buses and operational costs.

This project addresses the problem by forecasting passenger counts at the individual trip level.

### Business Objectives

- Forecast passenger demand for different routes.
- Identify high-demand and low-demand departure periods.
- Analyze weekday, weekend and seasonal demand patterns.
- Support bus capacity and scheduling decisions.
- Compare machine learning predictions against historical demand baselines.
- Provide an interactive dashboard for business users.

## 3. Problem Definition

| Component | Definition |
|---|---|
| Problem Type | Supervised Machine Learning – Regression |
| Prediction Unit | Individual bus trip |
| Target Variable | `passenger_count` |
| Prediction Horizon | 7 days before departure |
| Evaluation | MAE, RMSE and WAPE |
| Primary Objective | Estimate expected passenger count |

The model is intended to support operational planning. It does not automatically make scheduling or high-stakes business decisions.

## 4. Dataset Description

**Dataset:** `bus_passenger_demand_synthetic_2025.csv`

| Attribute | Details |
|---|---|
| Total Records | 17,520 |
| Total Columns | 17 |
| Routes | 12 |
| Date Coverage | January–December 2025 |
| Data Format | CSV / Excel |
| Data Source | Reproducible synthetic data generator |
| Random Seed | 42 |

### Dataset Features

| Feature | Description |
|---|---|
| `trip_id` | Unique trip identifier |
| `route_id` | Bus route identifier |
| `source` | Departure city |
| `destination` | Arrival city |
| `departure_date` | Scheduled departure date |
| `departure_time` | Scheduled departure time |
| `day_of_week` | Day of the week |
| `month` | Departure month |
| `season` | Summer, Winter or Monsoon |
| `bus_capacity` | Total seating capacity |
| `booking_lead_days` | Forecast lead time |
| `booked_seats_7d_before` | Seats booked seven days before departure |
| `historical_route_time_avg_28d` | Historical route/time demand average |
| `historical_same_weekday_avg_4w` | Historical same-weekday demand average |
| `weather_forecast_temp_c` | Forecast temperature |
| `weather_forecast_rain_probability` | Forecast rainfall probability |
| `passenger_count` | Actual passenger count (target) |

## 5. Project Workflow

The project follows a structured machine learning pipeline:

1. Dataset collection and generation.
2. Dataset understanding and profiling.
3. Exploratory Data Analysis (EDA).
4. Missing-value analysis and treatment.
5. Duplicate record detection.
6. Outlier detection using Boxplots and IQR.
7. Correlation analysis.
8. Feature engineering.
9. Categorical encoding and numerical scaling.
10. Chronological train-validation-test splitting.
11. Baseline development.
12. Machine learning model training.
13. Model evaluation and error analysis.
14. Model serialization.
15. Streamlit dashboard development.

## 6. Exploratory Data Analysis

EDA is performed to understand passenger demand patterns, data quality and relationships between variables.

### Planned Visualizations

- Passenger demand distribution using histograms.
- Passenger count outlier analysis using boxplots.
- Route-wise passenger demand comparison.
- Monthly demand trends.
- Weekday versus passenger demand.
- Hourly passenger demand analysis.
- Peak versus off-peak demand.
- Seasonal demand distribution.
- Numerical feature correlation heatmap.
- Bus capacity versus passenger demand.

## 7. Data Preprocessing

Data preprocessing includes:

- Identifying and handling missing values.
- Checking duplicate records.
- Validating numerical and categorical data types.
- Detecting invalid and extreme values.
- Investigating outliers using the IQR method.
- Handling missing numerical features using appropriate imputation techniques.
- Handling categorical missing values.
- Removing or investigating invalid target observations.

Outliers are not automatically removed. Genuine peak passenger demand is retained because it is important for forecasting.

Imputation and scaling parameters are learned using training data only.

## 8. Feature Engineering

New features are derived from existing trip information to improve model performance.

Examples include:

- Departure hour.
- Weekend indicator.
- Peak/off-peak indicator.
- Month and season.
- Historical route demand.
- Historical same-weekday demand.

Historical features are designed to use information available before the seven-day forecast cutoff.

## 9. Train, Validation and Test Strategy

Since passenger demand depends on time, chronological splitting is used instead of random splitting.

| Dataset | Proportion | Purpose |
|---|---:|---|
| Training | 80% | Model training |
| Validation | 10% | Model selection and tuning |
| Testing | 10% | Final unseen evaluation |

The final test set is kept separate from model tuning.

## 10. Machine Learning Models

The following models will be evaluated:

1. Historical route/time demand baseline.
2. Linear Regression.
3. Random Forest Regressor.
4. XGBoost Regressor (optional candidate).

The best-performing model will be selected based on validation performance and business requirements.

## 11. Model Evaluation

Regression performance will be measured using:

### Mean Absolute Error (MAE)

Measures the average absolute difference between actual and predicted passenger counts.

### Root Mean Squared Error (RMSE)

Penalizes larger prediction errors more heavily.

### Weighted Absolute Percentage Error (WAPE)

Measures total absolute prediction error relative to total actual passenger demand.

Model performance will be compared across:

- Overall test data.
- Individual bus routes.
- Peak-hour trips.
- Off-peak trips.

Actual evaluation results will be added after training. No performance figures are assumed in advance.

## 12. Interactive Dashboard

An interactive Streamlit dashboard will provide:

### Dashboard Modules

**Overview**

- Total trips.
- Total passenger count.
- Average bus occupancy.
- Number of routes.

**Exploratory Data Analysis**

- Passenger demand distribution.
- Route-wise analysis.
- Monthly and seasonal trends.
- Hourly demand patterns.
- Missing-value analysis.
- Outlier visualization.

**Route Analysis**

- Route comparison.
- Highest-demand routes.
- Lowest-demand routes.

**Demand Forecasting**

- Route selection.
- Departure date and time.
- Bus capacity.
- Seven-day booking information.
- Predicted passenger count.
- Expected seat occupancy.
- Capacity-related warning.

**Model Performance**

- MAE, RMSE and WAPE.
- Actual versus predicted comparison.
- Residual analysis.
- Route-wise and peak/off-peak error analysis.

Predictions will be generated using the saved preprocessing and trained model artifacts rather than hard-coded sample outputs.

## 13. Technology Stack

| Technology | Purpose |
|---|---|
| Python | Programming |
| Pandas | Data manipulation |
| NumPy | Numerical computation |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Plotly | Interactive charts |
| Scikit-learn | Machine learning and preprocessing |
| XGBoost | Advanced regression (if selected) |
| Streamlit | Interactive dashboard |
| Joblib | Model serialization |
| Git & GitHub | Version control |

## 14. Project Structure

```text
Bus-Passenger-Demand-Forecasting/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_Data_Understanding.ipynb
│   ├── 02_EDA.ipynb
│   ├── 03_Data_Cleaning.ipynb
│   ├── 04_Feature_Engineering.ipynb
│   └── 05_Model_Training.ipynb
├── src/
│   ├── data_generator.py
│   ├── preprocessing.py
│   ├── train.py
│   ├── evaluate.py
│   └── predict.py
├── models/
│   └── bus_demand_model.pkl
├── tests/
│   └── test_prediction.py
├── app.py
├── requirements.txt
├── README.md
└── report.pdf
```

## 15. Installation and Setup

Clone the repository:

```bash
git clone https://github.com/akashkumar181/Bus_Forcasting.git
cd Bus_Forcasting
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## 16. Running the Project

### Step 1: Generate or prepare the dataset

```bash
python src/data_generator.py
```

### Step 2: Train the model

```bash
python src/train.py
```

### Step 3: Evaluate the model

```bash
python src/evaluate.py
```

### Step 4: Run the dashboard

```bash
streamlit run app.py
```

Commands should match the final implemented repository structure.

## 17. Limitations and Responsible Use

- The dataset is synthetic and may not fully represent real-world passenger behavior.
- New routes may have insufficient historical information.
- Unexpected events, strikes, road closures and severe weather may affect demand.
- Seasonal and holiday patterns may differ between actual operators.
- Forecasts are estimates and should not be interpreted as guaranteed passenger counts.
- Human review is required before making capacity and scheduling decisions.
- No personal passenger information is included in the dataset.

## 18. Reproducibility

- Fixed random seed: 42.
- Dataset generation instructions are provided.
- Chronological data splitting is used.
- Preprocessing and model artifacts are saved.
- Training and inference instructions are documented.
- Tests are included for preprocessing and prediction.

## 19. Project Deliverables

- Source code and Jupyter notebooks.
- Synthetic dataset and generator.
- EDA and data preprocessing.
- Trained machine learning model.
- Evaluation report.
- Interactive Streamlit dashboard.
- Technical documentation.
- Project demonstration video.

## 20. Author

**Name:** Akash Kumar  
**Project:** Bus Passenger-Demand Forecasting  
**Domain:** AI & Machine Learning  
**Organization:** ALGIONS AI LABS PRIVATE LIMITED  
**GitHub:** https://github.com/akashkumar181

---

**Project Status:** In Development

This documentation will be updated with actual model results, dashboard screenshots, inference instructions and final implementation details as development progresses.
