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

| Rank | Feature | Description | Gini Importance |
| :---: | :--- | :--- | :---: |
| **1** | `ram` | Random Access Memory (MB) | **0.458** |
| **2** | `battery_power` | Total energy stored by battery (mAh) | **0.074** |
| **3** | `px_width` | Pixel resolution width | **0.059** |
| **4** | `px_height` | Pixel resolution height | **0.058** |
| **5** | `int_memory` | Internal Memory (GB) | **0.040** |
| **6** | `mobile_wt` | Weight of mobile phone | **0.040** |
| **7** | `pc` | Primary Camera megapixels | **0.031** |
| **8** | `talk_time` | Longest battery run time on a call | **0.031** |
| **9** | `clock_speed` | Microprocessor execution speed | **0.030** |
| **10** | `sc_w` | Screen width (cm) | **0.030** |
| **11** | `sc_h` | Screen height (cm) | **0.029** |
| **12** | `fc` | Front Camera megapixels | **0.027** |
| **13** | `m_dep` | Mobile depth (cm) | **0.025** |
| **14** | `n_cores` | Number of processor cores | **0.024** |
| **15** | `dual_sim` | Dual SIM support | **0.008** |
| **16** | `wifi` | Wi-Fi connectivity | **0.007** |
| **17** | `blue` | Bluetooth connectivity | **0.007** |
| **18** | `touch_screen` | Touch screen presence | **0.007** |
| **19** | `four_g` | 4G network capability | **0.007** |
| **20** | `three_g` | 3G network capability | **0.006** |

## Conclusion

- **Classification Precision:** The model demonstrates strong predictive performance at **86.67% accuracy**, showing particularly high separation power for extreme tiers (Class 0 at 0.94 F1-score and Class 3 at 0.92 F1-score).
- **RAM is the Primary Deciding Factor:** With a Gini importance of **0.458**, `ram` accounts for nearly 46% of the total predictive power. Upgrading RAM is the single most effective way to justify a higher price bracket.
- **Secondary Tier Drivers:** Battery capacity (`0.074`) and display resolution (`px_width` at `0.059` and `px_height` at `0.058`) are the subsequent major differentiators between tiers.
- **Commoditized Baseline Features:** Connectivity features such as Dual SIM, Wi-Fi, Bluetooth, Touch Screen, 4G, and 3G each have less than a **0.008** importance score. These are industry standards expected by consumers and do not command a premium price on their own.
- **Actionable Recommendation for Bob:** Focus production and supply chain budgets on maximizing **RAM**, followed by **battery size** and **screen resolution**, rather than investing heavily in commodity marketing features.