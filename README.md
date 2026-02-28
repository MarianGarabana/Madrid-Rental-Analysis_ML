# Madrid Rental Housing Analysis
**Machine Learning I — MBDS Group Assignment**

> End-to-end ML pipeline applied to 2,100 rental property listings from [idealista.com](https://idealista.com), covering EDA, segmentation, association analysis, and regression modeling.

---

## Project Overview

We analyzed a real-world Madrid housing rental dataset to:
1. **Segment** properties into meaningful clusters based on structural characteristics
2. **Run association analysis** to find co-occurring property features
3. **Model rental price** using both Linear Regression and Logistic Regression (classification of High Rent ≥ €1,800/month)

---

## Repository Structure

```
📁 madrid-rental-analysis/
│
├── 📓 EDA_Group_Assignment_Formatted.ipynb          # Exploratory Data Analysis & data cleaning
├── 📓 Phase1_Phase2_Segmentation_Association_0225.ipynb  # K-Means clustering + Apriori association rules
├── 📓 Phase3_Linear_Regression_0225.ipynb           # OLS Linear Regression to predict rent (€)
├── 📓 Phase4_Logit_Regression_0225.ipynb            # Logistic Regression to classify High Rent (≥€1,800)
│
├── 📄 ML_Report_v3.docx                             # Final report (addressed to Real Estate agency)
├── 📄 Group_Assignment_Instructions_2026.pdf         # Original assignment brief
│
└── README.md
```

> ⚠️ **Note:** The dataset file (`Houses_for_rent_in_Madrid.xlsx`) is **not included** in this repo due to data source restrictions. See the Data section below.

---

## Methodology

### Phase 0 — EDA & Cleaning
- 2,100 properties → **2,089 after cleaning**
- Handled missing values, outliers, and created derived features (e.g., Price/m²)

### Phase 1 — Segmentation (K-Means)
- Clustered on **5 structural variables**: Sq.Mt, Bedrooms, Floor, Is_Special, Outer
- Profiled clusters across all remaining variables (rent, district, elevator, etc.)
- Applied **"lean clustering, rich profiling"** methodology: cluster on structure, profile on everything

### Phase 2 — Association Analysis (Apriori)
- Discovered co-occurring property features within key segments
- Evaluated rules by Support, Confidence, and Lift

### Phase 3 — Linear Regression (OLS)
- Target: **monthly rent (€)**
- Feature selection via **VIF** (multicollinearity removal) + iterative refinement
- Used `statsmodels` for interpretability (p-values, confidence intervals)
- Validated with train/test split

### Phase 4 — Logistic Regression
- Target: **High Rent** (1 if Rent ≥ €1,800, else 0)
- Feature selection via **LASSO + RFECV**
- Evaluated with confusion matrix, ROC-AUC, precision, recall
- Used `sklearn` for classification performance

---

## Tech Stack

| Library | Purpose |
|---|---|
| `pandas`, `numpy` | Data manipulation |
| `sklearn` | Clustering, Logit, train/test split, RFECV |
| `statsmodels` | OLS Linear Regression (interpretation) |
| `matplotlib`, `seaborn` | Visualization |
| `mlxtend` | Apriori association rules |

---

## Data

**Source:** idealista.com (scraped, anonymized)  
**Size:** 2,100 listings → 2,089 after cleaning  
**Key variables:** Rent (€), Sq.Mt, Bedrooms, Bathrooms, Floor, District, Elevator, Parking, and more.

The raw dataset is **not included** in this repository. To reproduce results, place `Houses_for_rent_in_Madrid.xlsx` in the root directory before running the notebooks in order.

---

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/madrid-rental-analysis.git
cd madrid-rental-analysis

# 2. Install dependencies
pip install pandas numpy scikit-learn statsmodels matplotlib seaborn mlxtend openpyxl jupyter

# 3. Add the dataset to the root folder
# Place Houses_for_rent_in_Madrid.xlsx here

# 4. Run notebooks in order
jupyter notebook
```

Run in this order:
1. `EDA_Group_Assignment_Formatted.ipynb` → produces `HousesMadridClean.xlsx`
2. `Phase1_Phase2_Segmentation_Association_0225.ipynb` → produces `Madrid_Rental_Segmented.xlsx`
3. `Phase3_Linear_Regression_0225.ipynb`
4. `Phase4_Logit_Regression_0225.ipynb`

---

## Key Findings

- Segmentation revealed distinct property clusters (e.g., compact urban flats vs. large premium properties)
- Linear Regression achieved strong explanatory power for mid-range properties
- Logistic model successfully classifies High Rent properties with good AUC performance
- Key drivers of high rent: surface area, district, floor level, and premium features (parking, elevator)

---

## Authors

MBDS 2026 — Machine Learning I Group Assignment  
*IE School of Human Sciences & Technology*
