# Admitted vs Enrolled Students for Three North American Colleges – Analysis

A data-driven project to optimize college admissions and enrollment decisions using statistical modeling and machine learning.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Background and Context](#background-and-context)
- [Business Understanding](#business-understanding)
- [Dataset Description](#dataset-description)
- [Data Preparation](#data-preparation)
- [Modeling Approach](#modeling-approach)
  - [Logistic Regression Models](#logistic-regression-models)
  - [Classification and Regression Tree (CART) Models](#classification-and-regression-tree-cart-models)
- [Key Findings](#key-findings)
- [Limitations and Recommendations](#limitations-and-recommendations)
- [How to Run](#how-to-run)

---

## Project Overview

This project analyzes and models the college admissions process for three North American colleges—Arts & Letters, Business & Economics, and Math & Science. The objective is to help institutions make efficient, data-driven decisions about which applicants to admit and which admitted students are most likely to enroll, ultimately saving time and improving academic quality[1].

---

## Background and Context

Higher education institutions receive thousands of applications from students with diverse backgrounds. Efficiently filtering and selecting applicants—while also predicting which admitted students will enroll—is crucial for resource optimization and maintaining academic standards. This project supports admissions committees and enrollment management teams by providing predictive models and actionable insights[1].

---

## Business Understanding

**Business Objective:**  
Provide a data-driven strategy to optimize admissions and enrollment, making the process more efficient and helping colleges select students who are most likely to enroll and succeed.

**Stakeholders:**  
- Admissions Committee (makes final admit decisions)
- Enrollment Management (improves retention)
- Marketing & Outreach (targets high-potential applicants)

**Key Decision Factors:**  
- Parental education
- High school GPA
- SAT/ACT scores
- Gender
- Ethnicity
- College applied to[1]

---

## Dataset Description

- **Source:** McGraw Hill – Business Analytics Communication with Numbers by Sanjiv Jaggia
- **Size:** 17,339 applicants across three colleges
- **Attributes:**  
  - Demographics: Gender, Ethnicity  
  - Academic: High School GPA, SAT/ACT score, College GPA (for enrolled students)  
  - Parental Education: Two fields  
  - Application Outcomes: Admitted (Yes/No), Enrolled (Yes/No), College applied to

- **Data Quality:**  
  - College GPA is missing for non-enrolled students  
  - Some missing/undefined categories in parental education[1][2]

---

## Data Preparation

- **Selection:** Focus on relevant variables (GPA, SAT/ACT, parental education, gender, ethnicity, college)
- **Cleaning:**  
  - Addressed missing values and unexplained categories (e.g., parental education value '5')
  - Converted categorical variables to ordered/factor types
- **Splitting:**  
  - Data split into training and validation sets (typically 70/30)
  - Oversampling used for class imbalance in enrollment prediction[1][3]

---

## Modeling Approach

### Logistic Regression Models

- **Admission Prediction:**  
  - Predicts probability of being admitted using parental education, GPA, SAT/ACT, and other factors.
  - Final model: `Admitted ~ Edu_Parent1 + Edu_Parent2 + HSGPA + SAT_ACT`
  - Achieved ~81.75% accuracy, ~89% sensitivity, ~65% specificity on validation data.

- **Enrollment Prediction (among admitted students):**  
  - Predicts probability of enrollment using similar predictors, with college as an additional factor.
  - Final model: `Enrolled ~ Edu_Parent1 + Edu_Parent2 + White + HSGPA + SAT_ACT + College`
  - Achieved ~80.9% accuracy, ~20% sensitivity, ~95% specificity.

- **Model selection based on variable significance and cross-validation.**[1][3]

### Classification and Regression Tree (CART) Models

- **Admission and Enrollment Trees:**  
  - Built and pruned trees for interpretability and to avoid overfitting.
  - Evaluated accuracy, sensitivity, specificity, and ROC/AUC.
  - For admission: Pruned tree achieved ~76.8% accuracy, ~77.9% sensitivity, ~76.3% specificity.
  - For enrollment: Pruned tree achieved ~66.8% accuracy, ~64.2% sensitivity, ~69.3% specificity.

- **Visualizations:**  
  - Confusion matrices, lift charts, decile charts, ROC curves for model evaluation.
  - Bar plots for model comparison (accuracy, sensitivity, specificity)[1][3]

---

## Key Findings

- **Parental education, high school GPA, and SAT/ACT scores are the strongest predictors for both admission and enrollment.**
- **Gender and Asian ethnicity are not significant predictors in this context.**
- **Students applying to Math & Science and Business & Economics are more likely to enroll than those applying to Arts & Letters.**
- **Logistic regression outperforms CART in most scenarios, especially for admission prediction.**
- **Oversampling improves sensitivity for enrollment models but may reduce overall accuracy.**
- **Data-driven models reduce cognitive biases and support fairer, more effective admissions decisions.**[1][3]

---

## Limitations and Recommendations

- **Limitations:**
  - Dataset is from a specific institution and may not generalize to all colleges.
  - Some important factors (financial aid, application session, extracurriculars) are not included.
  - Enrollment decisions may be influenced by unmeasured variables (e.g., competing offers, financial incentives).
  - Models do not account for changing trends over time.

- **Recommendations:**
  - Incorporate additional variables (financial aid, extracurriculars, referrals) for holistic modeling.
  - Regularly update models to reflect current trends and feedback from admissions teams.
  - Develop a user-friendly interface for admissions staff to use predictive tools.
  - Implement feedback mechanisms for continuous model improvement.[1]

---

## How to Run

1. **Clone the Repository**
- git clone https://github.com/Yashtated/Admitted-Vs-Enrolled-students-for-three-North-American-Colleges---Analysis

2. **Install R and Required Packages**
- Install R and RStudio
- Install packages: `caret`, `gains`, `rpart`, `rpart.plot`, `pROC`, `caTools`, `dplyr`, `readxl`, `ROSE`, `ggplot2`
3. **Prepare Data**
- Place `College_Admissions.csv` in your working directory.
4. **Run Analysis**
- Open and execute `Project.R` in RStudio.
- Review outputs: model summaries, confusion matrices, plots, and charts.

