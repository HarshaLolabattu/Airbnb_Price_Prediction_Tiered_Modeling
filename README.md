# Airbnb Price Prediction — Tiered Market Modeling  
### Assignment 4 — Machine Learning & Cross-Market Transfer Analysis

---

## 1. Project Description

This project investigates how pricing models perform when applied to Airbnb listings across markets of differing sizes.  
We evaluate model accuracy city-by-city, by tier, and cross-tier generalization.

The assignment required:

✔ Data acquisition  
✔ Feature engineering  
✔ Per-city modeling  
✔ Tier-based model learning  
✔ Cross-tier transfer evaluation  
✔ SHAP-based explanation  

This repository contains the full implementation, analysis, and results.

---

##  2. Market Tiers and Selected Cities

Cities are grouped according to market size:

| Tier  | Cities |
|-------|-------|
| **Big** | New York, Los Angeles, San Francisco, Chicago |
| **Medium** | Austin, Seattle, Denver, Portland |
| **Small** | Santa Cruz, Asheville, Salem, Columbus |

This structure enables performance comparison both **within markets** and **across markets**.

---

## 📂 3. Dataset Source & Reproducibility

All data used is publicly available via:

🔗 https://insideairbnb.com/get-the-data

To reproduce:

1. Download **Detailed Listings Data — `listings.csv.gz`** for each city  
2. Extract → `listings.csv`  
3. Rename using the standard format:
new_york_city_listings.csv
los_angeles_listings.csv
san_francisco_listings.csv
chicago_listings.csv
austin_listings.csv
seattle_listings.csv
denver_listings.csv
portland_listings.csv
asheville_listings.csv
santa_cruz_listings.csv
salem_listings.csv
columbus_listings.csv

4. Upload these files into your working notebook environment  
5. Run all notebook cells sequentially

This yields identical results to those reported.

---

##  4. Feature Engineering

###  Base features extracted:
- accommodates  
- bedrooms  
- beds  
- bathrooms_text  
- review score fields  
- availability and demand features  

###  Engineered features:
| Feature | Purpose |
|---------|---------|
| amenities_count | captures listing richness |
| avg_review_score | combines quality ratings |
| price_per_person | pricing fairness |
| is_entire_home | structural indicator affecting price |

Final dataset used **19 well-defined features per listing**.

---

##  5. Machine Learning Models Used

Three regressors were trained:

- **XGBoost** → baseline tabular model
- **Neural Network A** → shallow dense model
- **Neural Network B** → deeper MLP

Evaluation metrics:

✔ RMSE  
✔ MAE  
✔ R²

Train/test split = 80/20

---

##  6. Key Findings

### City-Level Modeling
- XGBoost is consistently strong
- Neural nets perform better in large markets
- NN-A slightly underperforms NN-B

### Tier-Level Modeling
- Aggregation increases training stability
- Medium tier shows most balanced behavior

### Cross-Tier Transferability
| Train Tier → Test Tier | Outcome |
|------------------------|---------|
| **Big → Medium** | generalizes well |
| **Big → Small** | moderate generalization |
| **Small → Big** | weak transfer |
| **Medium → Both** | balanced transfer |

Conclusion: **major market models learn richer structures that transfer more effectively.**

---

##  7. Explainability Insights — SHAP

SHAP values revealed meaningful price drivers:

| Feature | Interpretation |
|---------|----------------|
| price_per_person | strongest impact |
| accommodates | larger listings → higher price |
| amenities_count | amenities contribute to value |
| avg_review_score | reputation adds premium |
| is_entire_home | entire homes price higher |

SHAP validated that engineered features capture meaningful pricing relationships.

---

##  8. Running the Notebook

### Option 1 — Google Colab
1. Open `.ipynb` in Colab  
2. Upload all `*_listings.csv` files  
3. Run all cells

### Option 2 — Local Execution
pip install xgboost shap tensorflow keras pandas numpy scikit-learn
jupyter notebook

Open the notebook and run cell-by-cell.

---

##  9. Repository Layout
notebooks/
└── Assignment4_Airbnb_Price_Prediction.ipynb
README.md

---

##  10. Final Takeaways

- Tree-based methods show dominant reliability across markets
- Neural models benefit from richer data
- Tier models stabilize learning
- Larger markets produce the most transferable representations
- Explainability confirms intuitive value drivers

This implementation satisfies all technical and analytical requirements of Assignment 4.

---

✍  Lolabattu Harsha — Assignment Submission





