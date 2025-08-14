# Forest Fire Classification using MODIS Active Fire Data – India (2021)

This project focuses on predicting the **type of forest fire** detected by NASA’s MODIS (Moderate Resolution Imaging Spectroradiometer) satellite data using **machine learning classification algorithms**. MODIS operates aboard the **Terra** and **Aqua** satellites, capturing vital environmental data for monitoring wildfires globally.

---

## 📂 Dataset
The dataset used is **MODIS Active Fire Data (India, 2021)**, which contains ~12,000 records with the following features:

- **latitude, longitude** – Geographical coordinates of detected fire pixels.  
- **brightness, bright_t31** – Brightness temperature (in Kelvin).  
- **scan, track** – MODIS pixel dimensions on the Earth’s surface.  
- **acq_time** – Time of fire detection.  
- **satellite** – Source satellite (Terra / Aqua).  
- **instrument** – MODIS sensor.  
- **confidence** – Detection confidence score (0–100).  
- **frp** – Fire radiative power (MW).  
- **daynight** – Time of detection (Day/Night).  
- **type** – Target variable:  
  - `0` – Presumed vegetation fire  
  - `1` – Active volcano  
  - `2` – Other static land source  
  - `3` – Offshore  

---

## 🔄 Preprocessing
- Data cleaning & handling missing values.  
- Feature selection and correlation analysis.  
- Train-test split: **80% training, 20% testing**.  

---

## 🤖 Models Implemented

### 1. Logistic Regression  
- Solver: `liblinear` with L2 regularization.  
- **Accuracy:** 93%  
- **Strength:** Perfect recall for type `0`.  
- **Weakness:** Underfitting due to high bias.  

### 2. K-Nearest Neighbours (KNN)  
- Optimal `K = 2` (determined via accuracy plot).  
- **Accuracy:** 95%  
- **Weakness:** More misclassifications for type `0` than Logistic Regression.  

### 3. XGBoost (Best Performing Model)  
- Chosen to reduce bias and improve performance.  
- Optimal hyperparameters found using `GridSearchCV`:  
  - `n_estimators = 200`  
  - `max_features = 4`  
- **Accuracy:** 98%  
- Less than 2% misclassifications.  

---

## 📊 Results & Conclusion
- **XGBoost** outperforms Logistic Regression and KNN, providing the highest accuracy and balanced precision-recall.  
- Logistic Regression and KNN showed signs of underfitting, while XGBoost effectively handled bias and variance.  
- **Final Recommendation:** Use XGBoost for forest fire type prediction on MODIS data.

---
