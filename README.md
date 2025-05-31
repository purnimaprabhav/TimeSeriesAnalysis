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

## Basic EDA

You can see an introductory EDA in our [Pump_Sensor_Data_EDA.ipynb](https://github.com/purnimaprabhav/TimeSeriesAnalysis/blob/main/Pump_Sensor_Data_EDA.ipynb) notebook to get a better understanding of the data patterns and characteristics
