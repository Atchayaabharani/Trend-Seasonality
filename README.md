# Imports:

matplotlib.pyplot is imported as plt for plotting graphs.

pandas is imported as pd for loading and handling datasets (CSV files in this case).
# Loading the Data:

The pd.read_csv() function reads the sales data from a CSV file located at the provided path.

y stores the 'Unit Price' column, which is a time series representing unit prices over time.
This code will generate a plot with three subplots:
# Estimating Trend:
estimate_trend() calculates the moving average trend for the time series y.
## Inputs:
y: the time series data (unit prices).

d: the window size for calculating the moving average (the number of data points considered in each calculation).
## Steps:
n is the length of the time series.

The trend list is initialized with zeros.

The function loops through each time point (t) and calculates the average over a window of d data points.

If d is odd, the window is centered on t. If d is even, the window is slightly shifted.

sum_y is the sum of values in the selected window, and count is used to make sure the window doesn't exceed the bounds of the data.

For each time point t, the trend value is the average of the data within the window, stored in trend[t].

Output: The function returns the trend values as a list.

# Estimating Seasonality:
estimate_seasonality() computes the seasonality component by dividing the actual data point by its corresponding trend value.

## Inputs:
y: the original time series data.

d: the window size (not used directly in this function).

trend: the trend component previously computed.
## Steps:
n is the length of the time series.

The seasonality list is initialized with zeros.

For each time point t, the seasonality is calculated by dividing the original data value (y[t]) by its corresponding trend value (trend[t]).

Output: The function returns the seasonality values as a list.

# Window Size Decision:
This block determines the value of d (the window size for the moving average).

If the length of the time series y is even, d is set to 3.

If the length of the time series is odd, d is set to 4.

# Calling the Functions:
The estimate_trend() function is called with the time series y and window size d, and the result is stored in trend.

The estimate_seasonality() function is then called with y, d, and the previously computed trend, and the result is stored in seasonality.

# Plotting the Results:
plt.figure(figsize=(10, 6)): Creates a figure of size 10x6 inches.

The plt.subplot(3, 1, i) creates a 3-row plot:

The first subplot shows the original time series y.

The second subplot shows the trend component calculated by estimate_trend().

The third subplot shows the seasonality component calculated by estimate_seasonality().

plt.legend() adds a legend to each subplot.

plt.tight_layout() adjusts the subplots to fit neatly within the figure.

plt.show() displays the plots.
