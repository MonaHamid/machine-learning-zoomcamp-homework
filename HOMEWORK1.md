# 📘 Homework 1 – Car Fuel Efficiency

This repository contains my solutions for **Homework 1** of the ML Zoomcamp.  
The task involves setting up the environment, loading the Car Fuel Efficiency dataset, and answering several data analysis questions.

---

## ⚙️ Environment Setup
To run the notebook/scripts, install the following packages:

```bash
pip install numpy pandas matplotlib seaborn
```

---

## 📊 Dataset
We use the **Car Fuel Efficiency dataset**:

```bash
wget https://raw.githubusercontent.com/alexeygrigorev/datasets/master/car_fuel_efficiency.csv
```

Then load it with Pandas:
```python
import pandas as pd
df = pd.read_csv("car_fuel_efficiency.csv")
```

---

## 📝 Questions & Answers

### Q1. Pandas version  
What's the version of Pandas that you installed?  

**Answer:** `2.2.2`

---

### Q2. Records count  
How many records are in the dataset?  

Options: 4704, 8704, 9704, 17704  

**Answer:** `9704`

---

### Q3. Fuel types  
How many fuel types are presented in the dataset?  

Options: 1, 2, 3, 4  

**Answer:** `2`

---

### Q4. Missing values  
How many columns in the dataset have missing values?  

Options: 0, 1, 2, 3, 4  

**Answer:** `4`

---

### Q5. Max fuel efficiency (Asia)  
What’s the maximum fuel efficiency of cars from Asia?  

Options: 13.75, 23.75, 33.75, 43.75  

**Answer:** `23.75`

---

### Q6. Median value of horsepower  
Steps:  
1. Find the median value of `horsepower` column in the dataset.  
2. Calculate the most frequent value of the same column.  
3. Fill missing values in `horsepower` with the most frequent value.  
4. Recalculate the median.  

**Answer:** ✅ Yes, it increased

---

### Q7. Sum of weights (Linear regression exercise)  
Steps:  
1. Select all cars from Asia.  
2. Select only columns `vehicle_weight` and `model_year`.  
3. Take the first 7 values → NumPy array `X`.  
4. Compute `XTX = X.T @ X`.  
5. Invert `XTX`.  
6. Create array `y = [1100, 1300, 800, 900, 1000, 1100, 1200]`.  
7. Compute `w = (XTX^-1) @ X.T @ y`.  
8. Take the sum of `w`.  

**Answer:** `0.51`

---

## ✅ Final Multiple-Choice Answers
1. Pandas version → `2.2.2`  
2. Records count → `9704`  
3. Fuel types → `2`  
4. Missing values → `4`  
5. Max fuel efficiency → `23.75`  
6. Median horsepower change → **Yes, it increased**  
7. Sum of weights → `0.51`

---

## 🚀 How to Run
Clone the repo and open the notebook/script:
```bash
git clone <your-repo-url>
cd <your-repo>
jupyter notebook homework1.ipynb
```

Or run scripts directly with Python:
```bash
python homework1.py
```
