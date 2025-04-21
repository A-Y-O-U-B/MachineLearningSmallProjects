# NaiveBayes

1) Gaussian Naive Bayes:
   1. Problem Definition:
      - In this project, I used the Breast Cancer Wisconsin dataset to classify cancer diagnosis (benign or malignant).
      - The goal is to predict whether a patient has cancer based on cell sample features.
     
   3. Data:
      - Source: Breast Cancer Wisconsin Dataset (https://www.kaggle.com/uciml/breast-cancer-wisconsin-data)
      - Features: A total of 30 numerical features (e.g., radius, texture, perimeter, smoothness, etc.)
      - Target Variable: “diagnosis” (M = Malignant, B = Benign)
     
   4. Method:
      - Gaussian Naive Bayes: A probabilistic classification method assuming each feature follows a normal 
        distribution for each class.
      - scikit-learn and manual Naive Bayes implementation:
          - scikit-learn: GaussianNB(var_smoothing=1e-9)
          - Manual implementation: Computed mean and variance (with ddof=0) and added var_smoothing=1e-9 to address                potential numerical issues.
      - Train/Test Split: 79% training, 21% testing (random_state=42, stratify=y).
     
   5. Results:
      - Accuracy: ~94% (sklearn model) / ~92-93% (manual model)
      - Confusion Matrix:
          - sklearn:
             - [[75  0]
               [ 7 38]]
          - manual:
             - [[72  3]
               [ 6 39]]
      - Additional Metrics (Precision, Recall, F1-Score) were calculated and reported.
      - It was seen that sklearn model was faster than manual model in terms of time and the time were calculated for 
        each model and reported
     
   6. Discussion:
      - Reasons for Differences: I think that the minor discrepancies between manual and sklearn results may stem from 
        variance calculation, log probability differences, or floating-point rounding.
      - In a problem with a balanced class distribution, accuracy is often a good initial indicator. However, if there are factors like cost, risk, or priority, 
        metrics such as precision, recall, and F1 should definitely be considered. Therefore, evaluation metrics must be chosen based on the problem and the nature 
        of the data (especially class distribution). In particular, for imbalanced datasets, focusing on metrics like precision, recall, and F1-score rather than 
        relying solely on accuracy leads to a much more meaningful assessment.

   7. Resources:
      - https://scikit-learn.org
      - https://www.ibm.com
      - INTRUDUCTION TO MACHINE LEARNING by ETHEM ALPAYDIN
      - https://chatgpt.com





  



  


      


       

   

    
