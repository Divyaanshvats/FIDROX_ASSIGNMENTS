### 📌 DBSCAN-Based Anomaly Detection – Final Report

#### 🔍 Methodology
We used DBSCAN (Density-Based Spatial Clustering) to detect unusual access patterns from swipe log data. Features included:
- Encoded User ID and Door ID
- Hour of swipe
- Day of the week
- Whether access was successful or failed

DBSCAN works by identifying data points that are far from dense clusters (anomalies are labeled `-1`).

#### 📈 Insights from Data
- **Odd-hour accesses** (e.g., 2 AM, 4 AM) were flagged as suspicious.
- Users accessing **restricted or rarely used doors** frequently (e.g., Server Room, Rooftop) stood out.
- Repeated **failures in short bursts** were detected — potentially cloned badges or unauthorized attempts.

#### 🚨 Key Anomalies Detected
- Several users showed swipe attempts outside normal working hours.
- Access failures clustered around the Server Room and Basement Storage.
- Users trying multiple times rapidly were flagged as potential tailgating cases.

#### 🛡️ Real-World Recommendations
- Use this model for **insider threat detection** — flag users accessing sensitive areas at odd hours.
- Improve **access policies** for rarely used or sensitive doors by monitoring anomaly trends.
- Support **compliance audits** with automated logging and alerts from DBSCAN.

> DBSCAN is unsupervised and adaptive — making it useful even when labeled threat data is not available.
