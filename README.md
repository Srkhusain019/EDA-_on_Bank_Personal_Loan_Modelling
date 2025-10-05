# 🏦 EDA on Bank Personal Loan Modelling Dataset

## 📘 Project Overview
This project performs a **comprehensive exploratory data analysis (EDA)** and **statistical interpretation** using the **Bank Personal Loan Modelling Dataset**.  
The dataset is used to understand customer demographics, income patterns, and behavioral trends related to **loan acceptance** and **banking service usage**.

The project is divided into two sections:
- **Section 1:** Conceptual and basic statistical interpretation questions.
- **Section 2:** Applied EDA and statistical analysis using Python on the dataset.

---

## 🧠 Objectives
- Understand and apply core **statistical concepts** (mean, variance, skewness, z-score, etc.)
- Analyze **customer characteristics** related to personal loan adoption.
- Perform **data visualization and distribution analysis**.
- Use **Python libraries** to calculate key metrics, correlation, and outlier detection.

---

## 🧾 Section 1: Descriptive & Conceptual Questions

| No. | Question | Key Concept / Interpretation |
|-----|-----------|------------------------------|
| 1 | A test of 10 learners with mean = 85, variance = 0 | All learners scored **exactly 85**; zero variance means no difference among scores. |
| 2 | Mean house size = 2224 sq.ft, Median = 1500 sq.ft | Distribution is **right-skewed** (presence of larger houses). |
| 3 | Compare variability in expenditure | Use **Coefficient of Variation (CV)** = (σ / μ) × 100 to compare relative variability. |
| 4 | COVID patients cumulative frequency | Identify modal, median, and highest frequency class intervals. |
| 5 | Average return on investment | Use **Geometric Mean** to calculate average return over multiple years. |
| 6 | Measuring average height of males | Use **sampling** and compute a **statistic** (not parameter, since it’s sample-based). |
| 7 | Z-score calculation | Used to standardize data and identify outliers. |

---

## 📊 Section 2: Exploratory Data Analysis on Bank Dataset

### 🧰 Tools & Libraries
- **Python Libraries:** pandas, numpy, matplotlib, seaborn, scipy, sklearn
- **Environment:** Jupyter Notebook

---

9️⃣ Measures of Central Tendency & Dispersion

Mean, Median, Mode, Range, Variance, Standard Deviation

Quantitative variables: Age, Experience, Income, CCAvg, Mortgage, etc.

🔟 Relationship Between Age & Experience

Statistical Method: Correlation Analysis

sns.regplot(x='Age', y='Experience', data=df)
plt.title('Relationship between Age and Experience')
plt.show()


✅ Strong positive relationship observed between Age and Experience.

11️⃣ Most Frequent Family Size
df['Family'].mode()


✅ Most frequent family size: Family = 1

12️⃣ Percentage of Variation in ‘Income’
(df['Income'].std() / df['Income'].mean()) * 100


Gives the Coefficient of Variation (CV) — indicating how much the income varies around its mean.

13️⃣ Imputation of Mortgage Variable

Many zero values were replaced with a logical median or mean (e.g., df['Mortgage'].replace(0, df['Mortgage'].median())).

14️⃣ Density Curve of CCAvg for Credit Card Holders
sns.kdeplot(df[df['CreditCard']==1]['CCAvg'], shade=True)
plt.title('Density of Credit Card Average Spending')


✅ Most customers spend between 1–3 units, with a slightly right-skewed distribution.

15️⃣ Outlier Detection

Outliers were checked using:

Boxplots and Z-scores

Visualization:

sns.boxplot(df['Income'])


✅ Boxplots are ideal for stakeholder presentation.

16️⃣ Decile Values of ‘Income’
df['Income'].quantile([0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9])
<img width="710" height="615" alt="Screenshot 2025-10-05 194828" src="https://github.com/user-attachments/assets/596a4003-a12d-48f3-b963-ba51aa6d841f" />


✅ Provides 10th to 90th percentile income range for segmentation.

17️⃣ Interquartile Range (IQR)
Q1 = df[num_cols].quantile(0.25)
Q3 = df[num_cols].quantile(0.75)
IQR = Q3 - Q1


✅ IQR used for continuous numerical variables.

18️⃣ High Income vs Credit Card Spending
sns.scatterplot(x='Income', y='CCAvg', data=df)
plt.title('Income vs Credit Card Spending')
plt.show()
<img width="669" height="517" alt="Screenshot 2025-10-05 194400" src="https://github.com/user-attachments/assets/21ef75ce-3986-4db9-96e7-4ea4756fc541" />


✅ Positive correlation — higher income customers tend to spend more on credit cards.

19️⃣ Online Banking Usage
online_income = df[df['Online'] == 1]['Income']
offline_income = df[df['Online'] == 0]['Income']

print(f"Average income (Online users): {online_income.mean()}")
print(f"Average income (Offline users): {offline_income.mean()}")


Results:

Average income (Online users): 74.31

Average income (Offline users): 72.97

✅ Online banking users have slightly higher average income.

20️⃣ Z-Score Outlier Detection (Income)
df['Income_zscore'] = (df['Income'] - df['Income'].mean()) / df['Income'].std()
outliers = df[(df['Income_zscore'] < -3) | (df['Income_zscore'] > 3)]
print(outliers.shape[0])
```python
df.describe()
