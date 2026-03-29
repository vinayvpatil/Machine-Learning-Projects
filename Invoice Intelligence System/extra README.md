# Vendor Invoice Intelligence System

## Overview

The **Vendor Invoice Intelligence System** is a machine learning–powered application designed to detect suspicious or potentially fraudulent vendor invoices. The system analyzes invoice details and compares them with purchase order information to identify inconsistencies that may indicate errors, overcharges, or fraud.

This project combines **data processing, machine learning, and an interactive dashboard** to help businesses automatically monitor invoice transactions and flag high-risk invoices for further review.

---

# Problem Statement

Organizations process thousands of vendor invoices every month. Manual verification of invoices against purchase orders is time-consuming and prone to human error.

This project aims to:

* Automatically analyze invoice data
* Detect unusual patterns or mismatches
* Flag suspicious invoices for review
* Provide a risk score indicating the probability of fraud

---

# Key Features

## 1. Invoice Fraud Detection

The system uses a **Random Forest Machine Learning model** to classify invoices as:

* **Valid Invoice**
* **Flagged / Suspicious Invoice**

---

## 2. Fraud Risk Score

Instead of only binary classification, the system provides a **Fraud Risk Score (0–100%)** based on prediction probability.

Risk Levels:

| Risk Score | Risk Level  |
| ---------- | ----------- |
| 0 – 40%    | Low Risk    |
| 40 – 70%   | Medium Risk |
| 70 – 100%  | High Risk   |

---

## 3. Single Invoice Prediction

Users can manually enter invoice details through the **Streamlit interface** and receive instant fraud detection results.

---

## 4. Bulk Invoice Analysis (CSV Upload)

The system supports **CSV file uploads** to analyze multiple invoices simultaneously.

Capabilities:

* Upload invoice dataset
* Automatically detect suspicious invoices
* Generate fraud risk scores
* Download processed results

---

## 5. Interactive Dashboard

A **Streamlit web application** provides an easy-to-use interface for:

* Invoice input
* Fraud prediction
* Risk analysis
* CSV upload and download
* Results visualization

---

# Machine Learning Pipeline

The project follows a structured ML pipeline.

## 1. Data Loading

Data is extracted from an **SQLite database** containing:

* Vendor invoices
* Purchase orders
* Receiving data

SQL queries are used to aggregate purchase order information and combine it with invoice data.

---

## 2. Feature Engineering

Key features used for fraud detection:

* `invoice_quantity`
* `invoice_dollars`
* `invoice_freight`
* `total_item_quantity`
* `total_item_dollars`

Additional derived features include:

* Days between PO and invoice
* Receiving delay
* Purchase order aggregation

---

## 3. Invoice Risk Label Creation

A rule-based system initially creates labels for training the model.

Example conditions:

* Large difference between invoice amount and purchase amount
* High receiving delay

If such conditions are detected, the invoice is marked as **flagged**.

---

## 4. Data Preprocessing

Steps include:

* Train-test split
* Feature scaling using **StandardScaler**
* Data preparation for machine learning

Scaler is saved using **Joblib** for inference.

---

## 5. Model Training

The model used:

**Random Forest Classifier**

Hyperparameter tuning is performed using:

* **GridSearchCV**
* Cross-validation
* F1-score optimization

Parameters tuned include:

* `n_estimators`
* `max_depth`
* `min_samples_split`
* `min_samples_leaf`
* `criterion`

---

## 6. Model Evaluation

Model performance is evaluated using:

* Accuracy
* Classification Report
* Precision
* Recall
* F1 Score

---

# Model Inference

The trained model and scaler are saved as:

```
models/
│
├── predict_flag_invoice.pkl
├── scaler.pkl
```

During prediction:

1. Input data is converted to a dataframe
2. Features are scaled using the saved scaler
3. The trained model predicts fraud probability
4. Risk score is calculated

```
Fraud Risk Score = Probability of Fraud × 100
```

---

# Streamlit Application

The project includes an interactive **Streamlit dashboard**.

### Features of the App

* Single invoice fraud detection
* CSV bulk invoice analysis
* Fraud risk scoring
* Risk level classification
* Downloadable prediction results
* Interactive UI

---

# Example CSV Input

```
invoice_quantity,invoice_dollars,invoice_freight,total_item_quantity,total_item_dollars
100,15000,120,98,14950
50,4000,40,50,3900
70,8000,60,65,7800
```

---

# Project Structure

```
Vendor Invoice Intelligence System
│
├── data_preprocessing.py
├── model_evaluation.py
├── train.py
├── inference.py
├── app.py
│
├── models
│   ├── predict_flag_invoice.pkl
│   └── scaler.pkl
│
├── inventory.db
│
└── README.md
```

---

# Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* SQLite
* Joblib
* Streamlit
* Matplotlib
* Seaborn

---

# How to Run the Project

## 1. Install Dependencies

```bash
pip install pandas numpy scikit-learn streamlit joblib matplotlib seaborn
```

---

## 2. Train the Model

```bash
python train.py
```

---

## 3. Run the Streamlit Application

```bash
streamlit run app.py
```

---

# Use Cases

This system can be used by:

* Finance departments
* Procurement teams
* Vendor management teams
* Internal audit teams

Applications include:

* Fraud detection
* Invoice verification
* Vendor monitoring
* Automated auditing

---

# Future Improvements

Possible enhancements:

* Explainable AI using **SHAP**
* Real-time API deployment using **FastAPI**
* Dashboard analytics for fraud trends
* Vendor risk scoring system
* Integration with enterprise ERP systems

---

# Conclusion

The **Vendor Invoice Intelligence System** demonstrates how machine learning can automate invoice verification and fraud detection. By combining data analytics, machine learning, and an interactive dashboard, the system helps organizations identify suspicious transactions efficiently and reduce financial risk.
