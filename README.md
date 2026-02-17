# Employee Engagement Sentiment Analysis

## Project Overview

This project analyzes employee email communications to assess sentiment, engagement patterns, and potential flight risks. The analysis is conducted using Natural Language Processing (NLP), Exploratory Data Analysis (EDA), and Predictive Modeling techniques.

The objective is to derive meaningful insights from an unlabeled dataset of employee emails and evaluate sentiment trends at an individual and organizational level.

---

## Project Objectives

The project accomplishes the following:

- Automated Sentiment Labeling (Positive, Negative, Neutral)
- Exploratory Data Analysis (EDA)
- Monthly Employee Sentiment Score Calculation
- Employee Ranking (Top Positive & Negative Performers)
- Flight Risk Identification
- Linear Regression Modeling to analyze sentiment trends

---

## Dataset Description

The dataset contains employee email records with the following fields:

- `Subject` – Email subject
- `body` – Email content
- `date` – Email timestamp
- `from` – Employee email ID (used as Employee Identifier)

The dataset is unlabeled and requires sentiment classification.

---

## Methodology

### 1. Sentiment Labeling

Sentiment classification is performed using TextBlob polarity scoring.

Polarity scoring rules:

- Polarity > 0 → Positive
- Polarity < 0 → Negative
- Polarity = 0 → Neutral

Each message is assigned a numeric score:

- Positive = +1
- Negative = -1
- Neutral = 0

This approach is rule-based, deterministic, and fully reproducible.

---

### 2. Exploratory Data Analysis (EDA)

EDA includes:

- Dataset structure inspection
- Missing value analysis
- Sentiment distribution visualization
- Monthly sentiment trend analysis
- Email activity distribution per employee

Visualizations are generated to support insights and stored in the `visualizations/` folder.

---

### 3. Employee Score Calculation

For each employee:

- Monthly sentiment scores are computed by summing message scores.
- Scores reset at the beginning of each new month.
- Aggregation is performed using group-by operations on Employee and Month.

Formula:

Monthly Score = Sum of message sentiment scores within that month

---

### 4. Employee Ranking

For each month:

- Top 3 Positive Employees:
  - Sorted by highest monthly score
  - Alphabetically sorted in case of tie

- Top 3 Negative Employees:
  - Sorted by lowest monthly score
  - Alphabetically sorted in case of tie

This ranking is derived strictly from the calculated monthly sentiment scores.

---

### 5. Flight Risk Identification

An employee is flagged as a Flight Risk if:

- They send 4 or more negative emails within a given month.

This rule is applied using grouped monthly negative counts per employee.

The resulting flagged employees are extracted and listed.

---

### 6. Predictive Modeling (Linear Regression)

A Linear Regression model (using sklearn) is developed to analyze and predict sentiment score trends.

Features used:

- Average Message Length (monthly)
- Average Word Count (monthly)

Steps:

- Feature engineering
- Train-test split
- Model fitting
- Performance evaluation

Evaluation metrics:

- Mean Squared Error (MSE)
- R² Score

This modeling step helps understand the relationship between communication behavior and sentiment scores.

---

## Key Insights

- The majority of employee emails are Neutral in tone.
- Certain employees exhibit recurring negative sentiment patterns.
- Flight risks are identifiable through negative frequency patterns.
- Communication characteristics (length and word count) show measurable correlation with sentiment trends.

---


## How to Run

1. Open `Employee_Sentiment_Analysis.ipynb`
2. Run all cells sequentially from top to bottom.
3. Review the generated visualizations and model outputs.

All steps are reproducible from raw dataset to final outputs.

---

## Dependencies

The project requires the following Python libraries:

- pandas  
- numpy  
- matplotlib  
- seaborn  
- textblob  
- scikit-learn  

Install using:

```bash
pip install pandas numpy matplotlib seaborn textblob scikit-learn

If using Google Colab:

!pip install textblob
!python -m textblob.download_corpora

Reproducibility

Sentiment labeling logic is rule-based and deterministic.

Monthly aggregation methodology is clearly defined.

Model training uses a fixed random state for consistency.

Code is fully documented and structured for clarity.

All outputs can be reproduced from the raw dataset.

Conclusion

This project successfully:

Labeled sentiment for employee emails

Identified engagement trends

Ranked employees by monthly performance

Flagged potential flight risks

Built a predictive regression model

The framework can be extended for real-time HR analytics and employee engagement monitoring systems.

Author

Sai Likhitha Gaddam
