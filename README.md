# Energy Consumption Analysis

## Machine Learning and Python — Individual Assignment 2024/25

This project analyses energy consumption patterns using two datasets: PJME hourly electricity demand and individual household power consumption.

---

## Datasets

| Dataset | Description | Records |
|---------|-------------|---------|
| **PJME_hourly.csv** | Hourly electricity demand for the PJM East region | ~145,000 |
| **household_power_consumption.txt** | Individual household electric power consumption (2006-2010) | ~2,000,000 |

---

## Part 1: PJME Hourly Energy Consumption

- **Statistical Analysis**: Mean, median, standard deviation, min, max, range
- **Missing Values**: NaN check and handling strategy
- **Outlier Detection**: IQR method (3,455 outliers detected, 2.38%)
- **Time Series Visualization**: Hourly, daily, monthly consumption patterns
- **Seasonal Analysis**: Weekdays vs weekends, winter vs summer
- **Distribution Analysis**: Histogram and boxplot (right-skewed distribution)
- **K-Means Clustering**: Elbow method for optimal k, daily consumption profiles (24 features per day)

## Part 2: Household Power Consumption

- **Seasonality & Trends**: Monthly consumption patterns across years
- **Daily & Hourly Averages**: Average daily consumption 1.087 kW
- **Correlation Analysis**: Voltage vs Power (Pearson r = -0.396), pair plot, correlation heatmap
- **Multiple Linear Regression**: R² = 0.9982, RMSE = 0.0448, MAE = 0.0296, feature importance, reduced model
- **K-Means Clustering**: StandardScaler normalization, elbow method, cluster analysis with heatmap

---

## Results

### Statistical Analysis (PJME)
- Mean: 32,080 MW | Median: 31,421 MW | Std: 6,464 MW
- Range: 14,544 — 62,009 MW (47,465 MW)

### K-Means Clustering (PJME)
- Optimal clusters: **k=4**
- Cluster 0: 788 days, mean 40,274 MW, peak 17h (high-demand winter workdays)
- Cluster 1: 2,146 days, mean 32,206 MW, peak 18h (typical workdays)
- Cluster 2: 2,270 days, mean 27,659 MW, peak 21h (weekends and holidays)
- Cluster 3: 823 days, mean 36,260 MW, peak 19h (summer high-cooling days)

### Multiple Linear Regression (Household)
- R² = 0.9982 (due to physical relationship P = V × I)
- Global_intensity dominates feature importance (coefficient: 0.236)
- Reduced model (3 features) performs equally to full model

### K-Means Clustering (Household)
- Optimal clusters: **k=4**
- Cluster 0: Low-consumption idle periods (night-time)
- Cluster 1: Moderate morning/evening activity
- Cluster 2: High evening peak (heating, cooking)
- Cluster 3: Extreme peak (simultaneous high-power appliances)

---

## How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn kneed statsmodels
```

1. Place notebook and datasets in the same folder
2. Open in Jupyter or VS Code
3. Run All

---

## Technologies

- Python 3.x
- scikit-learn (KMeans, LinearRegression)
- pandas, numpy
- matplotlib, seaborn
- KneeLocator (elbow method)
- statsmodels
