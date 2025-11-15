# NAT Traffic Classification with Machine Learning

This project provides a complete machine learning pipeline for analyzing and classifying firewall and NAT (Network Address Translation) traffic logs. The goal is to predict whether a network action (e.g., `ALLOW` or `DENY`) occurs based on packet-level metrics, port activity, and NAT translation behavior. The repository includes exploratory visualization, feature engineering, model training, evaluation, and feature importance analysis using multiple classical ML models. It is designed for students, researchers, cybersecurity analysts, and network engineers working on traffic classification or NAT behavior modeling.

---

## 📦 Dataset Description

This repository uses the **Internet Firewall Log Dataset (log2.csv)** from the UCI Machine Learning Repository, available here:  
👉 https://archive.ics.uci.edu/ml/datasets/Internet+Firewall+Data  

This dataset is designed for analyzing and modeling network security decisions in real-world firewall environments. It contains **65,532 traffic flow records** captured from a university firewall system and includes detailed **connection metadata, NAT translation fields, packet statistics**, and the corresponding **firewall action** applied to each flow.

The dataset provides a structured foundation for research in **traffic classification, firewall policy automation, anomaly detection**, and **AI-driven cybersecurity**, making it suitable for developing and benchmarking intelligent network security models.

### 🔌 Port-Level Fields
- Source Port  
- Destination Port  
- NAT Source Port  
- NAT Destination Port  

### 📊 Numerical Traffic Metrics
- Bytes, Bytes Sent, Bytes Received  
- Packets  
- Elapsed Time (sec)  
- pkts_sent, pkts_received  

### 🎯 Target Variable
- **Action** (`ALLOW` or `DENY`)

---

## 🧪 Feature Engineering

Two binary NAT indicators are added:

- `Source_Port_NAT_Match`: 1 if Source Port = NAT Source Port  
- `Destination_Port_NAT_Match`: 1 if Destination Port = NAT Destination Port  

These features capture NAT translation consistency, which improves model performance.

---

## 🔄 Workflow Pipeline

1. **Data Loading & Preview**  
   Read CSV, inspect shape, head, and missing values.

2. **Exploratory Visualization**  
   - Port distribution histograms  
   - NAT match frequency bar plots  

3. **Feature Engineering**  
   Add NAT matching indicators, drop raw port columns after transformation.

4. **Feature Scaling**  
   Normalize numerical features using MinMaxScaler.

5. **Model Training**  
   Train/test split (80/20) followed by evaluation of:  
   - Random Forest  
   - Extra Trees  
   - Gradient Boosting  
   - AdaBoost  
   - KNN  
   - XGBoost  
   - LightGBM  

6. **Evaluation Metrics**  
   - Accuracy  
   - Cross-validation score  
   - Classification report  
   - Confusion matrix  
   - Feature importance (tree models)

---

## 🧠 Model Performance Summary

| Model             | Test Accuracy | CV Performance | Notes |
|------------------|---------------|----------------|-------|
| **Extra Trees**   | High          | Stable         | Best overall consistency |
| **Random Forest** | High          | Strong         | Robust and reliable |
| XGBoost           | High          | Strong         | Excellent discriminative power |
| Gradient Boosting | Moderate      | Moderate       | Good for structured data |
| AdaBoost          | Good          | Good           | Lightweight and fast |
| KNN               | Varies        | Sensitive      | Dependent on scaling |
| Decision Tree     | Varies        | Unstable       | Interpretable but simple |

Extra Trees and Random Forest were the most consistent performers.

---

## 📈 Visualizations

- **Port Distribution Histograms**  
  Show wide variation in ports, motivating feature engineering.

- **NAT Match Plots**  
  Display how often NAT keeps or modifies port values.

- **Confusion Matrices**  
  Visualize correct vs. incorrect predictions for each classifier.

- **Feature Importance Plots**  
  Identify which features (bytes, packets, NAT match) most influence decisions.

---

## ⚙️ Installation & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
