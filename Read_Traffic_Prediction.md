## Part 2 – Predicting Hourly Traffic Volume with Random Forest

In this section, we build a regression model to predict **hourly traffic volume** using historical weather and time data. This supports better demand forecasting and traffic planning for urban infrastructure.

---

### Before vs After: Model Improvement Journey

| Step                | R² Score | MSE     | MAE     |
|---------------------|----------|---------|---------|
| **Initial Model**   | 0.17     | 0.0618  | 0.198   |
| **After Feature Engineering** | **0.9477** | **0.0039** | **0.0345** |

Key improvements:
- Added meaningful time-based features (`hour`, `weekday`, `rush_hour`, `is_weekend`)
- Scaled numeric features and encoded categorical ones
- Model performance improved **from poor to excellent**

---

### Data Preprocessing & Feature Engineering

We created several new features from the `date_time` column and encoded others:

```python
# Feature engineering
df['hour'] = df['date_time'].dt.hour
df['weekday'] = df['date_time'].dt.weekday
df['month'] = df['date_time'].dt.month
df['is_weekend'] = df['weekday'].isin([5, 6]).astype(int)
df['rush_hour'] = df['hour'].isin([7, 8, 16, 17, 18]).astype(int)

# Encoding & scaling
LabelEncoder() for holiday, weather_main, weather_description
MinMaxScaler() for temp and traffic_volume
```

---

### Model: Random Forest Regressor

```python
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

### Evaluation Results

| Metric                   | Value     |
|--------------------------|-----------|
| R² Score                 | 0.9477    |
| Mean Squared Error (MSE) | 0.00389   |
| Mean Absolute Error (MAE)| 0.03446   |

---

### Feature Importance

| Feature              | Importance |
|----------------------|------------|
| `hour`               | 81.77%     |
| `weekday`            | 7.26%      |
| `is_weekend`         | 3.77%      |
| `temp`               | 3.50%      |
| `month`              | 1.01%      |
| `rush_hour`          | 0.92%      |
| `clouds_all`         | 0.57%      |
| `weather_description`| 0.52%      |
| `weather_main`       | 0.39%      |
| `rain_1h`            | 0.26%      |
| `snow_1h`            | 0.02%      |
| `holiday`            | 0.003%     |

Time-of-day (`hour`) was by far the strongest predictor, dominating model accuracy.

---

### Takeaways

- **Time-based patterns** (especially `hour` and `weekday`) drive traffic volume far more than weather or holidays.
- Feature engineering is **critical** in unlocking predictive performance.
- Model is now highly accurate and ready for deployment or dashboard integration.

---

Download the processed dataset here:  
**[Engineered_Metro_Interstate_Traffic_Data.csv](./Datasets/Preprocessed_Metro_Interstate_Traffic_Data.csv)**  
(Contains encoded and scaled features for reproducibility)

