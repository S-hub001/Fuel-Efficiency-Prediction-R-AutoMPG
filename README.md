# 🚗 Fuel Efficiency Prediction using Auto-MPG Dataset (R)

This project analyzes how different car features impact fuel efficiency using the **Auto-MPG dataset** from the UCI Machine Learning Repository. It applies data preprocessing, correlation analysis, and regression modeling in **R** to build predictive models for miles per gallon (MPG).

---

## 🎯 Objective
To explore which car features (like weight, horsepower, etc.) most influence fuel efficiency and develop a prediction model for MPG using statistical techniques.

---

## 📚 Dataset Overview
- **Name:** Auto-MPG Dataset  
- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/9/auto+mpg)  
- **Type:** Secondary (public, pre-collected)
- **Total Records:** 398  
- **Target Variable:** `mpg` (Miles Per Gallon)

### 🔑 Key Features:
- `mpg`: Fuel efficiency
- `cylinders`: Engine cylinders
- `displacement`, `horsepower`: Engine size/power
- `weight`: Vehicle weight
- `acceleration`: Speed pickup
- `model year`: Year of manufacture
- `origin`: Region (1 = USA, 2 = Europe, 3 = Japan)
- `car name`: Text (not used in modeling)

---

## 🧼 Data Preprocessing

### ✅ Handling Missing Values:
- Rows with NA removed or imputed using **mean imputation**:
```r
data_cleaned$HorsePower[is.na(data_cleaned$HorsePower)] <- mean(data_cleaned$HorsePower, na.rm = TRUE)
data_cleaned$acceleration[is.na(data_cleaned$acceleration)] <- mean(data_cleaned$acceleration, na.rm = TRUE)
```

## ❌ Outlier Removal

Outliers were detected using the **IQR method**. To retain more data while still cleaning extreme values, the threshold was increased from **1.5 to 2.4**.

---

## 📏 Standardization

Standardization was applied **only** to continuous numeric variables such as:

- `mpg`
- `horsepower`
- `weight`
- `acceleration`

Categorical variables like `origin` were **factorized or one-hot encoded**.

---

## 📊 Correlation Analysis

**Pearson correlation coefficients** revealed the following relationships with `mpg`:

- `weight` vs `mpg`: **-0.83**
- `horsepower` vs `mpg`: **-0.78**
- `model year` vs `mpg`: **+0.58**

📌 **Multicollinearity** was noted between `horsepower`, `displacement`, and `cylinders`.

---

## 📈 Modeling

### 1️⃣ Simple Linear Regression

- **Best single predictor:** `Weight` (R² = **0.693**)
- Other strong negative predictors: `horsepower`, `displacement`
- **Weakest predictor:** `acceleration`

### 2️⃣ Multiple Linear Regression

- **R² = 0.8207** → Model explains ~82% of variation in `mpg`.

**Significant Predictors:**

- `weight`: Strong negative impact  
- `model year`: Positive impact  
- `origin`: Moderate positive effect  

**Less significant variables:** `cylinders`, `acceleration`

---

## 🔍 Interpretation of Coefficients

| Variable      | Coefficient | Interpretation                                 |
|---------------|-------------|-----------------------------------------------|
| `Weight`      | -0.8310     | Heavier cars = lower MPG                      |
| `Horsepower`  | -0.7809     | More power = less efficient                   |
| `Displacement`| -0.8058     | Bigger engine = lower MPG                    |
| `Cylinders`   | -0.4565     | More cylinders = less fuel efficiency        |
| `Acceleration`| +0.4140     | Weak positive effect on MPG                   |
| `Model Year`  | +0.1607     | Newer cars = better MPG                      |
| `Origin`      | +0.7035     | Cars from some regions (e.g., Japan) = better MPG |

---

## 💡 Conclusion

- Lighter and newer cars tend to have **better fuel efficiency**.
- **Weight** is the **single most important predictor** of MPG.
- The regression model supports both **manufacturers** and **consumers** in making **eco-friendly** vehicle decisions.

---

## 🧠 Skills Applied

- Data cleaning & preprocessing  
- Descriptive statistics  
- Correlation & multicollinearity analysis  
- Linear & multiple regression modeling in R  
- Model interpretation & feature analysis

---

## 🧑‍💻 Author

**Syeda Shanzay Shah**    
Project submitted for **Probability and Statistics** course 📊
