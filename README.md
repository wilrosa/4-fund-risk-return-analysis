# Analyzing Portfolio Risk and Return

This repo contains the results of the module 4 challenge. I assumed the role of a quantitative analyst for a FinTech investing platform. This platform aims to offer clients a one-stop online investment solution for their retirement portfolios. I've evaluated four new investment options for inclusion in the client portfolios. Legendary fund and hedge-fund managers run all four selections. These fund managers are also referred to as "whales" because of the large amount of money that they manage. I analyzed each portfolio to determine the funds with the most investment potential based on key risk-management metrics: (1) daily returns, (2) standard deviations, (3) Sharpe ratios, and (4) betas.

I created a Jupyter notebook that contains  data preparation, analysis, and visualizations for key risk and return metrics. A CSV file was imported and daily returns DataFrame was prepared for analysis. My quantitative analysis included performance, volatility, risk, risk-return profile, and portfolio diversification. Specifically, it contains the following: (1) A single DataFrame imported from a CSV file that has a DateTimeIndex, (2) A risk analysis of the assets that the DataFrame contains vs. the S&P 500, and (3) Risk-return metrics, including the daily returns, standard deviation, Sharpe ratio, and beta.

---

## Technologies

This project leverages python 3.7 with the following packages:

* [pandas](https://github.com/pandas-dev/pandas) - For manipulating data

* [matplotlib](https://github.com/matplotlib/matplotlib) - For creating static, animated, and interactive visualizations

* [numpy](https://github.com/numpy/numpy) - For scientific computing with Python

---

## Installation Guide

Using the Pandas read_csv function and the Path module, import the data from the `whale_navs.csv` containing the data about portfolios with net asset value (NAV) pricing from four whale investors. The file also contains data about the S&P 500 index, which will serve as the benchmark for your analysis.

Use the read_csv function and the Path module to read the `whale_navs.csv` file into a Pandas DataFrame. Be sure to create a DateTimeIndex. Review the first five rows of the DataFrame by using the head function.

Use the Pandas pct_change function together with dropna to create the daily returns DataFrame. Base this DataFrame on the NAV prices of the four portfolios and on the closing price of the S&P 500 Index. Review the first five rows of the daily returns DataFrame.

```python
  from pathlib import Path
    
    whale_data = Path("../Resources/whale_navs.csv")
    whale_df = pd.read_csv(whale_data, index_col="date", infer_datetime_format=True, parse_dates=True)
    
    whale_daily_returns = whale_df.pct_change().dropna()

    whale_daily_returns.head()
```
---

## **Analyze the Performance**

Based on the analysis in this section, we answer the question: 

(1) Do any of the four fund portfolios outperform the S&P 500 Index?

```python
whale_cumulative_returns.plot(figsize=(15,7), title="Fund NAV & S&P 500 Cumulative Returns")
```

* ![Fund NAV & S&P 500 Cumulative Returns](/Screenshots/Fund_NAV_S&P_500_Cumulative_Returns.png) 


## **Analyze the Volatility**

Here, we answer the question: 

(2) Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?

```python
fund_daily_returns.plot(kind='box', title="Fund NAV Daily Returns",rot=45)
```

* ![Fund NAV Daily Returns](/Screenshots/Fund_NAV_Daily_Returns.png)


## **Analyze the Risk**

In this section, we answer the following three questions: 

(3) Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

(4) Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

(5) Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

```python
whale_std_21.plot(figsize=(10,7), title="Fund NAV and S&P 500 21 Day Standard Deviation")
```

* ![Fund NAV and S&P 500 21 Day Standard Deviation](/Screenshots/Fund_NAV_and_S&P_500_21_Day_Standard_Deviation.png)

```python
fund_std_21.plot(figsize=(10,7), title="Fund NAV 21 Day Standard Deviation")
```

* ![Fund NAV 21 Day Standard Deviation](/Screenshots/Fund_NAV_21_Day_Standard_Deviation.png)

## **Analyze the Risk-Return Profile**

Here, we answer the question: 

(6) Which of the four portfolios offers the best risk-return profile? Which offers the worst?

```python
whale_sharpe_ratios.plot.bar(figsize=(10, 7), title="Fund NAV and S&P 500 Sharpe Ratios")
```

## **Diversify the Portfolio**

In this final section, I evaluated how two portfolios react relative to the broader market. I choose two portfolios that I would most likely to recommend as investment option and answer the following questions: 

(7) Which of the two portfolios seem more sensitive to movements in the S&P 500?

```python
bh_rolling_60_beta.plot(figsize=(10,7), title="BERKSHIRE HATHAWAY INC - 60 Day Rolling Beta")
```

* ![BERKSHIRE HATHAWAY INC - 60 Day Rolling Beta](/Screenshots/BERKSHIRE_HATHAWAY_INC-60_Day_Rolling_Beta.png)

(8) Which of the two portfolios do you recommend for inclusion in your firm’s suite of fund offerings?

```python
tg_rolling_60_beta.plot(figsize=(10,7), title="TIGER GLOBAL MANAGEMENT LLC - 60 Day Rolling Beta")
```

* ![TIGER GLOBAL MANAGEMENT LLC - 60 Day Rolling Beta](/Screenshots/TIGER_GLOBAL_MANAGEMENT_LLC.png)

---
## Contributors

Brought to you by Wilson Rosa. https://www.linkedin.com/in/wilson-rosa-angeles/.

---
## License

MIT
