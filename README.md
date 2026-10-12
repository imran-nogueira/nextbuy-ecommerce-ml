# NextBuy — E-commerce Analytics & Recommendations

> Exploratory analysis of a multi-table grocery e-commerce dataset, answering 8 business questions and powering a product-recommendation engine built on association rules.

**Epitech Bachelor · Year 1 · Data Analysis (B-DAT-201) · Mar 2026**
Source code is private under Epitech's academic policy. Happy to walk you through the notebooks or demo the dashboards → **imran.nogueira@gmail.com**

## Overview

Five related tables — orders, products, departments, aisles and order lines — cleaned, joined and analyzed to answer concrete business questions, then turned into a recommendation engine that suggests complementary products for a given cart.

## Business questions answered

1. Top 10 best-selling products
2. Top 10 least-sold products by day of the week
3. Top 10 products added to the cart first
4. Top 10 products bought together with the most popular item
5. Top 10 most reordered products
6. Which days customers order most
7. Which department offers the fewest products
8. Sales by department × day of the week (heatmap)

## Stack

| Layer | Tech |
|---|---|
| Analysis | Python, pandas, NumPy, matplotlib, seaborn, Jupyter |
| Recommendations | mlxtend — Apriori + association rules |
| Regression | scikit-learn RandomForestRegressor |
| Dashboards | Streamlit (one per model), models serialized with joblib |

## How the recommendation engine works

1. Keep the 100 best-selling products and build an order × product basket matrix.
2. Mine frequent itemsets with **Apriori** (`min_support = 0.01`).
3. Derive **association rules**, keep those with lift ≥ 1, rank by confidence.
4. For a given cart, suggest the consequents of the strongest matching rules — served in a Streamlit dashboard.

## What I'd do differently

The second model, a RandomForest predicting department activity by day, reported R² = 0.99. Reviewing it afterwards, the target was derived from a column that was also among the features — a textbook **target leakage**, which makes that score meaningless. The fix: build the target from a separate signal and validate on held-out days rather than a random split. I keep this here on purpose: catching leakage is part of the job.

## Contact

Notebook walkthrough or dashboard demo on request → **imran.nogueira@gmail.com** · [Portfolio](https://imran-nogueira.github.io)
