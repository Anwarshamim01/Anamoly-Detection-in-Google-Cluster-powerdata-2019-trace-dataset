# Anamoly-Detection-in-Google-Cluster-powerdata-2019-trace-dataset
I applied time series transformer and lstm for anamolyh detection in Google Cluster powerdata-2019 trace dataset
### **Introduction**

This project focused on analyzing power utilization data from May 2019 to detect anomalies in the power consumption of machines connected to power distribution units (PDUs). Both Long Short-Term Memory (LSTM) autoencoders and Transformer-based models were used for anomaly detection.

### **Data Preprocessing & Feature Engineering**

Key features used for both single- and multi-feature models:
- `measured_power_util`: Main feature representing power utilization.
- **Additional features for multi-feature models**:
  - Lags (`measured_power_util_lag_1`, etc.)
  - Rolling statistics (mean and standard deviation)
  - Temporal features (hour, day_of_week)

Preprocessing included timestamp alignment, aggregation at 5-minute intervals, and handling missing data.

### **Modeling with LSTM and Transformer**

Both LSTM autoencoders and Transformer models had similar structures in single- and multi-feature setups:
- **Single-Feature Models**: Used only `measured_power_util`.
- **Multi-Feature Models**: Included lags, rolling statistics, and temporal information.

**LSTM Model**: Consisted of two stacked LSTM layers for sequence reconstruction.  
**Transformer Model**: Used positional encoding and a Transformer encoder to model sequential dependencies.

### **Anomaly Detection and Results**

Reconstruction error was used to detect anomalies, with a threshold based on the mean reconstruction error plus three standard deviations. Both models improved significantly with multi-features:

| Model              | Single-Feature Performance           | Multi-Feature Performance               |
|--------------------|--------------------------------------|-----------------------------------------|
| **LSTM Autoencoder**| Good anomaly detection               | MSE was not converging |
| **Transformer**     | Strong performance                   | MSE was not converging |
| **CLassical Models**     | Confused anamolies and outliers  |  |
