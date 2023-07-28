

## Augmented Dickey-Fuller (ADF) Test

The ADF test belongs to a category of tests called **‘Unit Root Test’**, which is the proper method for testing the stationarity of a time series. A unit root is a characteristic of non-stationary time series, indicating that the data has a stochastic trend and its statistical properties are not constant over time. It is an extension of the simpler Dickey-Fuller test and is designed to handle more complex time series data with potential autocorrelation.

##### Let's Understand this step by step:

1. **The Null and Alternative Hypotheses:**

- **Null Hypothesis (H<sub>0</sub>):** The time series has a unit root, making it non-stationary (stochastic trend).
- **Alternative Hypothesis (H<sub>1</sub>):** The time series is stationary and doesn't have a unit root.

2. **The ADF Test Equation:**
The ADF test uses the following equation to check for the presence of a unit root

<span style="font-size:24px">ΔYt​=α+βt+γ Y<sub>t−1​</sub>+δ<sub>1</sub> ​ΔY<sub>t−1</sub>​+δ<sub>2</sub>​ ΔY<sub>t−2</sub>​+…+δ<sub>p</sub> ​ΔY<sub>t−p</sub>​+ε<sub>t</sub>​</span>

Where:

- ΔYt​ is the differenced series at time *t*.
- α is a constant term.
- β represents the coefficient of time trend (t) if there is a deterministic trend present.
- γ is the coefficient of the lagged level of the time series.
- δ<sub>1</sub>,δ<sub>2</sub>,…,δ<sub>p</sub>​ are the coefficients of the lagged differences.
- εt​ is the error term or residual.

This part isn't necessary to go too deep into since this tests equation is mostly calculated using pre-built packages like [`statsmodel`](https://www.statsmodels.org/stable/index.html) in python.

This is a example of the output `statsmodel` provides after calculation:

```python
ADF Statistic: 3.1451856893067296
n_lags: 1.0
p-value: 1.0
Critial Values:
   1%, -3.465620397124192
Critial Values:
   5%, -2.8770397560752436
Critial Values:
   10%, -2.5750324547306476
```


3. **Interpretation:**

The ADF test calculates a test statistic based on the above equation and compares it to critical values obtained from statistical tables or bootstrapping.

- If the test statistic is greater than the critical value, we cannot reject the null hypothesis (H<sub>0</sub>), and the series is likely non-stationary (presence of a unit root).
- If the test statistic is smaller than the critical value, we reject the null hypothesis (H<sub>0</sub>), and the series is likely stationary (no unit root).

4. **P-Value:**

The p-value represents the probability of obtaining a test statistic as extreme as the one calculated if the null hypothesis is true (H<sub>0</sub> is correct). In other words, it indicates the likelihood that the time series has a unit root and is non-stationary.

- If the p-value is below a pre-defined significance level (commonly set at 0.05), we reject the null hypothesis and consider the series stationary.
- If the p-value is above the significance level, we cannot reject the null hypothesis, and the series is likely non-stationary.

5. **Above Code's Explanation:**

To remind ourselves again, the code goes like this:
```python
ADF Statistic: 3.1451856893067296
n_lags: 1.0
p-value: 1.0
Critial Values:
   1%, -3.465620397124192
Critial Values:
   5%, -2.8770397560752436
Critial Values:
   10%, -2.5750324547306476
```
The ADF test statistic is 3.1451856893067296. To determine whether the time series is stationary or not, we need to compare this value with the critical values at different significance levels (1%, 5%, and 10%).

1. At the 1% significance level:
    - Critical Value: -3.465620397124192

Since the ADF statistic (3.1451856893067296) is greater than the critical value (-3.465620397124192) at the 1% level, we cannot reject the null hypothesis (H<sub>0</sub>). This suggests that the time series may have a unit root, and it is likely non-stationary at the 1% significance level.

2. At the 5% significance level:
    - Critical Value: -2.8770397560752436

The ADF statistic (3.1451856893067296) is still greater than the critical value (-2.8770397560752436) at the 5% level. Therefore, we still cannot reject the null hypothesis (H<sub>0</sub>) at the 5% significance level, indicating that the time series may have a unit root and is likely non-stationary at the 5% significance level.

3. At the 10% significance level:
    - Critical Value: -2.5750324547306476

Even at the 10% significance level, the ADF statistic (3.1451856893067296) is higher than the critical value (-2.5750324547306476). Thus, we cannot reject the null hypothesis (H<sub>0</sub>) at the 10% significance level either. This further suggests that the time series may have a unit root and is likely non-stationary at the 10% significance level.

**Based on the ADF test results, we find that the ADF statistic is greater than the critical values at all significance levels (1%, 5%, and 10%). This indicates that we cannot reject the null hypothesis of the presence of a unit root. Therefore, the time series is likely non-stationary, and it may exhibit a stochastic trend or other non-constant statistical properties over time.**


---

## Kwiatkowski-Phillips-Schmidt-Shin (KPSS) Test

The KPSS test is another hypothesis test used to assess the stationarity of a time series, complementing the Augmented Dickey-Fuller (ADF) test. While the ADF test checks for the presence of a unit root and a stochastic trend, the KPSS test focuses on testing the null hypothesis that the time series is stationary around a deterministic trend.

1. **Null and Alternative Hypotheses:**

- **Null Hypothesis (H<sub>0</sub>):** The time series is stationary around a deterministic trend.
- **Alternative Hypothesis (H<sub>1</sub>):** The time series is non-stationary and does not have a deterministic trend.


	*Note: The equation is not the concern here as we can find packages that calculates for us.*

2. **How the KPSS Test Works:**

The KPSS test assumes that the trend in the time series can be represented by a deterministic function, like a straight line or a known pattern, and there are no random fluctuations around this trend. It calculates a test statistic, and its p-value is used to determine the stationarity of the time series:

- If the p-value is above a predetermined significance level (commonly set at 0.05), we fail to reject the null hypothesis. This suggests that the time series is stationary around a deterministic trend.

- If the p-value is below the significance level, we reject the null hypothesis in favor of the alternative hypothesis. This indicates that the time series is likely non-stationary and does not have a deterministic trend.

3. **Interpretation of Results:**

- A high p-value indicates that the time series is likely stationary around a deterministic trend.

- A low p-value suggests that the time series is non-stationary and lacks a deterministic trend.

<span style="font-size:15px; font-style: italic;">Basically a complete opposite logic than that of ADF test</span>

4. **Example of KPSS Test Output:**

For instance, after performing the KPSS test on a time series, you might get the following results:

```python
KPSS Statistic: 0.123456789
p-value: 0.0123456789
Critical Values:
   10% level: 0.23456789
   5% level: 0.3456789
   2.5% level: 0.456789
   1% level: 0.56789
```

In this example, the KPSS test statistic is 0.123456789, and the p-value is 0.0123456789. The p-value is less than the significance level of 0.05 (commonly used), indicating that we reject the null hypothesis (H<sub>0</sub>) of stationarity around a deterministic trend. Therefore, the time series is likely non-stationary and lacks a deterministic trend.


## ADF and KPSS tests as one


**Complementing Each Other:** By using both the ADF and KPSS tests together, you can gain a more comprehensive understanding of the stationarity properties of the time series. Here's how they complement each other:

1. **Identifying Stochastic vs. Deterministic Trends:**
    
    - ADF: The ADF test helps identify whether the time series has a stochastic trend, indicating non-stationarity due to random fluctuations.
    - KPSS: The KPSS test helps identify whether the time series has a deterministic trend, suggesting non-stationarity around a known pattern.
    
2. **When to Use Each Test:**
    
    - ADF: Use the ADF test when you suspect a stochastic trend or want to detect the presence of a unit root.
    - KPSS: Use the KPSS test when you suspect a deterministic trend or want to explore stationarity around a deterministic pattern.
    
3. **Comprehensive Analysis:**
    
    - If both tests indicate stationarity, it strengthens the evidence that the time series is indeed stationary.
    - If both tests indicate non-stationarity, it suggests a clear indication of non-stationarity in the time series.
    - If the ADF test indicates non-stationarity (presence of a unit root), while the KPSS test suggests stationarity around a deterministic trend, it implies the presence of a complex behavior with a combination of stochastic and deterministic components.

By combining the results of both tests, analysts can make more informed decisions about the appropriate time series modeling techniques and transformations needed to prepare the data for accurate forecasting and analysis. It helps in selecting appropriate models and understanding the underlying patterns and trends present in the time series data.