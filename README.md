🚨 Anomaly Detection in User Activity using Unsupervised Machine Learning
📌 Overview

Modern digital platforms often fail not because of average user behavior, but due to abnormal patterns such as fraud, bots, account takeovers, sudden disengagement, or system bugs.

This project builds an unsupervised anomaly detection system that identifies abnormal user activity patterns from behavioral logs — without relying on labeled data.

🎯 Problem Statement

Detect users or time periods exhibiting unusual activity patterns that significantly deviate from normal behavior, using only historical usage data.

Key challenges:

No ground-truth labels available

Anomalies are rare and diverse

Behavior evolves over time

💡 Solution Approach

We model normal user behavior and flag deviations using Isolation Forest, an unsupervised anomaly detection algorithm well-suited for high-dimensional behavioral data.

The system:

Learns normal activity patterns

Assigns an anomaly score to each user-day

Flags high-risk behavior

Explains why a user was flagged

📊 Dataset
Data Type

Synthetic but realistic user activity data, designed to mimic real-world platform logs.

Granularity

Row: User × Day

Users: 500

Days: 30

Total rows: ~15,000

Key Features
Feature	Description
sessions_count	Number of sessions per day
actions_count	Total actions performed
avg_session_duration	Mean session duration
night_activity_ratio	Fraction of activity between 12am–6am
avg_time_between_sessions	Average gap between sessions
inactivity_hours	Hours of inactivity in a day

⚠️ Anomalies were injected into ~6% of users for validation only. Labels were not used during training.

🔍 Feature Engineering

Behavioral features were designed to capture:

Volume anomalies (spikes/drops)

Temporal anomalies (night-time usage)

Consistency anomalies (erratic behavior)

Engagement drop-offs

All features were standardized prior to modeling.

🤖 Model
Algorithm

Isolation Forest

Why Isolation Forest?

Works well without labels

Efficient on large datasets

Explicitly models anomaly isolation

Produces interpretable anomaly scores

Configuration

n_estimators = 200

contamination ≈ 0.06 (expected anomaly ratio)

📈 Outputs

Anomaly Score (continuous)

Anomaly Flag (Normal / Anomalous)

Severity Levels:

High

Medium

Low

Lower scores indicate higher abnormality.

🔎 Explainability

To explain flagged anomalies:

Normal behavior baselines were computed

Feature-wise deviations (z-scores) were calculated

Top contributing features were identified per user

This allows insights such as:

“User flagged due to unusually high session volume and abnormal night-time activity over multiple days.”

📊 Visualizations

Anomaly score distributions

User-level anomaly timelines

Normal vs anomalous behavior comparisons

These help validate model behavior and support human decision-making.

🧠 Use Cases

Fraud & account takeover detection

Bot and scraper detection

SaaS user health monitoring

Employee system misuse

Early detection of system or feature failures

⚠️ Limitations

Synthetic data (real-world deployment would require live logs)

Isolation Forest does not provide native SHAP values

Threshold tuning depends on business risk tolerance

🚀 Future Improvements

Compare with LOF and Autoencoders

Real-time streaming anomaly detection

Alerting system with escalation rules

Deployment using Streamlit or FastAPI

Concept drift monitoring

🧩 Tech Stack

Python

Pandas, NumPy

Scikit-learn

Matplotlib

📎 Key Takeaway

This project demonstrates system-level ML thinking:

Unsupervised learning

Behavioral modeling

Explainability

Real-world anomaly detection design
