# 🛍️ Mall Customer Segmentation: Clustering & Dimensionality Reduction

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikitlearn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

> Segmenting 200 mall customers with **K-Means**, **Hierarchical Clustering** and **DBSCAN**, then visualising the structure with **PCA** and **t-SNE** to turn clusters into actionable marketing strategy.

---

## 📌 Project Overview

A retail mall wants to understand *who* its customers are so it can target them with the right offers. This project groups customers by **Annual Income** and **Spending Score**, compares three clustering algorithms, and translates the winning segmentation into business recommendations.

**Highlights**
- 🎯 Five clear customer segments, confirmed by two independent algorithms (adjusted Rand index **0.94**)
- 📈 Cluster count validated with the elbow method, silhouette score and Davies-Bouldin index
- 🔍 PCA and t-SNE used to explore the data in 2-D
- 💼 Segment-by-segment business recommendations

---

## 📂 Repository Contents

| File | Description |
|---|---|
| `Assignment 08 Clustering and Dimensionality Reduction.ipynb` | Full analysis: preprocessing, clustering, PCA/t-SNE, interpretation |
| `mall_customer_spend.xlsx` | Dataset: 200 customers (ID, Genre, Age, Annual Income, Spending Score) |

---

## 🧰 Tech Stack

`Python` · `pandas` · `NumPy` · `scikit-learn` · `SciPy` · `Matplotlib` · `Jupyter Notebook`

---

## 🔬 Methodology

1. **Data check:** 200 rows, no missing values; Genre encoded (Female=0, Male=1).
2. **Feature selection:** Annual Income (k$) and Spending Score (1–100).
3. **Scaling:** `StandardScaler` so both features carry equal weight.
4. **Choosing k:** Elbow method (k=1–10), supported by silhouette and Davies-Bouldin scores.
5. **Clustering:** K-Means (`n_init=10`, `random_state=42` to avoid the random-initialisation trap), Ward hierarchical clustering with a dendrogram, and DBSCAN (`eps=0.5`, `min_samples=5`).
6. **Dimensionality reduction:** PCA and t-SNE on four features (Age, Genre, Income, Spending Score).
7. **Interpretation:** Cluster profiles and business recommendations.

---

## 📊 Results

### Algorithm comparison

| Method | Clusters | Silhouette | Notes |
|---|---|---|---|
| **K-Means (k=5)** | 5 | **0.555** | Inertia 65.57; compact, easy to interpret |
| Hierarchical (Ward) | 5 | 0.554 | Matches K-Means on 196 of 200 customers |
| DBSCAN | 2 + 8 noise points | 0.388 | Merges the mid-income groups; very sensitive to `eps` |

**Why k = 5?** The silhouette score peaks at k=5 (0.555 vs 0.494 at k=4 and 0.540 at k=6) and the Davies-Bouldin score is lowest there (0.572).

### PCA vs t-SNE

- **PCA:** two components explain **59.9%** of the variance (PC1 33.7%, PC2 26.2%). PC1 is mainly Age vs Spending Score; PC2 is mainly Income and Gender.
- **t-SNE:** preserves local neighbourhoods much better (trustworthiness **0.996** vs 0.859 for PCA at 10 neighbours), making it the better tool for visualisation, while PCA suits feature extraction.

---

## 👥 Customer Segments & Recommendations

| Segment | Customers | Avg Age | Income (k$) | Spend Score | Recommended Action |
|---|---|---|---|---|---|
| 🌟 **High-Value** | 39 | 32.7 | 86.5 | 82.1 | VIP membership, early access, personalised offers |
| 💰 **Wealthy, Low-Spending** | 35 | 41.1 | 88.2 | 17.1 | Targeted campaigns and events; biggest growth opportunity |
| 🛒 **Enthusiastic Shoppers** | 22 | 25.3 | 25.7 | 79.4 | Cashback, youth promotions, affordable bundles |
| 🙂 **Average** | 81 | 42.7 | 55.3 | 49.5 | Loyalty programme, cross-selling, seasonal offers |
| 🏷️ **Budget-Conscious** | 23 | 45.2 | 26.3 | 20.9 | Coupons, value ranges, festive sales |

Gender is balanced across all segments (39–54% male), so it does not drive the grouping.

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/hasanulazad-cloud/Assignment-08-Clustering-and-Dimensionality-Reduction.git
cd Assignment-08-Clustering-and-Dimensionality-Reduction

# 2. Install dependencies
pip install pandas numpy scikit-learn scipy matplotlib openpyxl jupyter

# 3. Launch the notebook
jupyter notebook "Assignment 08 Clustering and Dimensionality Reduction.ipynb"
```

---

## 💡 Key Takeaways

- Income and spending score alone produce **five well-separated, interpretable segments**.
- Two different algorithms agreeing (K-Means and Ward) gives confidence in the result.
- DBSCAN is useful for spotting outliers, but needs careful `eps` tuning on data like this.
- A 2-D plot of four features loses over 40% of the variance, so visualisations should be read as exploratory.

---

## 👤 Author

**Hasanul H Azad**
Medical billing / RCM professional upskilling in Data Science, AI and Machine Learning
GitHub: [@hasanulazad-cloud](https://github.com/hasanulazad-cloud)

---

⭐ If you found this useful, consider starring the repo.
