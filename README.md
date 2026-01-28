# customer-segmentation-data-mining
Data mining project focused on customer segmentation and profile analysis.


# Customer Segmentation Analysis: A Multi-Perspective Clustering Approach

This project focuses on identifying distinct customer profiles by integrating **demographic data** with **behavioral spending patterns (preferences)**. The objective is to create actionable segments to drive personalized marketing strategies and improve business decision-making.

##  Project Pipeline

### 1. Data Cleaning & Imputation

* **Data Quality Assessment**: Initial analysis identified missing values, notably in the `loyalty_card` variable (18.51% missing).
* **Missing Data Imputation**: Utilized **k-Nearest Neighbors (kNN) Imputer** with  to estimate missing entries based on similar user profiles.
* **Outlier Management**: Implemented an inclusive filtering strategy that discards observations only if they are flagged as anomalies by three simultaneous methods: **Z-Score** (), **Interquartile Range (IQR)** (), and **Manual Thresholds** based on business logic.

### 2. Feature Engineering & Transformation

* **Distribution Normalization**: Applied **Log Transformation** () to variables with high positive skewness, such as `spend_videogames` and `spend_electronics`, to improve model performance.
* **New Feature Creation**: Engineered behavioral metrics including `age`, `loyalty_years`, `total_children`, and daily shopping periods (`time_period`).
* **Categorical Encoding**: Converted non-numeric features via **One-Hot Encoding** to ensure compatibility with clustering algorithms.

### 3. Clustering Strategy

A specialized "Multi-Perspective" approach was adopted:

* **Feature Division**: Data was split into two perspectives: **Demographics/Behavior** and **Preferences**.
* **Algorithm Comparison**: Evaluated **K-Means** against **Ward's Hierarchical Method**.
* **Noise Detection**: Integrated **DBSCAN** to isolate and identify density-based anomalies before final labeling.
* **Final Integration**: Merged the two perspectives using hierarchical clustering to define **4 robust final segments**.

### 4. Model Validation & Interpretability

* **Predictive Validation**: A **Decision Tree Classifier** was trained to predict cluster labels, achieving an accuracy of **95.10%**.
* **Segmentation Drivers**: Feature importance analysis revealed that spending in **Groceries**, **Meat**, and **Video Games** are the primary factors distinguishing the customer profiles.

## Identified Customer Profiles

1. **The Price-Sensitive & Fussy Shoppers**: High complaint rates (**1.29**) and heavy reliance on promotions (**0.64**). They manage a strict budget with the lowest grocery spend (**9,683.17**).
2. **The Niche Entertainment Enthusiasts**: A younger segment with the fewest children (**0.40**). Their spending is leisure-driven, leading in **Video Games** (**5,005.34**) and **Alcohol** (**2,565.19**).
3. **The Premium Family Pillar**: The highest-value segment. Large households (**4.35 children**) that dominate essential categories like **Groceries** (**45,007.24**) and **Meat**.
4. **The Health-Conscious Minimalists**: Defined by a specific diet, showing the highest expenditure on **Vegetables** (**4,924.48**) and a strong rejection of meat and alcohol products.

##  Tech Stack

* **Language**: Python
* **Libraries**: Pandas, NumPy, Scikit-learn
* **Clustering**: K-Means, Ward’s Hierarchical, DBSCAN
* **Visualization**: Matplotlib, Seaborn, t-SNE
