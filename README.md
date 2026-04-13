# Supreme Court Case Prediction Project

# Files
1) Preprocessing (src/preprocess_case_data_a.py and notebooks/preprocess_case_data_a.ipynb)
2) Training (src/run_deep_learn_sc_model_training_pipeline.py, notebooks/run_deep_learn_sc_model_training_pipeline.ipynb, src/run_grad_boost_sc_model_training_pipeline.py, notebooks/run_grad_boost_sc_model_training_pipeline.ipynb)

# Data
- Used the Case Centered Data (Organized by Issue/Legal Provision CSV) from PennState’s Supreme Court Database
- **Description:** A collection of cases where each row records the issue and legal provision dealt with by the Court for the given docket

# Data Prep Pipeline (Found In Preprocessing Files)
1) Remove columns with >20% of values missing
2) Remove docket details that would only be known after a given Supreme Court Case (ex. The majority opinion writer and the direction of the decision)
3) Remove case identifiers (metadata)
4) Impute columns with <20% of values missing with a negative value (ex. -10) to denote missing value
5) Remove instances of cases where any of the feature values are missing (rows where at least one of the values in any of the other columns are missing)

# Feature Selection
- Preprocessed data was split into Train/Validation/Test splits
- A correlation matrix was created to relate all the features of the Train data to each other (prevent data leakage)
- A mutual information matrix was computed to determine which of the features in the pairs would be removed

# Evaluation Metrics
1) Accuracy
2) Log Loss

# Evaluation Strategy
- A separate validation set was chosen over a K-Fold cross-validation approach since there are ≅10000 samples in the Train data (high computational complexity)

# Models
- Non Deep Learning Model: Gradient Boosting Classifier
- Deep Learning Model: Feedforward Neural Network