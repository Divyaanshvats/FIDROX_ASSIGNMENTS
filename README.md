# 🛡️ DBSCAN-Based Anomaly Detection in Swipe Access Logs

This project applies **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** to detect anomalous swipe access behavior in a simulated building environment over one month.

---

## 📌 Overview

We analyze swipe logs consisting of:
- **User ID**
- **Door ID**
- **Time of swipe (hour of day)**
- **Day of the week**
- **Swipe success/failure**

Using unsupervised learning, we aim to identify:
- Suspicious access attempts (e.g., odd hours)
- Frequent failures (e.g., cloned cards)
- Rare access to sensitive doors (e.g., server rooms)

---

## ⚙️ Methodology

1. **Preprocessing**  
   - Label Encoding for `User ID`, `Door ID`, and `Status`
   - Scaled using `MinMaxScaler`
   - Applied PCA to project features to 2D for visualization

2. **Clustering**  
   - Performed DBSCAN with multiple `(eps, min_samples)` values
   - Detected anomalies using `label = -1`
   - Calculated **Silhouette Score** for clustering evaluation

---

## ✅ Best Result

- **Best Parameters:**  
  `eps = 0.40`, `min_samples = 9`

- **Clusters Formed:** `12`
- **Silhouette Score:** `0.669`

This configuration yielded the best clustering performance and maximum anomaly separation.

### 📈 Why Silhouette Score?
The Silhouette Score measures:
- **Cohesion** within clusters
- **Separation** between clusters

A score near **1.0** implies well-defined clusters.  
**Score = 0.669** indicates strong structure with minimal overlap — ideal for anomaly detection.

---

## 🔍 Key Insights

| Anomaly Type                     | Description                                                   |
|----------------------------------|---------------------------------------------------------------|
| Odd-hour Access                  | Swipes during 2 AM – 5 AM showed isolated, suspicious patterns |
| Restricted Door Access           | Rare swipes to Server Room, Basement, Rooftop flagged         |
| Multiple Consecutive Failures    | Rapid failed attempts could indicate cloned badge usage       |
| Rapid Sequential Swipes          | Tailgating behavior or automation misuse detected             |

---

## 🚨 Real-World Applications

- 🕵️‍♀️ **Insider Threat Detection**  
  Identify users deviating from normal behavior

- 🔐 **Sensitive Zone Monitoring**  
  Detect unauthorized entry attempts to secure areas

- 📊 **Behavioral Logging & Audit**  
  Maintain reports for security and compliance

- 🔄 **Adaptive Security Policies**  
  Use unsupervised patterns to refine access control

---

**THIS WAS THE COMPLETE ANALYSIS OF DBSCAN METHOD**
