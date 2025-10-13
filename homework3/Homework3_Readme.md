# 🧮 Lead Scoring Homework — Bank Marketing Dataset

## 📊 Dataset

In this homework, we will use the **Lead Scoring (Bank Marketing)** dataset.  
Download it directly or via `wget`:

```bash
wget https://raw.githubusercontent.com/alexeygrigorev/datasets/master/course_lead_scoring.csv
```

The goal is to predict whether the client **converted** (signed up to the platform) — this is our **target variable** (`converted`).

---

## 🧹 Data Preparation

Before modeling:
- Check for missing values.
- For **categorical features**, replace missing values with `'NA'`.
- For **numerical features**, replace missing values with `0.0`.

---

## ❓Question 1

**What is the most frequent observation (mode) for the column `industry`?**

**Options**
- NA  
- technology  
- healthcare  
- retail  

✅ **Answer:** `retail'
📘 *Explanation:* After imputing missing values, `'NA'` appeared most frequently in the `industry` column.

---

## ❓Question 2

**Create the correlation matrix for numerical features** and find the pair with the biggest correlation.  
Only consider the pairs below:

- interaction_count and lead_score  
- number_of_courses_viewed and lead_score  
- number_of_courses_viewed and interaction_count  
- annual_income and interaction_count  

✅ **Answer:** annual_income and interaction_count 
📘 *Explanation:* These two features have the strongest positive correlation in the dataset.

---

## 🧩 Data Split

Split your data into **train/val/test = 60%/20%/20%** using `train_test_split` from Scikit-Learn, with `random_state=42`.  
Make sure the target column `converted` is **not** included in your feature set.

---

## ❓Question 3

**Calculate the mutual information score** between the target (`converted`) and the categorical variables, using the training set only.  
Round to 2 decimals.

**Options**
- industry  
- location  
- lead_source  
- employment_status  

✅ **Answer:** `lead_source`  
📊 * MI scores:*
| Feature | MI Score |
|----------|-----------|
| lead_source | **0.0272** |
| industry | 0.0138 |
| employment_status | 0.0071 |
| location | 0.0013 |

📘 *Explanation:* `lead_source` provides the most information about conversion likelihood.

---

## ❓Question 4

**Train a Logistic Regression model** with parameters:  
```python
model = LogisticRegression(solver='liblinear', C=1.0, max_iter=1000, random_state=42)
```
Include all categorical variables via **one-hot encoding**.

**What accuracy did you get on the validation set?**

**Options**
- 0.64  
- 0.74  
- 0.84  
- 0.94  

✅ **Answer:** `0.64`  
📘 *Explanation:* The validation accuracy was approximately **0.682**, which is closest to **0.64** among the given options.

---

## ❓Question 5

**Find the least useful feature using feature elimination:**

Train the model again (same parameters as Q4). Then:
- Remove each of these features one by one:  
  `'industry'`, `'employment_status'`, `'lead_score'`
- Compute the difference between baseline and new accuracy.

| Feature Removed | Δ Accuracy | Interpretation |
|------------------|------------|----------------|
| industry | –0.00685 | Removing slightly increased accuracy |
| **employment_status** | **0.00000** | No change → least useful |
| lead_score | +0.00685 | Removing decreased accuracy |

✅ **Answer:** `'employment_status'`  
📘 *Explanation:* Removing it made **no difference** to accuracy, indicating it adds little predictive value.

---

## ❓Question 6

**Train regularized Logistic Regression** with different `C` values:  
`[0.01, 0.1, 1, 10, 100]`

Round the validation accuracy to 3 decimals.

| C Value | Validation Accuracy |
|----------|----------------------|
| **0.01** | **0.688** |
| 0.1 | 0.682 |
| 1 | 0.682 |
| 10 | 0.682 |
| 100 | 0.682 |

✅ **Answer:** `C = 0.01`  
📘 *Explanation:* The model performed best with **C = 0.01**, and per instructions, we select the **smallest C** in case of ties.

---



## 🧠 Notes

- **C parameter** in logistic regression controls regularization strength — smaller C means stronger regularization.
- **Mutual Information** captures non-linear dependencies between categorical variables and the target.
- **Feature elimination** helps identify irrelevant or redundant predictors.

---

### 📚 Dependencies
```bash
pip install pandas scikit-learn numpy
```

### 💻 Run this notebook in Colab
You can reproduce everything using this link:  
👉 [Open in Colab](https://colab.research.google.com)

---

**Author:** Fareeda Hamid  
**Course:** Machine Learning Zoomcamp — Lead Scoring Homework
