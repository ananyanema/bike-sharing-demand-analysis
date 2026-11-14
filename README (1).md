# Bike Sharing Demand Analysis

An end-to-end analysis and regression pipeline in Python that explains and predicts daily bike rental demand from weather, season, and calendar features.

## Dataset

`day.csv`: 730 daily records from 2018 to 2019 with weather (temperature, humidity, wind speed, weather situation), season, month, weekday, holiday, and working-day fields. The target is `cnt`, the total daily rentals.

## Workflow

1. **Cleaning:** removed `instant` (row index), `casual` and `registered` (they add up to the target, so keeping them would leak it), and `temp` (0.99 correlated with `atemp`).
2. **Feature preparation:** converted dates and decoded numeric codes into readable labels (season, month, weekday, weather), then one-hot encoded the categorical variables.
3. **Exploratory analysis:** bar charts of rentals by season, month, weekday, and weather; a demand trend over time; scatter plots of temperature, humidity, and wind speed against rentals; a correlation heatmap.
4. **Modeling:** Linear Regression on an 80/20 train-test split, evaluated with R² and MAE.

## Key findings

- Rentals grew strongly from 2018 to 2019 (about 1.24 million to 2.05 million total rentals, roughly 65% more).
- Demand peaks from June to September, and fall is the highest season by total rentals.
- Registered users account for about 81% of all rentals.

## Model results

| Set | R² | MAE (rentals per day) |
| --- | --- | --- |
| Train | 0.85 | 546 |
| Test | 0.83 | 615 |

The small gap between train and test R² shows minimal overfitting.

## Tech stack

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn

## Run it

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook Bike_Sharing_Demand_Analysis.ipynb
```

Keep `day.csv` in the same folder as the notebook.

## Author

Ananya Nema | [LinkedIn](https://linkedin.com/in/ananya-nema-434970264)
