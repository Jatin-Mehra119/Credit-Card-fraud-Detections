# Credit Card Fraud Detection Project

In this repository, I am developing a machine learning model to detect fraudulent transactions using various parameters such as time, location, and store information.

### Project Workflow

1.  **Data Source**:
    
    -   The dataset was sourced from Kaggle.
2.  **Exploratory Data Analysis (EDA) and Visualization**:
    
    -   Conducted basic EDA and data visualization using Plotly, which is effective for handling large datasets.
3.  **Data Preprocessing**:
    
    -   Implemented custom transformers to transform the data and create new features. These features include hours, minutes, seconds, weekdays, is-weekend (indicating whether the day is a weekend or not), and clusters of locations.
    -   A dedicated script, `preprocessing.py`, was created to handle data transformation.
4.  **Data Splitting**:
    
    -   Split the dataset into training and test sets.
5.  **Model Training**:
    
    -   **Logistic Regression**:
        -   Initially trained a logistic regression model to understand the data complexity. As expected, it performed poorly.
    -   **Random Forest Classifier**:
        -   Achieved a validation score of around 78 F1 score, 98 precision score, and 65 recall score for the positive class (fraud).
        -   Performed hyperparameter tuning with randomized CV search, improving the F1 score to 82. However, this was insufficient for anomaly detection, leading to the decision to drop this model.
    -   **Other Models**:
        -   **Isolation Forest**: Achieved an F1 score of 0.05 for the positive class.
        -   **K-Neighbors Classifier**: Achieved an F1 score of 42 for the positive class.
        -   **OneClassSVM**: Trained on around 20,000 instances (19,400 negative class, 600 positive class) but did not perform well.
    -   **XGBClassifier**:
        -   Achieved a validation F1 score of 87 for the positive class.
        -   Hyperparameter tuning with randomized search CV improved the F1 score to 89.
        -   Selected this model for its good performance and reasonable training time.
        -   Tested on sets and achieved a 90 F1 score for the positive class, 97 precision, and 84 recall.
    -   **Class Balancing Approaches**:
        -   Tried balancing the class using techniques like SMOTE, but the models did not perform well with these techniques.
        -   Trained the model using the original dataset with resampling, i.e., using instances of each class 19K + 19K, achieving around 97 and 98 F1 scores for both classes. However, I chose not to use this approach as it was not considered a good practice.

### Deployment

I am developing a Flask app to predict anomalies on the fly using Flask APIs, enabling real-time fraud detection. [Flask APP](https://github.com/Jatin-Mehra119/Flask-APP-CreditCard-fraud-Detections-)
