2) Logistic Regression:
   1. Problem Definition:
      - Goal: Predict whether a customer will churn (leave the service) based on their account, service usage, and demographic data.
      - This project compares a manual implementation of logistic regression (using Python & NumPy) with scikit-learn’s LogisticRegression.
     
   2. Data:
      - Source: Telco Customer Churn Dataset (https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
      - Features: Multiple continuous and categorical features (e.g., tenure, MonthlyCharges, contract type, etc.).
      - Target Variable: Churn (binary: Yes/No, which we encode as 1/0).
     
   3. Method:
       3.1 Manual Logistic Regression:
          - Implementation:
              - Uses batch gradient descent to optimize the cross-entropy (logistic) cost function.
              - Includes feature scaling (via StandardScaler) and a bias column appended to X.
              -Applies a stable sigmoid (with clipping) to avoid overflow in exp().
              -Trains for a fixed number of iterations, printing the cost at intervals.
       3.2 scikit-learn Model:
          - Implementation:
              - Uses LogisticRegression(max_iter=1000, ...) from scikit-learn.
              - Also uses the same feature scaling (fitted on X_train) to ensure a fair comparison.
              - We measure training (fit) time and prediction time using time.time().
       3.3 Train/Test Split:
          - We split 80% for training, 20% for testing, using random_state=42 and stratify=y to preserve the churn ratio.

   4. Results:
      - Accuracy: ~80% (sklearn model) / ~79-80% (manual model)
      - Confusion Matrix:
          - sklearn:
             - [[917 116]
               [158 216]]
          - manual:
             - [[897 136]
               [151 223]]
      - Additional Metrics (Precision, Recall, F1-Score) were calculated and reported.
      - It was seen that sklearn model was faster than manual model in terms of time and the time were calculated for 
        each model and reported
     
   5) Discussion
      - Why Minor Differences?
          - scikit-learn’s logistic regression uses more sophisticated optimization (e.g., LBFGS or liblinear) and may have built-in regularization.
          - Our manual model uses a simple batch gradient descent with a fixed learning rate. Even after careful clipping and scaling, it can converge slightly differently.
      - Imbalanced Classes
          - The churn class (1) is only ~27% of the data. Both models occasionally predict “No Churn” more often, resulting in a lower recall for the positive class.
          - Evaluating precision, recall, F1, or even ROC-AUC is more informative than accuracy alone.
      - Feature Engineering
          - Additional preprocessing or hyperparameter tuning (e.g., learning rate schedules, mini-batches) could improve manual model performance.

   7. Resources:
      - https://scikit-learn.org
      - https://www.ibm.com
      - INTRUDUCTION TO MACHINE LEARNING by ETHEM ALPAYDIN
      - https://chatgpt.com
