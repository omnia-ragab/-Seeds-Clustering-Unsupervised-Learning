# 📱 Mobile Price Classification

> Predicting mobile phone price ranges using supervised machine learning algorithms based on hardware specifications.

---

## 📌 Project Overview

This project applies **supervised machine learning** to classify mobile phones into one of four price categories based on their technical specifications. The dataset is sourced from [Kaggle's Mobile Price Classification](https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification).

| Detail | Info |
|---|---|
| **Task** | Multi-class Classification |
| **Target** | `price_range` (4 classes) |
| **Training Samples** | 2,000 phones |
| **Test Samples** | 1,000 phones |
| **Features** | 22 hardware specifications |

### Price Range Classes

| Class | Label |
|---|---|
| 0 | 💰 Budget |
| 1 | 📱 Low-Mid |
| 2 | 📲 High-Mid |
| 3 | 💎 Premium |

---

## 📂 Repository Structure

```
mobile-price-classification/
│
├── Mobile_Price_Classification.ipynb   # Main notebook
├── data/
│   ├── train.csv                        # Labeled training data
│   └── test.csv                         # Unlabeled test data
└── README.md
```

---

## 🔬 Methodology

### Phase 1: Data Preparation
- Loaded and explored training (2000 rows) and test (1000 rows) datasets
- Verified data integrity — **no missing values** found in either set
- Analyzed target distribution — **perfectly balanced** dataset (500 samples per class)
- Visualized feature distributions using boxplots to detect outliers
- Split features (`X`) from target (`y`) for model training

### Phase 2: Modeling & Evaluation

Three classification algorithms were trained on an **80/20 stratified split**:

| # | Algorithm | Description |
|---|---|---|
| 1 | **Logistic Regression** | Linear probabilistic classifier (`C=1.0`, `max_iter=1000`) |
| 2 | **Random Forest** | Ensemble of 200 decision trees (`n_estimators=200`) |
| 3 | **Gradient Boosting** | Sequential ensemble (`n_estimators=200`, `lr=0.1`, `max_depth=4`) |

---

## 📊 Features Used

| Feature | Description |
|---|---|
| `battery_power` | Total energy capacity (mAh) |
| `ram` | RAM size (MB) |
| `px_height` / `px_width` | Pixel resolution |
| `clock_speed` | Processor speed (GHz) |
| `int_memory` | Internal storage (GB) |
| `fc` / `pc` | Front / Primary camera (MP) |
| `n_cores` | Number of processor cores |
| `sc_h` / `sc_w` | Screen height / width (cm) |
| `mobile_wt` | Device weight |
| `talk_time` | Battery life during calls |
| `m_dep` | Mobile depth (cm) |
| + others | Binary features (4G, 3G, Bluetooth, WiFi, etc.) |

---

## 🛠️ Technologies

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data-green?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Viz-red)
![Seaborn](https://img.shields.io/badge/Seaborn-Viz-purple)

```
pandas | numpy | matplotlib | seaborn
sklearn (LogisticRegression, RandomForestClassifier, GradientBoostingClassifier)
```

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/mobile-price-classification.git
   cd mobile-price-classification
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. **Run the notebook**
   ```bash
   jupyter notebook Mobile_Price_Classification.ipynb
   ```

> 💡 The notebook can also be run directly on [Google Colab](https://colab.research.google.com/) — just upload the CSV files to `/content/sample_data/`.

---

## 📈 Results

Models were evaluated on a held-out **20% validation set** using accuracy score and full classification reports (precision, recall, F1 per class).

> See the notebook for full confusion matrices, classification reports, and a visual model comparison chart.

---

## 📋 Dataset Source

- **Platform:** Kaggle
- **Dataset:** [Mobile Price Classification](https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification)
- **License:** Public / Educational use
