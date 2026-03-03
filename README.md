1. Project Overview

This project builds a full CRM analytical pipeline using a Netflix customer dataset.

We move from raw customer data to:

• Behavioral segmentation
• Churn prediction
• Risk scoring
• Marketing action prioritization

The objective is to support data-driven retention strategy.

2. Dataset

Source: Kaggle – Netflix Customer Churn Dataset

The dataset contains 5,000 customers and 14 variables including:

• Age
• Watch hours
• Average watch time per day
• Last login days
• Monthly fee
• Number of profiles
• Churned (target variable)

The dataset contains no missing values and no duplicates.

3. Data Cleaning

We performed the following checks:

• Missing value detection
• Duplicate record validation
• Data type verification

The dataset required no imputation or structural correction.

4. Customer Segmentation

We applied RFM-based behavioral segmentation.

Recency: last_login_days
Frequency: watch_hours, avg_watch_time_per_day
Monetary: monthly_fee

4.1 Standardization

We scaled variables using StandardScaler to normalize distance calculations.

4.2 Elbow Method

We evaluated inertia for k from 2 to 10.

The optimal number of clusters is k = 6.

4.3 KMeans Clustering

We applied KMeans with 6 clusters.

Each customer was assigned to one of six behavioral segments.

5. Segment Profiling

We computed per-segment metrics:

• Number of customers
• Churn rate
• Average watch hours
• Average watch time per day
• ARPU
• Average churn score

Key Insights

• Segments 0, 1, and 5 show high churn above 60 percent
• Segment 3 and 4 show near zero churn
• Engagement strongly correlates with retention

6. Churn Prediction Model

We built a Logistic Regression model.

6.1 Target Variable

y = churned

6.2 Features

• Age
• Watch hours
• Avg watch time per day
• Last login days
• Monthly fee
• Number of profiles

6.3 Train/Test Split

70 percent training
30 percent testing

6.4 Model Performance

Accuracy: 0.889
Precision and recall balanced across classes

The model predicts churn probability for each customer.

7. Churn Scoring

We generated churn_score using predict_proba.

Each customer receives a score between 0 and 1.

We classified risk levels:

Low: 0–0.3
Medium: 0.3–0.6
High: 0.6–1

8. Business KPIs

Overall churn rate: 0.503
Retention rate: 0.497
Average monthly revenue per user: 13.68

These metrics provide business context for risk prioritization.

9. Marketing Strategy: Score × Value Framework

We combined churn risk with customer value (monthly_fee).

Value levels:
Low: 0–12
Mid: 12–15
High: 15+

Action Rules

Priority 1 Retention
High risk + Mid/High value

Low-cost Retention
High risk + Low value

Upsell
Low risk + High value

Monitor
Remaining customers

Action Distribution

Priority 1 Retention: 1,414
Low-cost Retention: 980
Upsell: 842
Monitor: 1,764

This ensures marketing resources focus on high-risk high-value customers.

10. Conclusion

This project demonstrates a full CRM workflow:

Data cleaning
Behavioral segmentation
Predictive modeling
Risk scoring
Strategic marketing allocation

We convert customer data into actionable retention strategy.
