## Group Members  
- Venkata Purnima PRABHA
- David ROSSIG
- Srishti BINWANI

## Link to the Dataset  
We are using the NASA Turbofan Engine Degradation Simulation Dataset from Kaggle. [NASA Turbofan Engine Degradation Dataset on Kaggle](https://www.kaggle.com/datasets/behrad3d/nasa-cmaps)

The dataset meets the requirements of the project: it is public, has time-series data, and is suitable for anomaly detection based on engine performance over time.

## Use Case
Our project revolves around predictive maintenance of airplane engines. By monitoring the degradation of engine components using time-series sensor data, we aim to predict failures before they happen. This helps decrease downtime, improve safety, and streamline maintenance planning.

## Description of the Dataset
The dataset contains run-to-failure data for multiple aircraft engines, with each engine consisting of a series of time steps during its operational cycles. Sensor readings and operational conditions are recorded at each time step.

The dataset is divided into training and test sets. The training set includes engines that run to failure, while the test set includes engines with truncated life cycles.

Anomalies in the dataset are primarily identified in the final cycles of an engine's life, where the performance declines sharply before failure. Additionally, significant deviations from normal sensor readings are considered anomalies for our usecase.

## Features include:
- Engine ID
- Operational cycle index 
- 3 operational settings
- 21 sensor readings 

## Dataset Statistics
Number of engines: Differs per file (FD001, FD002, etc.)

Total rows in training dataset: train_FD001.txt is ~20,000

Estimated percentage of anomalies: ~10% (as the final cycles prior to failure)

Format: .txt files

## Basic EDA

You can see an introducotry EDA [here](https://github.com/purnimaprabhav/TimeSeriesAnalysis/blob/main/eda.ipynb) on our , precisly on file train_FD001.txt, to get a better idea on the behavior of our data :zap:
