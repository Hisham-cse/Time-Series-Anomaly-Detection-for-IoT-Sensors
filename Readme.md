# Time Series Anomaly Detection for IoT Sensors

## Overview
In manufacturing systems, IoT sensors continuously monitor equipment health.  
Unexpected sensor behavior can indicate hardware faults, performance degradation, or the need for maintenance.

This project focuses on building an **end-to-end anomaly detection pipeline** for time-series IoT sensor data using **unsupervised machine learning techniques**.  
The goal is to identify abnormal sensor readings without relying on labeled anomaly data.

---

## Project Approach
The solution follows a practical machine learning workflow:

- Generate realistic time-series sensor data
- Perform exploratory data analysis (EDA)
- Engineer features to capture local patterns
- Apply two different anomaly detection approaches
- Compare results through visual inspection and reasoning

Since labeled anomalies are not available, evaluation is based on pattern alignment and consistency across models.

---

## Project Structure
```bash
IoT_Time_Series_Anomaly_Detection.ipynb
README.md
```

All steps are implemented in a single notebook to keep the workflow easy to follow and review.

---

## Dataset Description
Synthetic IoT sensor data was generated to simulate real-world behavior.

**Normal behavior**
- Smooth sinusoidal pattern
- Small random noise

**Injected anomalies**
- Sudden spikes (sensor glitches)
- Sudden drops (power or communication issues)
- Gradual drift (equipment degradation over time)
- Sudden reset after drift (maintenance or recalibration)

This setup makes it easier to validate anomaly detection techniques without ground-truth labels.

---

## Data Preparation and Exploration
- Visualized raw sensor readings over time
- Introduced missing values to simulate sensor communication failures
- Handled missing values using forward-fill and backward-fill
- Identified abnormal patterns through time-series plots

---

## Feature Engineering
To improve anomaly detection, the following features were created:

- Rolling mean (local trend)
- Rolling standard deviation (local variability)
- Difference between consecutive readings
- Deviation from rolling mean

All features were scaled using standard normalization to ensure fair model behavior.

---

## Anomaly Detection Models

### Isolation Forest
Isolation Forest was used as a statistical, unsupervised method.

- Effective at detecting sudden spikes and drops
- Struggles with gradual drift, as individual drift points are not rare

### Autoencoder
A lightweight dense autoencoder was implemented using TensorFlow.

- Learns normal sensor behavior through reconstruction
- Uses reconstruction error to detect anomalies
- Performs better on gradual drift and contextual anomalies
- Introduces some false positives due to higher sensitivity

---

## Model Evaluation
Because labeled anomaly data is unavailable, traditional metrics such as accuracy and F1-score were not directly used.

Evaluation was based on:
- Visual inspection of detected anomalies
- Alignment with injected abnormal patterns
- Comparison between Isolation Forest and Autoencoder results

### Key Observations
- Isolation Forest performs well on point anomalies
- Autoencoder captures gradual drift more effectively
- A trade-off exists between sensitivity and false positives

---

## Limitations
- No ground-truth labels for quantitative evaluation
- Synthetic data may not fully represent real industrial environments
- Anomaly threshold selection is heuristic

---

## Future Improvements
- Apply the approach to real industrial IoT datasets
- Introduce labeled data for quantitative evaluation
- Explore sequence-based models such as LSTM autoencoders
- Implement adaptive thresholding techniques

---

## How to Run the Project
1. Install required dependencies:
```bash
pip install numpy pandas matplotlib scikit-learn tensorflow
```

Open the notebook:
```bash
jupyter notebook IoT_Time_Series_Anomaly_Detection.ipynb
```

Run all cells in sequence.

### Author

Muhammad Hisham
AI/ML Engineer

### Final Note

This project demonstrates a practical approach to time-series anomaly detection with a focus on understanding data behavior, selecting appropriate models, and interpreting results in real-world contexts.


---

