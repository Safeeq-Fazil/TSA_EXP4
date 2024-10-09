## DEVELOPED BY : Safeeq Fazil A
## REGISTER NO: 212222240086

# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
# Date: 



### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.
### PROGRAM:
```py

import pandas as pd
from matplotlib import pyplot as plt
from pandas.plotting import autocorrelation_plot
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
from statsmodels.tsa.arima.model import ARIMA
import numpy as np
import warnings
warnings.filterwarnings('ignore')

# Load your Vegetable Price data
vegetable_price_data = pd.read_csv('vegetable.csv')

# Convert 'Date' column to datetime and set it as the index
vegetable_price_data['Date'] = pd.to_datetime(vegetable_price_data['Date'])
vegetable_price_data.set_index('Date', inplace=True)

# Resample the 'Chennai' column by day to get daily price
daily_price = vegetable_price_data['Commodity'].resample('D').sum()

# Simulating an ARMA(1,1) Process
ar1 = np.array([1, 0.33])
ma1 = np.array([1, 0.9])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=1000)
plt.plot(ARMA_1)
plt.title('Simulated ARMA(1,1) Process')
plt.xlim([0, 200])
plt.show()
plot_acf(ARMA_1)
plot_pacf(ARMA_1)
plt.show()

# Simulating an ARMA(2,2) Process
ar2 = np.array([1, 0.33, 0.5])
ma2 = np.array([1, 0.9, 0.3])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=1000)
plt.plot(ARMA_2)
plt.title('Simulated ARMA(2,2) Process')
plt.xlim([0, 200])
plt.show()
plot_acf(ARMA_2)
plot_pacf(ARMA_2)
plt.show()
```

# OUTPUT:
## SIMULATED ARMA(1,1) PROCESS:
![image](https://github.com/user-attachments/assets/ed2df6cf-c259-4394-a738-171d4c4f3d04)


## Partial Autocorrelation:
![image](https://github.com/user-attachments/assets/3a491ea5-a0e3-4670-8649-1444b8356a27)


## Autocorrelation:
![image](https://github.com/user-attachments/assets/9061b4c4-ce12-4f31-8379-dd8775f4e78d)



## SIMULATED ARMA(2,2) PROCESS:
![image](https://github.com/user-attachments/assets/0c2a4d15-d26b-4870-abda-54cba49f73e6)


## Partial Autocorrelation:
![image](https://github.com/user-attachments/assets/fa337a37-d2f9-4809-a45a-0ab45b3c669a)


## Autocorrelation:


## RESULT:
Thus, a python program is created to fit ARMA Model for Time Series successfully.
