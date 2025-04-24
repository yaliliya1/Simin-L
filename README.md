# Forecasting Sales for Rossmann Stores (ADS1002 Project – Monash University)

This repository contains a sales forecasting project for Rossmann drug stores, completed as part of the ADS1002 unit at Monash University. The project involved exploratory data analysis and predictive modelling using a large retail dataset covering 1,115 stores across Europe between 2013 and 2015.

---

## 📌 Objective

The project had two primary goals:
- Identify key patterns that affect retail sales, such as holidays, store types, and promotions.
- Build predictive models that can estimate daily sales at each Rossmann store.

---

## 📚 Dataset

- Over **1 million** rows of daily store data  
- Features include: `Sales`, `Customers`, `StoreType`, `Assortment`, `Promo`, `CompetitionDistance`, `Holidays`, and others  
- Two merged datasets: `train.csv` (transactional) + `store.csv` (store metadata)

---

## 🛠️ Preprocessing

- Merged transactional and store metadata on store ID
- Forward and backward filled missing values
- Removed rows with remaining `NaN` if needed
- One-hot encoded categorical variables such as `StoreType`, `StateHoliday`, and `Assortment`

---

## 📊 Exploratory Data Analysis (EDA)

- Found strong correlation between `Sales` and `Customers` (r = 0.71)
- Sales were higher for:
  - Store Type `b`
  - Assortment type `extra`
  - When **Promotion 1** was active (but overuse of Promotion 2 led to declines)
  - During school holidays
- Sales peaked in December and on Sundays
- Sales trended upward despite decreasing customer count (time series pattern)
- Time series plots revealed:
  - Weekly and monthly periodicities
  - Clear holiday-driven effects

---

## 🤖 Modelling

We trained and evaluated four different models:
- **Multivariate Linear Regression**
- **Ridge Regression (normalised)**
- **Decision Tree Regression**
- **Random Forest Regression**

Each model was trained on:
- Full feature set (including `Customers`)
- Reduced feature set (excluding `Customers` to reduce dependency)

### ✅ Best Model: Random Forest Regressor
- `R² Train`: 0.9850
- `R² Test`: 0.9015
- Relative error mean: 0.04  
- Standard deviation of relative error: 6.73

---

## 📈 Model Example

Given a store on a Friday with:
- 3443 customers  
- No active promotions  
- Not a holiday  
- Store Type `b` with `extra` assortment  
- Competition 840m away  

→ **Predicted sales: \$11,120**

---

