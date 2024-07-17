# Gold Price Prediction

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Python Libraries](#python-libraries)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Model Training](#model-training)
- [Model Evaluation](#model-evaluation)
- [Results](#results)
- [Limitations](#limitations)
- [References](#references)

### Project Overview

This project aims to predict the price of gold (GLD) based on several other stock prices and financial indicators. The dataset includes historical data of the S&P 500 index (SPX), United States Oil Fund (USO), iShares Silver Trust (SLV), EUR/USD exchange rate and SPDR Gold Shares (GLD).

### Data Sources

Stock data: The primary dataset used is the "gld_price_data.csv" file, containing detailed information about each stock price from 2008 until 2018.

Description for each one of the columns:

- Date: The specific date on which the stock prices were recorded.
- SPX: The closing price of the S&P 500 index on the given date.
- GLD: The closing price of the SPDR Gold Shares ETF, which tracks the price of gold.
- USO: The closing price of the United States Oil Fund, which tracks the price of crude oil.
- SLV: The closing price of the iShares Silver Trust ETF, which tracks the price of silver.
- EUR/USD: The exchange rate between the Euro and the US Dollar on the given date.

### Tools

- Google Colaboratory
  - [Access here](https://colab.google/)

### Python Libraries:

- pandas: For data manipulation and analysis.
- numpy: For numerical computations.
- matplotlib: For data visualization.
- seaborn: For statistical data visualization.
- scikit-learn: For machine learning algorithms and evaluation metrics.

### Data Cleaning/Preparation

In the initial data preparation phase, it was performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

### Exploratory Data Analysis

EDA involved exploring the dataset to identify which features are correlated to each other and find out which features are important:

#### Positive Correlation

A positive correlation occurs when two variables move in the same direction. As one variable increases, the other variable also increases, and as one decreases, the other also decreases. The correlation coefficient for a positive correlation is greater than 0 and can go up to 1.

#### Negative Correlation

A negative correlation occurs when two variables move in opposite directions. As one variable increases, the other variable decreases, and vice versa. The correlation coefficient for a negative correlation is less than 0 and can go down to -1.

![image](https://github.com/user-attachments/assets/5671507e-1dbd-4fd0-a4b2-7dee66d3c0c3)


- SPX (S&P 500 Index): 0.049345
The correlation between GLD and SPX is almost negligible (0.049345). This suggests that there is no significant relationship between the movements of gold prices and the S&P 500 index.

- GLD (Gold): 1.000000
This is a self-correlation and, as expected, it is perfect (1.000000). This means that the asset is perfectly correlated with itself.

- USO (United States Oil Fund): -0.186360
The negative correlation (-0.186360) suggests a weak inverse relationship between GLD and USO. When the price of oil goes up, the price of gold tends to slightly decrease, and vice versa, but this relationship is not very strong.

- SLV (Silver): 0.866632
The high positive correlation (0.866632) indicates that gold and silver prices tend to move in the same direction. When the price of silver rises, the price of gold tends to rise as well, and vice versa. This makes sense since both are precious metals and are often influenced by similar economic factors.

- EUR/USD (Euro to US Dollar Exchange Rate): -0.024375
The correlation between GLD and the EUR/USD exchange rate is almost negligible (-0.024375). This suggests that there is no significant relationship between the movements of gold prices and the exchange rate between the Euro and the US Dollar.


### Model Training:

I've selected the Random Forest Regressor due to its robustness and reliability in handling various predictive modeling tasks. The model was trained using the training data that we previously split from the dataset. This step involves fitting the model to the training data, allowing it to learn the underlying patterns and relationships between the input features and the target variable (gold price).


### Model Evaluation

After training the model, I've moved to the evaluation phase, where we assessed the model's performance using the test data. This step is crucial to understand how well the model generalizes to new, unseen data.
Evaluation metrics such as R-squared (R²) score were used to quantify the model’s accuracy and predictive power.

### Results

To evaluate the performance of our Random Forest Regressor model, it was calculated the R-squared error using the r2_score function from the metrics module in scikit-learn. The R-squared error, also known as the coefficient of determination, measures the proportion of the variance in the dependent variable (gold prices) that is predictable from the independent variables (other stock prices). An R-squared value closer to 1 indicates a better fit of the model to the data. For our model, we obtained an R-squared error of 0.9888, which signifies that approximately 98.88% of the variance in the gold prices can be explained by our model. This high R-squared value demonstrates the model’s strong predictive power and accuracy in forecasting gold prices. The below plot demonstrates the comparison between the actual gold price and the predicted gold price:

![image](https://github.com/user-attachments/assets/7e8c98d6-1ddc-4913-9b6b-e23e6c489d43)



### Limitations

I had to create a temporary dataframe with only the numerical columns, because the corr() function can only work with columns that contain numerical values, as shown in the below snapcode for reference:

```python
# creating a temporary dataframe with only the numerical columns
numerical_data = gold_data.select_dtypes(include=['float64', 'int64'])

# calculate the correlation
correlation = numerical_data.corr()

```

### References

- Mastering Positive Correlation Analysis: Tools and Techniques
  - [Access here](https://www.isixsigma.com/dictionary/positive-correlation/)

- Seaborn heatmap | How to make a heatmap in Python Seaborn and adjust the heatmap style
  - [Access here](https://www.youtube.com/watch?v=0U9cs2V-Mqc)

- Random Forest Regression Explained
  - [Access here](https://www.youtube.com/watch?v=X1MRbEnEq2s)

- R Squared Explained
  - [Access here](https://www.youtube.com/watch?v=-7U10N8PvlQ)
