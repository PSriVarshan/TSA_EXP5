### Developed By : Sri Varshan P
### Reg. NO . 212222240104
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:


```py

# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset
  # Replace with the correct path to your file
df = pd.read_csv('russia_losses_equipment.csv')

# Display the first 5 rows of the dataset
print("First 5 Rows of the dataset:")
print(df.head())

# Converting the 'date' column to datetime and setting it as the index
df['date'] = pd.to_datetime(df['date'], format='%Y-%m-%d')
df.set_index('date', inplace=True)

# Filling missing values for the "tank" column (if any) using forward fill
df['tank'] = df['tank'].fillna(method='ffill')

# Performing seasonal decomposition on the "tank" feature (additive model)
decomposition = seasonal_decompose(df['tank'], model='additive', period=7)

# Plot and save each component separately with different colors

# Plot and save the observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='blue')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_plot.png')
plt.show()

# Plot and save the trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='green')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_plot.png')
plt.show()

# Plot and save the seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='red')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_plot.png')
plt.show()

# Plot and save the residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_plot.png')
plt.show()

```


### OUTPUT:

#### FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/66588b8c-5174-4b6d-ad3d-0302644bca98)






#### SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/21b4a878-3a20-4f97-bd0d-df39f4e8114f)


#### TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/2617e006-512e-4635-ac12-0728eb89e01f)


#### PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/361a199c-380f-4d95-ac10-3b497150ac39)


#### OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/14e6d636-6fbb-4d22-b51f-4e612844020b)



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
