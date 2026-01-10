AI-Driven AML Risk & Anomaly Detection System
📌 Problem Statement

Traditional Anti-Money Laundering (AML) systems rely heavily on static rules, leading to high false positives, poor adaptability to new fraud patterns, and limited explainability for regulators.
There is a need for an intelligent, explainable, and secure AML solution that can detect suspicious financial behavior early and support regulatory reporting.

🎯 Proposed Solution

This project implements a hybrid AML intelligence engine that combines:
1. Supervised risk prediction
2. Unsupervised anomaly detection
3. Rule-based compliance logic
4. Explainable AI (XAI)
5. Secure regulatory reporting

The system evaluates customer and transaction behavior to assign risk scores, anomaly scores, explanations, and regulatory status.


🧠 How It Works 

1. Risk Scoring Model (Random Forest)
Predicts customer risk using KYC, geography, behavior, and transaction data
Outputs a risk score (0–100) and level (LOW / MEDIUM / HIGH)

2. Anomaly Detection Model (Isolation Forest)
Detects unusual transaction behavior (velocity spikes, new receivers, abnormal volumes)
Outputs an anomaly score (0–100)

3. AML Rules Engine
Catches known laundering patterns (PEP, high-risk countries, mule accounts, smurfing)
Ensures regulatory coverage

4. Explainability Engine (SHAP)
Explains why a user was flagged
Generates human-readable reasons for compliance officers

5. Regulatory Mapping & Secure Reporting
Maps alerts to FIU-IND Grounds of Suspicion (GoS)
Sends digitally signed AML reports (HMAC-SHA256) to authorities


🛠️ Tech Stack

Python, NumPy, Pandas
Scikit-learn (Random Forest, Isolation Forest)
SHAP (Explainable AI)
Secure Webhooks (HMAC-SHA256)
