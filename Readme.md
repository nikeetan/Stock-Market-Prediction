# **Prediction of Daily Stock Movements on the US Market**  

## **Project Overview**  
This project aimed to predict the **sign of stock returns** at the end of approximately **700 days** for around **700 stocks** in the US market. Using **deep learning techniques**, particularly **neural networks**, we developed a predictive model that **outperformed traditional methods** like **polynomial regression** and **LightGBM**.  

Our approach ranked **15th among 20,000 participants** in an international stock market prediction challenge.  

---

## **Preprocessing Steps**  

### **1. Data Cleaning**  
- Removed unnecessary attributes (e.g., anonymized date column).  
- Retained `Equity Code` since it helped in grouping unique stocks.  
- Replaced missing values using **linear interpolation** to maintain time series continuity.  

### **2. Feature Engineering**  
- Extracted relevant time intervals (every **5 minutes**) from **9:30 AM to 3:20 PM**.  
- Grouped data by `Equity Code` to ensure stock movement consistency.  

### **3. Label Generation**  
- End-of-day return defined as **percentage change** from **3:30 PM to 4:00 PM**.  
- Binary Classification Mapping:  
  - **Positive return (≥ 0.5):** `Label = 1`  
  - **Negative return (< 0.5):** `Label = 0`  

---

## **Model Selection & Implementation**  

We experimented with multiple models before selecting the best-performing one:  

- **Polynomial Regression** (Limited due to memory constraints beyond degree 5)  
- **LightGBM** (Good performance but overfitting issue)  
- **Neural Networks** (Best-performing model)  

### **Neural Network Architecture**  
- Layers: 9  
- Epochs: 10  
- Activation Function: Linear  
- Optimizer: Adam  
- Loss Function: Mean Squared Error (MSE)  

---

## **Accuracy Computation & Truth Table Mapping**  

### **1. Truth Table for Binary Classification**  

| **Actual \ Predicted** | **Positive (1)** | **Negative (0)** |  
|------------------------|-----------------|-----------------|  
| **Positive (1)**       | True Positive (TP) | False Negative (FN) |  
| **Negative (0)**       | False Positive (FP) | True Negative (TN) |  

- **True Positive (TP):** Correctly predicted positive returns.  
- **True Negative (TN):** Correctly predicted negative returns.  
- **False Positive (FP):** Incorrectly predicted positive returns.  
- **False Negative (FN):** Incorrectly predicted negative returns.  

### **2. Accuracy Computation**  

 Accuracy = (TP + TN)/ (TP + TN + FP + FN)

For each model:  

| **Model**                | **Accuracy** |  
|--------------------------|-------------|  
| **Polynomial Regression** | 0.5083      |  
| **LightGBM**              | 0.5208      |  
| **Neural Network**        | **0.5238**  |  

- Neural Networks performed best with an accuracy of **52.38%**, slightly outperforming traditional methods.  
- LightGBM had overfitting issues, leading to inconsistencies in generalization.  
- Polynomial regression was limited by memory constraints beyond degree 5.  

---

## **Final Observations**  
- Deep Learning (Neural Networks) captured non-linear stock patterns better than traditional models.  
- Feature selection and missing data handling significantly influenced accuracy.  
- Binary classification was well-suited for this stock movement prediction task.  

---
