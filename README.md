# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA

## Developed by :S VAISHNAV NANDA
## Register number : 212222240112
## Date:

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on Google stock price data
### ALGORITHM:
Import libraries like pandas, numpy, and matplotlib.

Load the dataset using pandas.

Check for missing values and handle them if necessary.

Apply differencing to remove trends in the data.

Remove seasonality by differencing at the seasonal lag.

Apply log transformation to stabilize variance.

Visualize the data before and after applying each transformation.

Print and plot the results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data = pd.read_csv('Google_Stock_Price_Train.csv')

print("Missing values:\n", data.isnull().sum())

data = data[['Date', 'Close']]  # Select only the Date and Close columns
data.rename(columns={'Close': 'StockPrice'}, inplace=True)

data['StockPrice'] = pd.to_numeric(data['StockPrice'].str.replace(',', ''), errors='coerce')

data['Date'] = pd.to_datetime(data['Date'])

data.set_index('Date', inplace=True)

data['Differenced'] = data['StockPrice'].diff()

data['Seasonal_Differenced'] = data['StockPrice'].diff(12)

data['Log_Transformed'] = np.log(data['StockPrice'])

data.dropna(inplace=True)

plt.figure(figsize=(14, 8))

plt.subplot(3, 2, 1)
plt.plot(data['StockPrice'], label='Original Data')
plt.title('Original Data')
plt.legend()

plt.subplot(3, 2, 2)
plt.plot(data['Differenced'], label='Differenced Data')
plt.title('Regular Differencing')
plt.legend()

plt.subplot(3, 2, 3)
plt.plot(data['Seasonal_Differenced'], label='Seasonal Adjustment')
plt.title('Seasonal Adjustment')
plt.legend()

plt.subplot(3, 2, 4)
plt.plot(data['Log_Transformed'], label='Log Transformed')
plt.title('Log Transformation')
plt.legend()

plt.tight_layout()
plt.show()

print("REGULAR DIFFERENCING:\n", data['Differenced'].head())
print("SEASONAL ADJUSTMENT:\n", data['Seasonal_Differenced'].head())
print("LOG TRANSFORMATION:\n", data['Log_Transformed'].head())
```

### OUTPUT:

![exp21](https://github.com/user-attachments/assets/7d5dbe55-b0f0-4219-be21-483247ea789c)


![ecp22](https://github.com/user-attachments/assets/b2cbaa34-9ea5-4320-850d-334f7320bb44)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
