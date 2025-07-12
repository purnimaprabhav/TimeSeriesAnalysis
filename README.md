## Group Members  
- Venkata Purnima PRABHA
- David ROSSIG
- Srishti BINWANI

## Link to the Dataset  
We are using the Pump Sensor Data dataset from Kaggle. [Pump Sensor Data Dataset on Kaggle](https://www.kaggle.com/datasets/nphantawee/pump-sensor-data)

The dataset meets the requirements of the project: it is public, has time-series data, and is suitable for anomaly detection based on pump performance over time.

## Use Case
Our project focuses on predictive maintenance of industrial pumps. By monitoring the sensor data from pumps over time, we aim to detect anomalies and predict potential failures before they occur. This helps in reducing maintenance costs, preventing unexpected downtime, and optimizing pump performance.

## Description of the Dataset
The dataset contains time-series sensor data from multiple industrial pumps, with readings taken at regular intervals. The data includes various sensor measurements that indicate the operational status and health of the pumps.

The dataset includes both normal operation data and instances where anomalies or failures occurred, making it suitable for anomaly detection and predictive maintenance applications.

For our analysis, we have selected three specific sensors (sensors 10, 36, and 48) as they exhibit different distributions and characteristics, making them particularly interesting for anomaly detection and pattern analysis.

## Features include:
- Timestamp
- Sensor readings (multiple sensors)
- Machine status
- Various operational parameters

## Dataset Statistics
- Time period: Continuous monitoring data
- Number of sensors: Multiple sensor readings
- Selected sensors for analysis: Sensors 10, 36, and 48 (chosen for their distinct distribution patterns)
- Format: CSV file
- Contains both normal and anomalous conditions

## Anomaly Detection Methods

This project implements three distinct anomaly detection approaches for time series data:

### 1. STL Decomposition Method

**File:** `STL_decomposition_Method.ipynb`

**Method Overview:**
STL (Seasonal-Trend decomposition using Loess) is a powerful method for decomposing a time series into three distinct components:
- **Trend:** The long-term progression or movement in the data
- **Seasonality:** Regular, repeating patterns or cycles in the data
- **Residual (Remainder):** The part of the data that remains after removing trend and seasonality

**Anomaly Detection Process:**
1. **Decomposition:** Apply STL decomposition to separate the time series into trend, seasonal, and residual components
2. **Residual Analysis:** Focus on the residual component where anomalies are most visible
3. **Threshold-based Detection:** Use a statistical threshold method:
   - Calculate mean and standard deviation of residuals
   - Set threshold = mean + (3 × standard deviation)
   - Flag points exceeding this threshold as anomalies

**Advantages:**
- Robust and flexible, handling any type of seasonality
- Uses LOESS smoothing for smooth trend and seasonal components
- Effectively isolates anomalies in the residual component
- Provides clear visualization of different data components

**Implementation Details:**
- Applied to individual sensors (10, 36, 48) separately
- Uses 3-sigma rule for anomaly threshold
- Provides visual plots showing original data, components, and detected anomalies

### 2. MAD-Naive Method

**File:** `STL_decomposition_Method.ipynb` (or a similar notebook)

**Method Overview:**
The MAD-naive (Median Absolute Deviation) method is a robust statistical approach for anomaly detection. Unlike the mean and standard deviation, MAD uses the median and the median of absolute deviations, making it less sensitive to outliers and non-normal data distributions.

**Anomaly Detection Process:**
1. **Obtain Residuals:** Use the residual component from STL decomposition (or raw data for a naive approach).
2. **Calculate Median and MAD:**
   - Compute the median of the residuals.
   - Compute the MAD: the median of the absolute deviations from the median.
3. **Threshold-based Detection:**
   - Set a threshold, e.g., median + (k × MAD), where k is typically 3.
   - Flag points whose absolute deviation from the median exceeds this threshold as anomalies.

**Advantages:**
- **Robust to Outliers:** MAD is not affected by extreme values, making it more reliable for skewed or heavy-tailed data.
- **Simple and Interpretable:** Easy to implement and understand.
- **No Assumption of Normality:** Works well even if the residuals are not normally distributed.

**Implementation Details:**
- Can be applied to STL residuals or directly to raw sensor data (naive approach).
- The threshold multiplier (k) can be tuned for sensitivity.
- Provides a more robust alternative to mean-std thresholding, especially for data with outliers.

**Comparison to Mean-Std:**
- Mean-std is sensitive to outliers and assumes normality; MAD is robust and non-parametric.
- MAD may detect anomalies that mean-std misses, especially in non-Gaussian data.

### 3. VAR (Vector Autoregression) Model Method

**File:** `var_model.ipynb`

**Method Overview:**
Vector Autoregression (VAR) is a multivariate time series model that captures the linear interdependencies among multiple time series variables. It models each variable as a linear function of past values of all variables in the system.

**Anomaly Detection Process:**
1. **Model Training:** Fit a VAR model using normal operation data (excluding known anomaly periods)
2. **Forecasting:** Use the trained model to forecast expected values for all time points
3. **Residual Calculation:** Compute residuals by subtracting forecasted values from actual observations
4. **Anomaly Scoring:** Calculate anomaly scores using squared residuals summed across all sensors
5. **Threshold-based Detection:** Flag anomalies using threshold = mean + standard deviation of anomaly scores

**Key Parameters:**
- **Lag Order:** Determined automatically using model selection criteria (typically around 10 lags)
- **Multivariate Analysis:** Considers relationships between multiple sensors simultaneously
- **Anomaly Score:** Sum of squared residuals across all sensors for each time point

**Advantages:**
- Captures interdependencies between multiple sensors
- Provides a unified anomaly score for the entire system
- Can detect anomalies that manifest as unusual relationships between sensors
- More robust than univariate methods for complex systems

**Implementation Details:**
- Uses all three selected sensors (10, 36, 48) simultaneously
- Trains on normal operation data only
- Provides confusion matrix and performance metrics (precision, recall, F1-score)
- Includes visualization of anomaly scores and detection results

## Performance Comparison

Both methods offer different strengths:

- **STL Decomposition:** Better for understanding individual sensor behavior and detecting sensor-specific anomalies
- **VAR Model:** Better for detecting system-wide anomalies and capturing sensor interdependencies

The choice between methods depends on the specific requirements:
- Use STL for detailed analysis of individual sensor patterns
- Use VAR for system-level anomaly detection and predictive maintenance

## Basic EDA

You can see an introductory EDA in our [Pump_Sensor_Data_EDA.ipynb](https://github.com/purnimaprabhav/TimeSeriesAnalysis/blob/main/Pump_Sensor_Data_EDA.ipynb) notebook to get a better understanding of the data patterns and characteristics

## Requirements

The project requires the following Python packages (see `requirements.txt`):
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels (for STL and VAR)
- scikit-learn (for performance metrics)
