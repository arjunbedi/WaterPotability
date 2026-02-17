Project Summary

This project predicts whether water is potable (safe to drink) using machine learning models trained on physicochemical measurements. Because the dataset contains noise, missing values, and class imbalance, the workflow emphasizes thorough preprocessing, exploratory analysis, and systematic model comparison.

Dataset

Source: Water Potability Dataset, commonly distributed through platforms like Kaggle

Size: 3,276 samples

Target: Potability (0 = not potable, 1 = potable)

Features (9): pH, Hardness, Solids, Chloramines, Sulfate, Conductivity, Organic Carbon, Trihalomethanes, Turbidity

Key Data Insights

Missing values in pH, Sulfate, and Trihalomethanes

Overlapping feature distributions—no single distinguishing variable

Low linear correlations → strong nonlinearity

Moderate class imbalance (potable ≈ one-third)

Preprocessing Steps

Median imputation for missing data

Outliers retained due to natural environmental variability

Scaling only for logistic regression models

Stratified 80/20 train–test split

Imbalance handled primarily via model selection and tuning (no oversampling)

Modeling Approach

The project follows an intentional progression from simple to more expressive models:

1. Logistic Regression (Baseline)

Easy to interpret but limited by dataset nonlinearity

Poor minority-class recall

2. Decision Tree

Introduces nonlinear decision boundaries

Improved potable-class recall (~0.539)

Overfitting and model instability

3. Random Forest

Reduced variance and better generalization

Best overall accuracy (~0.64)

Majority class well-predicted; minority class still weak

Depth regularization (max_depth=10) improved potable recall (0.539 → 0.533 F1)

4. Gradient Boosting (Final Model)

Sequentially corrects previous errors

Best performance on minority (potable) class

Potable recall: 0.625

Potable F1: 0.555

Slightly lower overall accuracy (~0.61) but superior for safety-critical predictions

Key Findings

Dataset characteristics (noise, overlapping distributions, nonlinearity) demand nonlinear, robust models.

Random Forest provides the highest accuracy, but

Gradient Boosting is the most appropriate final model because it excels at detecting potable water—critical for real-world public-health applications.

The progression of models highlights the importance of matching model complexity to dataset structure and optimizing for the metrics that matter most (recall on the minority class).
