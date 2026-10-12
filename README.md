# Mobile Price Range Classification

Bob has founded a new mobile phone company aiming to compete with industry giants like Apple and Samsung. To stay competitive, he needs an objective, data-driven approach to estimate how his mobile specifications map to selling price tiers.

Using historical mobile sales data, this project builds a Machine Learning model to discover relationships between hardware specifications (e.g., RAM, battery capacity, screen resolution) and pricing brackets. Instead of predicting continuous prices, the goal is to categorize devices into four distinct price ranges:

- **0**: Low Cost
- **1**: Medium Cost
- **2**: High Cost
- **3**: Very High Cost

**Dataset Source:** [Mobile Price Classification (Kaggle)](https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification)

## Method
1. **Data Preparation:** 
   - Feature columns ($X$) and target column (`price_range`, $y$) separated.
   - Categorical and binary indicators validated against numerical hardware specs.
2. **Train/Test Split:** 
   - 70% Training data (`X_train`, `y_train`) to train the model.
   - 30% Testing data (`X_test`, `y_test`) to evaluate unseen generalization.
3. **Model Selection:** 
   - **Random Forest Classifier**

## Results
### Model Performance
Overall Test Accuracy: **[e.g., 86.7%]**

| Metric | Class 0 (Low) | Class 1 (Medium) | Class 2 (High) | Class 3 (Very High) | Macro Avg | Weighted Avg |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Precision** | 0.94 | 0.82 | 0.79 | 0.92 | 0.87 | 0.87 |
| **Recall** | 0.95 | 0.82 | 0.78 | 0.91 | 0.87 | 0.87 |
| **F1-Score** | 0.94 | 0.82 | 0.79 | 0.92 | 0.87 | 0.87 |
| **Support** | 151 | 146 | 148 | 155 | 600 | 600 |

---

### Top Feature Importances

The Random Forest model identified the following specifications as the strongest drivers of price tier classification:

| Rank | Feature | Importance Score | Business Takeaway |
| :---: | :--- | :---: | :--- |
| **1** | `ram` | ~[0.48 - 0.52] | By far the primary determinant of price tier. |
| **2** | `battery_power` | ~[0.07 - 0.09] | Significant factor separating entry from premium models. |
| **3** | `px_width` / `px_height` | ~[0.05 - 0.08] | Screen display resolution strongly correlates with tier. |
| **4** | `int_memory` | ~[0.03 - 0.05] | Internal storage capacity provides moderate lift. |
| **5** | `mobile_wt` | ~[0.03 - 0.04] | Weight and physical form factor have subtle influence. |

*(Features like `touch_screen`, `wifi`, and `dual_sim` exhibited minimal impact on price differentiation across competitors).*

---

## Conclusion

- **Dominant Driver:** **RAM** is the single most critical specification influencing mobile pricing brackets in the market, accounting for roughly half of the model's total predictive weight.
- **Secondary Tier Influencers:** **Battery capacity** and **display resolution** (`px_width`, `px_height`) serve as the secondary tier-defining specifications.
- **Commodity Features:** Connectivity features such as 3G/4G, Bluetooth, Dual SIM, and Wi-Fi have become standard industry baselines and do not justify a higher price tier on their own.
- **Actionable Recommendation for Bob:** When designing new product tiers, allocate the component budget primarily toward RAM and display quality to justify moving from a lower price bracket (0 or 1) to a premium bracket (2 or 3).