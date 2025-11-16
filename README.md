# 📊 Forecasting Weekly Sales Using Advertising Spend   
**Model Used:** Decision Tree Regression  
**Goal:** Predict weekly sales based on advertising spending across TV, Radio, and Social Media.

---

## 1️⃣ Introduction
The purpose of this project is to build a predictive model that estimates **Weekly Sales (in thousands of USD)** based on the amount spent on three advertising channels:
- TV
- Radio
- Social Media

This analysis helps answer the question: **How much sales revenue can we expect given a specific advertising budget?**

Understanding this relationship enables data-driven decision-making for marketing teams, helping optimize advertising budgets for maximum revenue impact.

---

## 2️⃣ Methodology

### 📁 Dataset Description
The dataset contains the following fields:

| Feature | Description |
|---------|-------------|
| TV_Spend_kUSD | Weekly spending on TV ads (in thousands USD) |
| Radio_Spend_kUSD | Weekly spending on Radio ads (in thousands USD) |
| Social_Spend_kUSD | Weekly spending on Social ads (in thousands USD) |
| Weekly_Sales_kUSD | Sales generated that week (in thousands USD) (target variable) |

The dataset was loaded directly from GitHub and explored using pandas.

---

### 🔧 Data Preprocessing & EDA
- Checked shape, missing values, and descriptive statistics
- No missing values detected
- Numerical features already in usable format
- Computed correlations and visualized relationships

**Correlation Heatmap**
- `TV_Spend_kUSD` showed the strongest positive correlation with `Weekly_Sales_kUSD` (r = 0.86)
- Radio and Social Media spend also showed positive but weaker correlations

**Key observation:** TV advertising appears to be the most influential variable.

---

## 3️⃣ Model & Findings

### 🧠 Model Used
I trained a **Decision Tree Regressor** using an 70/30 train-test split.

```python
reg_tree = DecisionTreeRegressor(max_depth=3, random_state=42)
reg_tree.fit(X_train, y_train)
```

### 📈 Performance Metrics
|Metric	|Train Set|	Test Set|	Interpretation|
|-------|--------|-------|------|
|MAE|	4.85 kUSD|	6.73 kUSD|	On average, predictions are off by $4,800 (train) to $6,700 (test)|
|R²	|0.807|	0.634|	Model explains 80.7% (train) and 63.4% (test) of variance|

Interpretation

The model performs well on training data and reasonably on unseen test data

A generalization gap exists (Train R² = 0.807 → Test R² = 0.634)

This indicates mild overfitting, but the model still provides useful predictive power

---

## 4️⃣ Recommendations

Based on model findings:

💡 Business Recommendations

- Prioritize TV advertising — it has the strongest impact on sales.

- Combine multiple channels rather than relying on just one.

- Consider incremental experimentation to optimize budget allocation.

- Use this model to forecast future performance and adjust spending proactively.

- Improve model performance by:

  - Increasing dataset size
  
  - Engineering new features (e.g., seasonality, consumer behavior)
  
  - Tuning tree hyperparameters or using ensembles (Random Forests / XGBoost)
 
---

## 5️⃣ Conclusion

This project demonstrates how Decision Tree Regression can be applied to forecast weekly sales based on advertising spend.
Key takeaways:

TV spend is the strongest predictor of weekly sales

Model performance is reasonably strong with R² of 0.63 on test data

The model provides useful insights but can be improved with tuning and more data
