
# Google Play Store App Rating Prediction

This repository presents a comprehensive data analysis and predictive modeling project on Google Play Store applications. The objective is to analyze app characteristics and build a model that can predict **app ratings**, helping the Play Store team identify promising apps to **boost visibility and engagement**.

---

## Objective

Google Play is launching a feature to **highlight high-potential apps** through recommendation and search result boosts. This project supports that goal by predicting app ratings based on app metadata.

---

## Problem Statement

The goal is to identify features that contribute to high app ratings and predict those ratings using linear regression. Apps with higher predicted ratings can be flagged as candidates for recommendation boosts.

---

## Dataset Overview

- Source: `googleplaystore.csv`
- Key Fields:
  - `App`, `Category`, `Rating`, `Reviews`, `Size`, `Installs`, `Type`, `Price`
  - `Content Rating`, `Genres`, `Last Updated`, `Current Ver`, `Android Ver`

---

## Steps Performed

### 1. Data Cleaning & Preprocessing

- Removed nulls and duplicates
- Converted columns with inconsistent formats:
  - `Size`: Converted to numeric (MB, KB handled)
  - `Reviews`, `Installs`, and `Price`: Cleaned symbols (`+`, `,`, `$`) and cast to numeric
- Applied sanity checks:
  - Ratings must be between 1 and 5
  - Reviews ≤ Installs
  - Free apps must have Price = 0

### 2. Univariate & Bivariate Analysis

#### Univariate Plots:
- **Boxplots** for `Price` and `Reviews` to detect outliers
- **Histograms** for `Rating`, `Size`, and others to check distribution

#### Bivariate Plots:
- **Rating vs. Price** – Does price influence user satisfaction?
- **Rating vs. Size** – Are larger apps better rated?
- **Rating vs. Reviews** – Does volume of feedback impact rating?
- **Boxplots** for:
  - `Rating vs. Content Rating`
  - `Rating vs. Category`

### 3. Outlier Treatment

- Dropped apps with:
  - Price > $200
  - Reviews > 2 million
  - Extremely high installs (based on 95th percentile threshold)

### 4. Feature Engineering

- Applied `np.log1p()` transformation to `Reviews` and `Installs` to reduce skew
- Dropped unused columns: `App`, `Last Updated`, `Current Ver`, `Android Ver`
- Created **dummy variables** for:
  - `Category`, `Genres`, `Content Rating`

---

##  Model Building: Linear Regression

- **Train-Test Split**: 70–30
- **Model**: Linear Regression
- **Evaluation**:
  - Reported **R² score** on training set
  - Evaluated model performance on test data

---

##  Key Insights

- Apps with **moderate pricing or free** tend to have higher ratings.
- **Lighter-weight apps** generally perform better in terms of ratings.
- **Casual genres** and **child-friendly content** often receive higher user feedback.
- **More reviews ≠ higher rating**, but there is a loose positive correlation.

---

##  Tools & Libraries

- **Python** (Jupyter Notebook)
- **Pandas**, **NumPy** – Data handling
- **Matplotlib**, **Seaborn** – Visualization
- **Scikit-learn** – Model building & evaluation

---

