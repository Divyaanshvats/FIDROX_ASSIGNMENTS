
# AccessAI – K-Means Clustering for Anomalous Swipe Behavior

This notebook is part of the **AccessAI project**, which focuses on detecting unusual access patterns in physical access control systems using unsupervised learning.

This specific module implements **K-Means Clustering**, from start to finish, to group behavioral patterns and highlight outliers in swipe access logs.

---

## 🚀 Objective

To apply the K-Means clustering algorithm on swipe access data, visualize user behavior, tune the model for optimal performance, and identify anomalous access patterns.

---

## 🧮 Process Overview

### 1. **Data Preprocessing**
- Normalized the dataset using `StandardScaler` to ensure all features contribute equally to distance-based clustering.
- Engineered time-based and access-related features (e.g., Hour, Result, DoorName, Direction).

---

### 2. **K-Means Clustering**
- **Tuned number of clusters (K)** using:
  - **Elbow Method** (plots Sum of Squared Errors)
  - **Silhouette Score** (measures cluster cohesion and separation)

---

### 3. **Final K-Means Model**
- Fitted the best K-Means model on scaled features.
- Stored `labels_kmeans` for each data point.
- Used PCA for 2D projection and visualized clusters in reduced space.

---

### 4. **Visualizations**
- **PCA scatter plot** for 2D cluster visualization.
- **Bar Chart**: Failed swipe attempts per door.
- **Heatmap**: Frequency of failed swipes by hour and door.

---

### 5. **Anomaly Scoring in K-Means**
- Defined an **anomaly score** based on distance from cluster centroids.
- Top 5% farthest points flagged as potential anomalies.

---

### 6. **Cluster-Level Summary**
- Computed for each cluster:
  - Cluster size
  - Number of failed swipes
  - Anomaly count and percentage
- Visualized using a bar chart (failure rate vs anomaly rate).

---

### 📌 Observations

Many of the **K-Means outliers** aligned with **failed swipe attempts** or **odd access hours**.  
This suggests that distance-based anomalies are not just mathematical outliers — they represent **behaviorally suspicious patterns**, aligning well with potential security risks.

---

## 🔍 Techniques Used (K-Means Specific)

| Technique             | Purpose                                       |
|----------------------|-----------------------------------------------|
| StandardScaler        | Normalize feature distributions               |
| Elbow Method          | Estimate ideal number of clusters (K)         |
| Silhouette Score      | Evaluate clustering quality                   |
| PCA                   | Visualize high-dimensional data in 2D         |
| Distance-based anomaly scoring | Identify outliers via centroid distance   |
| Cluster analytics     | Understand behavioral composition per group   |

---

## 📊 DBSCAN vs. K-Means Comparison

| Feature                  | DBSCAN                                | K-Means                               |
|--------------------------|----------------------------------------|----------------------------------------|
| Type                     | Density-based clustering               | Centroid-based clustering              |
| Number of clusters       | Automatically determined              | Requires manual tuning (K)             |
| Handles noise            | ✅ Yes, marks as -1                    | ❌ No, forces every point into a cluster|
| Shape of clusters        | Arbitrary shapes                       | Assumes spherical clusters             |
| Anomaly detection        | Built-in (noise points)                | Distance from centroid (custom scoring)|
| Parameter tuning         | eps and min_samples                    | Optimal K (via elbow/silhouette)       |
| Performance on sparse data | Strong                               | Can miscluster                         |
| PCA visualization used   | ✅ Yes                                 | ✅ Yes                                  |
| Silhouette Score used    | ✅ Yes                                 | ✅ Yes                                  |
| Failed attempts aligned  | ✅ Clearly in noise clusters           | ✅ Outliers correlated via score ranking|

---

## 🤔 Which is Better? – K-Means vs DBSCAN

Both algorithms provided valuable insights. However:

- **DBSCAN** was better at identifying isolated anomalies (noise points), especially in sparse regions.
- **K-Means** excelled at categorizing user behaviors into coherent clusters, and its distance-based anomaly score correlated surprisingly well with real-world failures.

### ✅ Conclusion:
> Use **DBSCAN** for pure anomaly detection, especially when outliers are the main focus.  
> Use **K-Means** when you want to understand behavior patterns across users, identify outliers, and summarize cluster-level insights — as required in AccessAI.

---

## 💼 Real-World Use Case of K-Means (Based on Our Analysis)

In access control systems like those in corporate offices or datacenters, **K-Means** can be used to:

- Group users by entry/exit timing, door usage, and swipe behavior
- Flag users whose access patterns differ sharply from their assigned group
- Monitor clusters for abnormal increases in failure rates or time-of-day access
- Support policy adjustments, such as redefining access hours or flagging badge misuse

Thus, K-Means is highly useful for **behavioral access analytics**, **internal threat detection**, and **security audits**.

---

## 💡 Suggestions for Future Work

✅ Integrate additional anomaly detection algorithms like:
- Isolation Forest
- One-Class SVM

✅ Develop interactive dashboards with Streamlit or Dash for real-time behavioral monitoring.

✅ Enhance dataset with features such as:
- UserRole (e.g., Staff, Admin)
- DayOfWeek
- Swipe Duration or Sequence Patterns

✅ Implement anomaly ranking with explainability, using SHAP, LIME, or distance heatmaps.

---

## 🛠️ Tools and Libraries

- **Python**
- `pandas`, `numpy` – Data manipulation
- `scikit-learn` – Clustering & evaluation
- `matplotlib`, `seaborn` – Visualization

---


