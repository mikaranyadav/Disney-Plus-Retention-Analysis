# Disney-Plus-Retention-Analysis
An end-to-end analysis of subscriber churn using Python, Scikit-learn, and Tableau.

# Disney+ SEA Subscriber Retention Analysis

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

An end-to-end data analysis project focusing on identifying, predicting, and mitigating subscriber churn for Disney+ in the Southeast Asia (SEA) market. This project leverages synthetic data, machine learning, and interactive visualization to provide actionable business insights.

---

## 📖 Table of Contents
- [1. Problem Statement](#1-problem-statement)
- [2. Project Goals](#2-project-goals)
- [3. Project Workflow](#3-project-workflow)
- [4. Data Generation & Exploration](#4-data-generation--exploration)
- [5. Data Preparation & Feature Engineering](#5-data-preparation--feature-engineering)
- [6. Predictive Modeling & Churn Drivers](#6-predictive-modeling--churn-drivers)
- [7. Interactive Dashboard Visualization](#7-interactive-dashboard-visualization)
- [8. Key Insights & Business Recommendations](#8-key-insights--business-recommendations)
- [9. How to Reproduce the Project](#9-how-to-reproduce-the-project)
- [10. Conclusion](#10-conclusion)

---

## 1. Problem Statement
In the competitive landscape of streaming services, subscriber churn significantly impacts revenue and growth. Understanding *why* and *when* customers leave is crucial for implementing effective retention strategies. This project addresses the challenge of identifying high-risk subscribers and the underlying factors driving churn for Disney+ within the Southeast Asian market.

## 2. Project Goals
- **Synthesize Realistic Data**: Create a comprehensive, synthetic dataset simulating Disney+ subscriber behavior and churn patterns in SEA.
- **Identify Churn Drivers**: Uncover the most influential factors contributing to subscriber churn using exploratory data analysis and machine learning models.
- **Predict Churn Risk**: Develop a machine learning model capable of predicting which subscribers are most likely to churn.
- **Visualize Insights**: Design an intuitive and interactive Tableau dashboard to present key metrics and actionable findings to business stakeholders.
- **Provide Actionable Recommendations**: Formulate data-driven strategies for improving subscriber retention.

## 3. Project Workflow
The project followed a standard data science lifecycle:
1.  **Data Generation** (`01-Data-Generation.ipynb`): Created a synthetic dataset of 5,000 subscribers with diverse attributes (age, country, plan type, watch hours, tenure, churn status). This involved embedding realistic churn logic.
2.  **Data Cleaning & Preparation** (`02-Data-Preparation.ipynb`): Loaded the generated data, performed initial sanity checks, feature engineering (e.g., `age_group`), and one-hot encoding for categorical variables to prepare the dataset for machine learning.
3.  **Exploratory Data Analysis (EDA)** (Integrated into `02-Data-Preparation.ipynb`): Visualized key relationships, such as churn rate versus tenure and watch hours, to confirm initial hypotheses about churn behavior.
4.  **Predictive Modeling** (`03-Modeling.ipynb`): Trained and evaluated Logistic Regression and Decision Tree Classifier models. The Decision Tree was chosen for its interpretability in identifying key churn drivers.
5.  **Dashboard Visualization**: Designed and built an interactive dashboard in Tableau Public to present findings in a clear, business-friendly format.

## 4. Data Generation & Exploration
The dataset was simulated to include typical subscriber demographics and engagement metrics. Key simulated behaviors contributing to churn included:
- **Higher churn for new subscribers** (especially within the first 3 months).
- **Higher churn for low-engagement users** (e.g., fewer than 5 watch hours per week).
- **Slightly higher churn for basic plan users**.

The generated data allowed for realistic patterns to be discovered and analyzed.

## 5. Data Preparation & Feature Engineering
The raw data underwent the following transformations:
- **Handling Categorical Data**: `country`, `plan_type`, and a newly engineered `age_group` feature were one-hot encoded for machine learning compatibility.
- **Feature Engineering**: An `age_group` category was created from the `age` column to identify patterns across age brackets.
- **Irrelevant Columns Dropped**: `user_id`, `subscription_date`, and the original `age` column were removed.

## 6. Predictive Modeling & Churn Drivers
A **Decision Tree Classifier** (`max_depth=5`) was used for its interpretability, which is vital for providing actionable business recommendations. The model achieved a strong accuracy in predicting churn on the test set.

The most significant factors influencing subscriber churn were identified:

| Feature                | Importance |
| :--------------------- | :--------- |
| `tenure_months`        | 0.615      |
| `watch_hours_per_week` | 0.310      |
| `country_Philippines`  | 0.019      |
| `plan_type_Standard`   | 0.015      |
| `plan_type_Premium`    | 0.012      |
| `age_group_26-35`      | 0.010      |

**Key Finding**: `tenure_months` and `watch_hours_per_week` collectively account for over 92% of the model's predictive power, highlighting their critical role in subscriber retention.

## 7. Interactive Dashboard Visualization
The final insights are presented through a comprehensive and interactive Tableau Public dashboard, designed with a Disney+ inspired color palette.

**Key Dashboard Components:**
- **Overall Churn Rate KPI**: A prominent display of the total churn percentage.
- **Churn by Tenure**: A bar chart demonstrating the high churn rates in early subscription months.
- **Churn by Country**: A geo-map visualizing churn hotspots across SEA.
- **Churn by Watch Hours**: A bar chart showing the correlation between low engagement and higher churn.
- **Churn by Plan Type**: An analysis of churn rates across 'Basic', 'Standard', and 'Premium' plans.

**[➡️ View the Interactive Dashboard on Tableau Public]([https://public.tableau.com/views/DisneySEA/Dashboard1])**

![Final Disney+ Churn Dashboard Screenshot](**[Disney+ SEA _ Tableau Public - Screenshot]**)

## 8. Key Insights & Business Recommendations
Based on the analysis and model findings, the following recommendations are crucial for Disney+ SEA:

1.  **Strengthen Onboarding & Early Retention Programs**: Given `tenure_months` is the primary churn driver, focus resources on the first 1-3 months of a subscriber's journey.
  * **Recommendation**: Implement personalized welcome series, curated content recommendations for new users, or exclusive offers after the first month to encourage continued engagement and commitment.
2.  **Drive Content Engagement**: As `watch_hours_per_week` is the second-most critical factor, promoting active viewing is essential.
  * **Recommendation**: Develop targeted re-engagement campaigns (e.g., push notifications for recently added shows, email digests of personalized recommendations) for users showing signs of low watch activity.
3.  **Evaluate Basic Plan Value Proposition**: The 'Basic' plan exhibits a slightly higher churn rate.
  * **Recommendation**: Conduct user experience research for Basic plan subscribers. Consider A/B testing different features or upgrade incentives for these users.
4.  **Localized Retention Efforts**: While less impactful, `country` does play a minor role.
  * **Recommendation**: Investigate specific market dynamics in countries with higher churn rates (e.g., Philippines, Vietnam) to understand local preferences or competitive pressures.

## 9. How to Reproduce the Project
To run this project locally:
1.  **Clone the Repository**:
  ```bash
  git clone [https://github.com/](https://github.com/)[YOUR_GITHUB_USERNAME_HERE]/Disney-Plus-Retention-Analysis.git
  cd Disney-Plus-Retention-Analysis
  ```
2.  **Install Dependencies**: Ensure you have Python installed. The core libraries used are `pandas`, `numpy`, `faker`, `scikit-learn`, `matplotlib`, and `seaborn`.
  ```bash
  pip install pandas numpy faker scikit-learn matplotlib seaborn jupyter
  ```
3.  **Run Jupyter Notebooks**: Open the project in Jupyter and execute the notebooks sequentially:
  * `01-Data-Generation.ipynb` (to create the raw data)
  * `02-Data-Preparation.ipynb` (to clean and preprocess data, producing `disney_plus_prepared_for_modeling.csv`)
  * `03-Modeling.ipynb` (to train models and identify churn drivers)
4.  **View Dashboard**: The Tableau dashboard can be accessed directly via the [Tableau Public link](#7-interactive-dashboard-visualization). To edit or view the raw Tableau workbook, download it from Tableau Public.

## 10. Conclusion
This project successfully demonstrates an end-to-end approach to solving a critical business problem – subscriber churn. By combining synthetic data generation, robust analytical techniques, predictive modeling, and effective visualization, actionable insights and strategies were delivered to enhance Disney+'s subscriber retention in Southeast Asia. This showcases proficiency in data manipulation, machine learning, and data storytelling.

---  
