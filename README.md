### Developed By:Gowrisankar P
### Register no:212222230041
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### AIM:
To Illustrates how to perform time series analysis and decomposition on the MentalHealthSurvey of the student.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```

import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.dates as mdates

file_path = 'MentalHealthSurvey.csv'
data = pd.read_csv(file_path)
print(data.head())

data_length = len(data)
data['Date'] = pd.date_range(start='2020-01-01', periods=data_length, freq='M')

data.set_index('Date', inplace=True)

monthly_data = data['depression'].resample('M').mean()

decomposition = seasonal_decompose(monthly_data, model='multiplicative', period=12)

fig = decomposition.plot()

for ax in fig.axes:
    
    ax.xaxis.set_major_locator(mdates.YearLocator())  
    ax.xaxis.set_major_formatter(mdates.DateFormatter('%Y')) 

   
    ax.tick_params(axis='x', rotation=45)  


plt.rc('axes', titlesize=14)   
plt.rc('axes', labelsize=12)   
plt.rc('xtick', labelsize=10)  
plt.rc('ytick', labelsize=10)  
plt.rc('legend', fontsize=12)  

plt.tight_layout()
plt.show()

```
### OUTPUT:
FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/f30f6b64-a53a-44e5-825d-d58d1cddd1c3)

PLOTTING THE DATA:
![image](https://github.com/user-attachments/assets/32911e54-a769-4389-94d3-bacc4c6fd12d)

SEASONAL PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/f2950ddf-8333-446d-89bb-2a69d6cd5fdc)

TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/2eb24eb1-2e5e-494b-85a4-9119e5f14402)

OVERAL REPRESENTATION:
![image](https://github.com/user-attachments/assets/3aab616a-1fb7-4a12-8b1e-cad1de953df1)

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
