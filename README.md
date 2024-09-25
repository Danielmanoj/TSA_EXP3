## Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.


### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.

   
### PROGRAM:
```
DEVELOPED BY : MANOJ G
REG NO. : 212222240060
```
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = '/mnt/data/astrobiological_activity_monitoring.csv'
data = pd.read_csv(file_path)

# Extract the 'Atmospheric_Composition_O2' column
o2_composition = data['Atmospheric_Composition_O2'].dropna()

# Mean
data_mean = np.mean(o2_composition)

# Variance
data_var = np.var(o2_composition)

# Normalized data
normalized_data = (o2_composition - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF for the first 35 lags
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) for Atmospheric Composition O2')
plt.show()

```


### OUTPUT:

![image](https://github.com/user-attachments/assets/1c36d0f4-06e9-4ed5-a9e6-4b7a07c8f03a)




### RESULT:
Thus the  auto correlation function in python is successfully implemented.
