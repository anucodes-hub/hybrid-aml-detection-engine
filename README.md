# 🛡️ Explainable KYC & AML Risk Intelligence System (Prototype)

An **end-to-end, explainable KYC & AML risk analysis prototype** that combines **machine learning, rule-based intelligence, anomaly detection, and secure regulatory reporting** to assess customer and transaction risk in real time.

This system is designed to reflect **real-world FinTech compliance workflows**, prioritizing **explainability, auditability, and security by design**.

---

## 📌 Key Capabilities

* **Customer & Transaction Risk Scoring** using supervised and unsupervised ML
* **Explainable AI (XAI)** for transparent risk decisions
* **Hybrid AML Intelligence** (Rules + ML + Anomaly Detection)
* **Regulatory-aware decision mapping** (STR priorities & GoS tags)
* **Secure webhook reporting** with cryptographic signatures

---

## 🧠 System Architecture Overview

### 1️⃣ Synthetic AML/KYC Dataset Generator

* Generates realistic customer and transaction profiles
* Includes KYC, behavioral, geographic, receiver, and channel risk features
* Models class imbalance and noisy labels common in AML data

---

### 2️⃣ ML-Based Risk Classification (Random Forest)

* Predicts **probability of high-risk customers**
* Hyperparameter-tuned using `RandomizedSearchCV`
* Handles class imbalance using weighted sampling

**Model Performance:**

* **Accuracy:** ~85%
* **ROC-AUC:** ~0.87
* **Weighted F1-Score:** ~0.84

> Metrics are reported with awareness of minority-class (high-risk) recall trade-offs.

---

### 3️⃣ Anomaly Detection (Isolation Forest)

* Detects unusual transactional behavior not captured by rules
* Produces a normalized **anomaly score (0–100)** with severity levels:

  * NORMAL
  * ELEVATED
  * HIGH

---

### 4️⃣ AML Rule Engine

Implements compliance-style rules such as:

* High-risk jurisdictions & corridors
* PEP involvement
* Velocity / structuring detection
* New account burst behavior
* Poor KYC quality indicators

Outputs:

* **Rule score (0–100)**
* **Rule risk level (LOW / MEDIUM / HIGH)**

---

### 5️⃣ Explainability with SHAP

* Uses **SHAP TreeExplainer** for:

  * Feature-level contribution analysis
  * Human-readable explanations (“Why was this flagged?”)
* Supports:

  * Main effects
  * Feature interactions (advanced mode)

This ensures **no black-box decisions**.

---

### 6️⃣ Unified Risk Decision Engine

Combines:

* ML risk score
* Anomaly score
* Rule score

Maps them to **regulatory-style outcomes**, such as:

* `ACCEPTED`
* `MANUAL_REVIEW`
* `STR_P2 (High ML Suspicion)`
* `STR_P1 (Urgent Terror Financing)`

Also derives **Grounds of Suspicion (GoS)** tags aligned with FIU-IND-style reporting.

---

### 7️⃣ Secure Regulatory Reporting

* Generates **digitally signed AML reports**
* Uses **HMAC-SHA256** signatures to prevent tampering
* Sends authenticated intelligence to regulator endpoints via webhook

> This simulates enterprise-grade compliance reporting pipelines.

---

## 🛠️ Tech Stack

* **Language:** Python
* **ML:** Scikit-learn (Random Forest, Isolation Forest)
* **Explainability:** SHAP
* **Data:** NumPy, Pandas
* **Security:** HMAC-SHA256, OAuth-style headers
* **Integration:** REST-style webhook communication

---

## 📊 Example Output (Compact API)

```json
{
  "risk_score": 65,
  "anomaly_score": 150,
  "rule_score": 100,
  "risk_level": "MEDIUM",
  "anomaly_level": "HIGH",
  "rule_level": "HIGH",
  "explanation": "Risk is strongly driven by high country risk and PEP involvement.",
  "status": "STR_P1",
  "priority": "URGENT_TERROR_FINANCING"
}
```

---

## 🚀 How to Run

1. Install dependencies:

```bash
pip install numpy pandas scikit-learn shap requests
```

2. Run the notebook or Python script:

```bash
python main.py
```

3. Review:

* Model performance metrics
* Risk explanations
* Secure webhook delivery logs

---

## ⚠️ Disclaimer

This project is a **prototype for educational, research, and hackathon use**.
It is **not a certified AML/KYC solution** and should not be deployed in production without regulatory validation.

---

## 👩‍💻 Author

**Anushka Kar**
Electronics & Telecommunication Engineering Student

---

## 🔮 Future Enhancements

* Threshold optimization to improve minority-class recall
* Real transaction data integration
* Streaming inference (Kafka / PubSub)
* Model retraining via analyst feedback loops
* Full dashboard & case management UI

---
