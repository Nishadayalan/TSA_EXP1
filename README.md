# Ex.No: 01A PLOT A TIME SERIES DATA
###  Date: 12-08-2025

# AIM:
To Develop a python program to Plot a time series data (population/ market price of a commodity
/temperature.
# ALGORITHM:
1. Import the required packages like pandas and matplot
2. Read the dataset using the pandas
3. Calculate the mean for the respective column.
4. Plot the data according to need and can be altered monthly, or yearly.
5. Display the graph.
# PROGRAM:
```
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
import pandas as pd
```
```
df = pd.read_csv("/content/plane_crash.csv")
```
```
df.head(5)
```
```
df.tail(5)
```
```
for col in df.columns:
    if df[col].dtype in ['float64', 'int64']:
        df[col] = df[col].fillna(df[col].median())
    else:
        df[col] = df[col].fillna("Unknown")
```
```
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')
```
```
df = df.sort_values(by='Date')
```
```
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')
df['Year'] = df['Date'].dt.year

# Group by year and sum fatalities
yearly_fatalities = df.groupby('Year')['Fatalities'].sum()

# Plot
plt.figure(figsize=(10, 6))
sns.lineplot(x=yearly_fatalities.index, y=yearly_fatalities.values, color='black')
plt.title("Fatalities per Year", fontsize=14)
plt.xlabel("Year")
plt.ylabel("Number of Fatalities")
plt.show()
```

# OUTPUT:

<img width="1748" height="360" alt="image" src="https://github.com/user-attachments/assets/e0a6f3a5-0ac3-46bf-920d-3c3cbe9438b5" />






<img width="1747" height="420" alt="image" src="https://github.com/user-attachments/assets/b5531e07-481c-43cd-a01c-542af7e3ef07" />






<img width="937" height="615" alt="image" src="https://github.com/user-attachments/assets/6fc33fdf-ba61-4333-b7c2-ba838f6f4a3d" />







# RESULT:
Thus we have created the python code for plotting the time series of given data.
