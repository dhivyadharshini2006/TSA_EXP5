# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 7/10/25


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv("gold_price_data.csv")

print("FIRST FIVE ROWS:")
print(data.head())

data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)

sales = data['Value'].dropna()

decomposition = seasonal_decompose(sales, model='additive', period=12)

plt.figure(figsize=(10,12))

plt.subplot(411)
plt.plot(sales, label='Original Sales')
plt.legend(loc='upper left')
plt.title('Original Sales Data')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()

plt.figure(figsize=(10,5))
plt.plot(sales, label='Original Sales')
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend()
plt.title('Overall Sales Time Series Representation')
plt.show()

```





# OUTPUT:
### FIRST FIVE ROWS:
<img width="233" height="155" alt="image" src="https://github.com/user-attachments/assets/df3b3d66-34ab-42aa-9d68-b4e4df972196" />



### PLOTTING THE DATA:
<img width="747" height="232" alt="image" src="https://github.com/user-attachments/assets/0411fd88-f25c-4a29-8d62-c974fd38baf4" />


### SEASONAL PLOT REPRESENTATION :
<img width="744" height="221" alt="image" src="https://github.com/user-attachments/assets/bed6f67c-7b11-4c57-9a22-e3544ee26d63" />



### TREND PLOT REPRESENTATION :
<img width="737" height="230" alt="image" src="https://github.com/user-attachments/assets/a26c0981-92bd-4685-96fa-fb75be2ad794" />



### OVERAL REPRESENTATION:

<img width="746" height="390" alt="image" src="https://github.com/user-attachments/assets/8dbe2b10-33c8-4541-8a3d-578c820698fe" />


# RESULT:
Thus we have created the python code for the time series analysis and decomposition.
