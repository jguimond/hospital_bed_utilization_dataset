# 🏥 Hospital Unit Bed Utilization Dataset

This dataset contains aggregated daily-level bed utilization metrics for multiple hospital units across facilities.  
It was prepared for predictive modeling and time-series forecasting related to healthcare operations, such as bed management, staffing, and capacity planning.

---

## 📊 Dataset Overview

| Attribute            | Description                          |
|----------------------|--------------------------------------|
| **Total Rows**       | 47,739                               |
| **Total Columns**    | 31                                   |
| **Time Span**        | 2017 to 2025                         |
| **Granularity**      | Daily (per unit per facility)        |
| **Format**           | CSV (`unit_daily_aggregated.csv`)    |
| **File Size**        | ~7.5 MB (approx)                     |

---

## 📁 File Contents

The CSV contains one row per **unit per day**, with aggregated bed occupancy data, patient movement counts, temporal features, and unit attributes.  
It is designed to support time series analysis and machine learning.

| Column Name                    | Type        | Description                                                                 |
|--------------------------------|-------------|-----------------------------------------------------------------------------|
| `date`                         | Date        | Calendar date                                                              |
| `facility_id`                  | String      | Unique identifier of the facility                                          |
| `unit_id`                      | String      | Unique identifier of the unit (within facility)                            |
| `unit_name`                    | String      | Descriptive name of the unit (e.g., "ICU", "3 North")                      |
| `total_beds`                   | Integer     | Total licensed capacity of the unit                                        |
| `occupied_beds`                | Integer     | Number of beds occupied on this date                                       |
| `unoccupied_beds`              | Integer     | Number of licensed beds not currently occupied                             |
| `utilization_percent`          | Float       | Percentage of total beds occupied (`occupied_beds / total_beds * 100`)     |
| `admits_today`                 | Integer     | Count of patients admitted into the unit on this date                      |
| `discharges_today`             | Integer     | Count of patients discharged from the unit on this date                    |
| `avg_length_of_stay`           | Float       | Average patient length of stay (in days) among discharges today            |
| `day_of_week`                  | String      | Name of the day (e.g., "Monday")                                           |
| `week_of_month`                | Integer     | Week number within the month (1-5)                                         |
| `month_of_year`                | Integer     | Month number (1=January … 12=December)                                     |
| `season_of_year`               | String      | Meteorological season (e.g., "Spring")                                     |
| `is_weekend`                   | Boolean     | Whether the day is a Saturday or Sunday                                    |
| `is_med_surge`                 | Boolean     | Whether the unit is a Med-Surg unit                                        |
| `is_intermediate_care`         | Boolean     | Whether the unit is Intermediate Care                                      |
| `is_icu`                       | Boolean     | Whether the unit is Intensive Care (ICU)                                   |
| `is_pediatric`                 | Boolean     | Whether the unit is Pediatric                                              |
| `is_labor_and_delivery`        | Boolean     | Whether the unit supports Labor & Delivery                                 |
| `is_obs`                       | Boolean     | Whether the unit is an Observation unit                                    |
| `is_psych`                     | Boolean     | Whether the unit is Psychiatric                                            |
| `is_nicu`                      | Boolean     | Whether the unit is Neonatal ICU                                           |
| `lag_utilization_1d`           | Float       | Utilization % 1 day ago (lag)                                              |
| `lag_utilization_7d`           | Float       | Utilization % 7 days ago (lag)                                             |
| `rolling_utilization_3d_avg`   | Float       | Rolling 3-day average of utilization %                                     |
| `rolling_utilization_7d_avg`   | Float       | Rolling 7-day average of utilization %                                     |
| `delta_utilization_1d`         | Float       | Day-over-day change in utilization                                         |

---

## 🔍 Usage Examples

This dataset is ideal for:

- Time-series forecasting of hospital bed utilization
- Predictive analytics for census-based staffing models
- Exploring patient-flow dynamics across healthcare units
- Operational analytics for hospital planning and logistics

Example code for loading the data in Python with Pandas:

```python
import pandas as pd

df = pd.read_csv("unit_daily_aggregated.csv", parse_dates=["date"])
print(df.head())
