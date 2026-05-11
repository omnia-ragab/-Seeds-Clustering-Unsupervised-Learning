#  Seeds Clustering — Unsupervised Learning

> Discovering natural groupings in wheat seed varieties using K-Means and Agglomerative Hierarchical Clustering, without using class labels during training.

---

##  Project Overview

This project applies **unsupervised machine learning** to cluster wheat seeds into groups based on physical measurements. The dataset is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/236/seeds) and contains 3 varieties of wheat: **Kama**, **Rosa**, and **Canadian**.

The class labels are intentionally hidden during clustering and only used at the end for **evaluation purposes** (ARI score), making this a true unsupervised learning exercise.

| Detail | Info |
|---|---|
| **Task** | Unsupervised Clustering |
| **Dataset** | Seeds Dataset (UCI) |
| **Samples** | 210 seeds |
| **Features** | 7 physical measurements |
| **True Classes** | 3 wheat varieties (Kama, Rosa, Canadian) |

---

##  Repository Structure

```
seeds-clustering/
│
├── Seeds_Clustering_Notebook.ipynb   # Main notebook
└── README.md
```

> The dataset is loaded directly from the UCI repository URL — no local CSV needed.

---

##  Methodology

### Phase 1: Exploratory Data Analysis
- Loaded dataset from [UCI Repository](https://archive.ics.uci.edu/ml/machine-learning-databases/00236/seeds_dataset.txt)
- Verified class balance — **70 samples per variety** (perfectly balanced)
- Checked for missing values and duplicates — **none found**
- Visualized feature distributions per variety using histograms
- Built a **correlation heatmap** — Area, Perimeter, and Kernel Length are highly correlated (>0.9)
- Generated pairplots for key features

### Phase 2: Preprocessing
- Separated features from ground-truth labels (labels hidden from models)
- Detected outliers using the IQR method — **very few outliers**, dataset is clean

### Phase 3: Clustering Algorithms

| # | Algorithm | Configuration |
|---|---|---|
| 1 | **K-Means** | `K=3`, `n_init=10`, `max_iter=300` |
| 2 | **Agglomerative Hierarchical** | `n_clusters=3`, `linkage='ward'` |

**Optimal K selection** was done using:
-  **Elbow Method** (Inertia / WCSS)
-  **Silhouette Score** — both confirmed K=3

**Dimensionality Reduction** via PCA (2 components) for cluster visualization.

---

##  Features

| Feature | Description |
|---|---|
| `Area` | Seed surface area |
| `Perimeter` | Seed perimeter |
| `Compactness` | Compactness ratio (4π × Area / Perimeter²) |
| `Kernel_Length` | Length of the kernel |
| `Kernel_Width` | Width of the kernel |
| `Asymmetry_Coefficient` | Asymmetry of the kernel |
| `Kernel_Groove_Length` | Length of the kernel groove |

---

##  Evaluation Metrics

Since this is unsupervised learning, multiple metrics were used:

| Metric | Direction | Meaning |
|---|---|---|
| **Silhouette Score** | ↑ Higher = Better | Cluster cohesion & separation |
| **Davies-Bouldin Index** | ↓ Lower = Better | Average similarity between clusters |
| **Calinski-Harabasz Score** | ↑ Higher = Better | Ratio of between-cluster to within-cluster dispersion |
| **Adjusted Rand Index (ARI)** | ↑ Closer to 1 = Better | Agreement with ground-truth labels |

---

##  Key Insights

- Both algorithms successfully recovered the **3 natural wheat variety clusters**
-  **Rosa** wheat has the **largest area and perimeter**
-  **Canadian** wheat has the **smallest area and perimeter**
-  **Kama** wheat has the **highest compactness**
-  PCA captures **72%+ of total variance** in just 2 components
-  **K-Means** outperformed Agglomerative Clustering on the majority of metrics

---

##  Technologies

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![Scipy](https://img.shields.io/badge/SciPy-Scientific-lightblue?logo=scipy)

```
pandas | numpy | matplotlib | seaborn | warnings
sklearn (KMeans, AgglomerativeClustering, PCA, silhouette_score, ARI, DB, CH)
scipy (dendrogram, linkage)
```

---

##  Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/seeds-clustering.git
   cd seeds-clustering
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
   ```

3. **Run the notebook**
   ```bash
   jupyter notebook Seeds_Clustering_Notebook.ipynb
   ```

>  The dataset is fetched automatically from the UCI URL — no manual download required.

---

##  Dataset Source

- **Repository:** UCI Machine Learning Repository
- **Dataset:** [Seeds Dataset](https://archive.ics.uci.edu/dataset/236/seeds)
- **Authors:** M. Charytanowicz, J. Niewczas, P. Kulczycki, P.A. Kowalski, S. Lukasik, S. Zak
- **License:** Public / Educational use
