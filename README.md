### Development by: Ganesh R
### Register no: 212222240029
### Date:
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

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
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the CSV file
file_path = '/content/Amazon.csv'
data = pd.read_csv(file_path)

# Extract the 'Volume' data
Volume_data = data['Volume'].dropna().values

# Mean
data_mean = np.mean(Volume_data)
print("Mean:", data_mean)

# Variance
data_var = np.var(Volume_data)
print("Variance:", data_var)

# Normalized data
normalized_data = (Volume_data - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) of pH level')
plt.show()

```

### OUTPUT:
![image](https://github.com/user-attachments/assets/4ff72c6c-d7dd-45ac-bc73-f36c36f6e2ac)
![image](https://github.com/user-attachments/assets/8e516330-b8ac-4a2a-9600-320e6eb72bbc)


### RESULT:
Implementation of auto correlation function in python was successfully completed .
