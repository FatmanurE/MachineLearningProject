# MachineLearningProject
Metal Parts Lifespan Prediction and Classification Using Machine Learning
Project Overview
This project focuses on predicting the lifespan of metal parts and classifying them based on durability using machine learning techniques. The primary goal is to help a manufacturing company optimize production, reduce defects, and improve part quality.

The dataset consists of production parameters, material composition, and defect metrics, which influence the durability of metal parts. The project is divided into two key tasks:

Regression Analysis: Predicting the exact lifespan of metal parts using Decision Tree Regressor and Polynomial Regression with Ridge Regularization.
Classification Task: Determining whether a metal part meets the minimum durability requirement of 1500 hours using Logistic Regression and Support Vector Machines (SVM).
Dataset
The dataset contains 1000 samples with 16 features, including:

Categorical Features:
partType: Type of metal part (Nozzle, Blade, Block, Valve).
microstructure: Grain structure of the metal (equiGrain, colGrain, singleGrain).
seedLocation: Location in the mold (Top or Bottom).
castType: Casting method used (Die, Investment, Continuous).
Numerical Features:
coolingRate, quenchTime, forgeTime, HeatTreatTime: Production parameters affecting the strength of metal.
Nickel%, Iron%, Cobalt%, Chromium%: Alloy composition affecting durability.
smallDefects, largeDefects, sliverDefects: Defect metrics affecting the quality of metal parts.
Target Variables:
Lifespan: The durability of a part in hours (for regression).
Lifespan_Label: Binary classification (1: Long lifespan, 0: Short lifespan).
Exploratory Data Analysis (EDA)
Data distribution: The Lifespan variable is right-skewed, with most parts having a lifespan below 2000 hours.
Correlation Analysis:
Nickel% has a positive correlation (0.32) with Lifespan, suggesting a higher Nickel content improves durability.
SmallDefects has a negative correlation (-0.18) with Lifespan, meaning more defects reduce lifespan.
Nickel% and Iron% have a strong negative correlation (-0.79), indicating multicollinearity concerns.
Boxplots & Heatmaps: Used to analyze the influence of categorical variables on lifespan. castType and partType were identified as key features affecting durability.
1️⃣ Regression Task - Predicting Lifespan
Methods Used
✅ Decision Tree Regressor
✅ Polynomial Regression with Ridge Regularization

Implementation Details
Feature Selection: One-hot encoding for categorical variables (partType, castType).
Data Split: 80% training, 20% testing.
Decision Tree Regressor:
Hyperparameters: max_depth=5, min_samples_split=10, min_samples_leaf=5.
Captures nonlinear patterns efficiently.
Polynomial Regression (Ridge Regularization):
Degree=2 to model quadratic relationships.
Regularization applied (alpha=1) to prevent overfitting.
Model Evaluation (Regression)
Model	R² Score (Train)	R² Score (Test)	MSE (Train)	MSE (Test)
Decision Tree	0.8896	0.8752	12,623.97	14,973.65
Polynomial Regression	0.8113	0.7629	22,362.44	24,554.04
📌 Key Findings:
✔ Decision Tree performed better, capturing non-linear relationships effectively.
✔ Polynomial Regression struggled to generalize and had higher error rates, indicating limitations in modeling complex interactions.

2️⃣ Classification Task - Categorizing Parts Based on Durability
Methods Used
✅ Logistic Regression
✅ Support Vector Machines (SVM)

Implementation Details
Target Variable Creation: Converted Lifespan into a binary label (Lifespan_Label), where ≥1500 hours = 1, otherwise 0.
Feature Engineering: Applied StandardScaler for numeric features and one-hot encoding for categorical variables.
Model Tuning:
Logistic Regression: Used hyperparameter tuning (C values tested).
SVM: Applied RBF kernel and optimized C values using F1-score.
Model Evaluation (Classification)
Model	Accuracy (%)	Precision	Recall	F1 Score
Logistic Regression	72.50%	72.22%	20.63%	32.10%
Support Vector Machine	89.00%	82.54%	82.54%	82.54%
📌 Key Findings:
✔ SVM outperformed Logistic Regression by effectively capturing nonlinear decision boundaries.
✔ Logistic Regression struggled due to class imbalance (fewer samples for long lifespan parts).
✔ SMOTE or resampling techniques could improve class balance and recall for Logistic Regression.

🔍 Future Improvements
Ensemble Methods: Using Random Forest or Gradient Boosting for more stable regression results.
Hyperparameter Optimization: Grid search for better tuning of Polynomial Regression and Logistic Regression.
Feature Engineering:
Adding polynomial interactions in Logistic Regression.
Testing different kernel functions in SVM.
Addressing Class Imbalance:
Using SMOTE to increase samples for the minority class (long lifespan parts).
Trying different threshold values for classification.
📌 Conclusion
This project demonstrates the application of machine learning techniques in industrial manufacturing to predict part lifespan and classify defective parts. The Decision Tree Regressor and SVM models were found to be the most effective in their respective tasks. These findings can help optimize production quality, reduce defects, and enhance decision-making in manufacturing industries.

👩‍💻 Author
👤 Fatmanur Ertas
📌 Master's in Data Science - University of Greenwich
