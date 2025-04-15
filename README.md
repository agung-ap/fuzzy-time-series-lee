# Stock Price Prediction using Fuzzy Time Series

## Overview
This Python script implements a Fuzzy Time Series (FTS) model to predict stock closing prices. The model analyzes historical stock price data, creates fuzzy sets, establishes fuzzy logic relationships, and generates predictions based on these relationships. It also calculates the Mean Absolute Percentage Error (MAPE) to evaluate prediction accuracy.

## Requirements
- Python 3.x
- pandas
- math (standard library)

## Installation
```bash
pip install pandas
```

## Input Data
The script reads stock price data from a CSV file located at `data/closing_price.csv`. This file should contain a column named 'Close' with the historical closing prices.

## How It Works

The FTS prediction model follows these steps:

1. **Data Loading**: Reads historical closing prices from a CSV file.

2. **Universe of Discourse Partitioning**:
   - Calculates the number of intervals using Sturges' formula: `k = 1 + 3.3 * log10(n)`
   - Computes the length of each interval
   - Determines the lower and upper bounds of each interval

3. **Fuzzification**:
   - Assigns each closing price to the appropriate fuzzy set (interval)
   - Calculates midpoints for each interval
   - Establishes membership degrees for the fuzzy sets

4. **Fuzzy Logical Relationship (FLR) Formation**:
   - Creates relationships between consecutive fuzzy sets
   - Groups these relationships based on current states

5. **Defuzzification**:
   - Calculates weighted average values for each fuzzy set group
   - Generates predictions based on these values

6. **Performance Evaluation**:
   - Computes the absolute difference between actual and predicted values
   - Calculates MAPE (Mean Absolute Percentage Error)

## Output
The script prints the following information:
- Number of data points
- Number of intervals
- Length of each interval
- Lower and upper bounds of intervals
- Midpoint values of intervals
- Fuzzy membership degrees
- Fuzzification results
- Fuzzy Logical Relationships groups
- Defuzzification values
- Prediction results
- MAPE value

## Example Usage
```python
python stock_prediction.py
```

## Customization
To adapt this script for different datasets:
1. Change the input file path in `pd.read_csv('data/closing_price.csv')`
2. Adjust column names if your CSV has different header names

## Performance
The model's accuracy is measured using MAPE, with lower values indicating better predictions. The script outputs the MAPE value at the end of execution.

## Notes
- The script uses the first-order FTS model, meaning it only considers the immediate previous state for predictions
- The number of predictions will be one less than the number of data points
- Make sure your dataset has no missing values in the 'Close' column
