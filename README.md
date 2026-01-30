# Post-Operative Risk Prediction

This project explores the use of machine learning models to assess post-operative patient risk based on clinical indicators.
The focus is on understanding model behavior, interpretability, and limitations when working with a small healthcare dataset.


## Objective

The primary objective of this study is to compare different machine learning models for post-operative risk assessment under limited data conditions.

Rather than optimizing for maximum predictive performance, this work aims to:
- analyze model behavior,
- evaluate interpretability versus performance trade-offs,
- and assess suitability for clinical decision support.


## Dataset

The dataset consists of post-operative patient records including vital signs, stability indicators, oxygen levels, and comfort scores.
The target variable indicates whether a patient is considered safe or requires further admission.

The dataset is relatively small and class-imbalanced, with a higher proportion of risky cases.
These characteristics were taken into account throughout model development and evaluation.


## Data Preparation

The following preprocessing steps were applied:

- Column names were standardized for consistency.
- Missing values in the comfort feature were handled using median imputation.
- Ordinal categorical features were encoded based on clinical interpretation.
- The target variable was converted into a binary format.

No rows were removed after cleaning in order to preserve the original data distribution.


## Modeling Approach

Three models were evaluated to compare interpretability and predictive behavior:


### Logistic Regression

Logistic Regression was used as a baseline model to evaluate whether the dataset could be separated using a linear decision boundary.

The model showed limited performance, particularly in identifying safe cases, suggesting that the relationship between features and the target variable is not purely linear.



### Decision Tree

A Decision Tree model was applied to improve interpretability and better reflect clinical decision-making logic.

This model made it possible to observe how features were prioritized during the decision process and which conditions led to different risk classifications.
To reduce overfitting given the small dataset size, the tree depth was intentionally constrained.

While predictive performance was modest, the model provided valuable insights into decision pathways and feature importance.


### Random Forest

Random Forest was used to improve predictive stability by combining multiple decision trees trained on different subsets of the data.

Compared to a single decision tree, this approach resulted in more consistent performance and improved recall for risky cases.
For this reason, Random Forest was selected as the final predictive model, while the Decision Tree was retained for interpretability.



## Model Evaluation

Model performance was evaluated using precision, recall, F1-score, and accuracy.
Given the clinical context, recall for the risky class was prioritized over overall accuracy to minimize the risk of missing high-risk patients.

Cross-validation was used to assess model stability and reduce dependency on a single train-test split.



## Limitations

This study is subject to several limitations:

- The dataset size is small, which limits generalization.
- Class imbalance affects performance for the safe class.
- Extensive hyperparameter tuning and resampling techniques were intentionally avoided to reduce overfitting risk.

Model results should be interpreted as exploratory and not as diagnostic outcomes.



## Conclusion

This project demonstrates how different machine learning models behave when applied to a small clinical dataset.
It highlights the trade-offs between interpretability and predictive performance and emphasizes the importance of cautious model evaluation in healthcare-related applications.

The models developed in this study are intended to support clinical decision-making rather than replace medical expertise.
