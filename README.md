# capstone-project-credit-card

Observations in the project:

Firstly imported necessary libraries.
Reading and understanding the data from jupyter notebook.
Using info() function we can check if any of the columns contain null values and also verify the datatypes of each columns. Looking at the output it can be seen that all the 31 columns have non-null values and data types of each column is also correct.
The dataset contains 284807 entries.
    Each entry represents a transaction as fraudulent or non-fraudulent.
    There are 31 columns in the dataset.
    The columns represent various features:
        As, it contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, the original features and more background information about the data could not be provided. Features V1, V2, ... V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'
        'Time' contains the seconds elapsed between each transaction and the first transaction.
        'Amount' is the transaction Amount, this feature can be used for example-dependant cost-sensitive learning.
        'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise.
    There are no missing values in columns.
    There were duplicates 1081 in several rows and we have dropped them.
    Now, the dataset contains 283726 entries.
    The target variable is 'Class', which represents the 1 in case of fraud and 0 for not fraud .

The describe() function generates descriptive statistics that summarize the central tendency,dispersion and shape of a dataset's distribution, excluding NaN values.

Inference:

    Time:
        The average time in seconds elapsed between each transaction and the first transaction is approximately 94811 sec, with a considerable standard deviation of 47481.04.
        The maximum time reported in seconds is significantly high at 172792 sec, which could represent outliers.
    Amount:
        The average amount is approximately \$88.47, with a standard deviation of \$250.39. This signifies the range of transaction Amount.
        Amount range from \$0.00 to \$25691.160, with most falling between \$5.60 and \$77.51. This indicates variability in transaction amount.

. Outliers Treatment:-

Not performing any outliers treatment for this dataset. Because all the columns are already PCA transformed, which assumed that the outlier values are taken care while transforming the data.

. Encoding:-

Categorization of Features for Encoding:

    After analyzing the dataset, we can categorize the features into three groups:
        No Encoding Needed: These are the features that do not require any form of encoding because they are already in a numerical format that can be fed into a model.
        One-Hot Encoding: This is required for nominal variables, which are categorical variables without any intrinsic order. One-hot encoding converts each unique value of the feature into a separate column with a 1 or 0, indicating the presence of that value.
        Label Encoding: This is used for ordinal variables, which are categorical variables with a meaningful order. Label encoding assigns a unique integer to each category in the feature, maintaining the order of the values.

Not performing any encoding for this dataset. Because all the columns are numerical format.


. Feature Scaling:-

We need to scale only the Amount column as all other columns are already scaled by the PCA transformation.


. Splitting the Training Dataset

. Model Building:-

    Logistic Regression Model
    Decision Tree Model
    Xgboost
Logistic Regression Model Evaluation:

    Metric 	Value 	Interpretation
    Accuracy 	94.52% 	The model correctly predicted transactions for 94.52% of the cases.
    Precision (Fraud) 	97.26% 	Out of all class as fraud, only 97.26% were actually fraud.
    Recall (Fraud) 	91.66% 	The model identified 94.66% of the actual fraud transaction.

    The evaluation of the Logistic Regression model in the class domain reveals its performance in predicting fraud transaction. While it achieved an accuracy of 94.52%, indicating overall correctness.

Decision Tree Model Evaluation:

    Metric 	Value 	Interpretation
    Accuracy 	99.82% 	The model correctly predicted transactions for 99.82% of the cases.
    Precision (Fraud) 	98.84% 	Out of all class as fraud, only 98.84% were actually fraud.
    Recall (Fraud) 	91.66% 	The model identified 97.72% of the actual fraud transaction.

XGBoost Model Evaluation:

    Metric 	Value 	Interpretation
    Accuracy 	98.28% 	The model correctly predicted transactions for 82.05% of the cases.
    Precision (Fraud) 	98.84% 	Out of all transactions as fraud, only 98.84% were actually fraud.
    Recall (Fraud) 	97.72% 	The model identified 97.72% of the actual fraud transactions.


. ROC curve:-

According to the analysis of classification reports and AUC scores, it's evident that the top-performing models for this problem are Decision Tree and XGBoost. These models demonstrate exceptional accuracy overall and exhibit strong capabilities in detecting fraud, as indicated by their high recall scores. Although Logistic Regression falls slightly behind in terms of fraud detection compared to the other two models, it still manages to achieve respectable overall accuracy.

    The AUC scores reveal that in the realm of distinguishing between fraudulent and genuine transactions, XGBoost leads with a remarkable score of 0.999, closely trailed by Decision Tree at 0.998. In contrast, Logistic Regression lags behind with a score of 0.989. These findings emphasize the superior discriminatory prowess of XGBoost and Decision Tree models over Logistic Regression in this context.`

    After analyzing the outcomes, we suggest considering either XGBoost or Decision Tree for addressing this issue. Further evaluation can help determine which model to prioritize, taking into account factors like computational capacity and the level of interpretability desired.

. Hyperparameter Tuning:-

XGBoost Model Evaluation (After Tuning)

    Metric 	Value 	Interpretation
    Accuracy 	99.75% 	The model correctly predicted transactions for 99.75% of the classes.
    Precision (Fraud) 	99.84% 	Out of all transactions predicted as fraud, only 99.84% were actually fraud.
    Recall (Fraud) 	99.66% 	The model identified 99.66% of the actual fraud transactions.

. Result:-

    After analyzing the outcomes, it's evident that leveraging XGBoost with oversampled data and fine-tuned hyperparameters yields superior results in identifying fraudulent transactions. This method consistently demonstrates high precision and recall rates across various folds, underscoring its resilience and accuracy in managing imbalanced datasets and delivering precise predictions.
