**Executive Summary**

The project aims to build a credit risk model to predict whether a customer will default on his or her loan with the given dataset. Basic data cleaning to fix potential data entry error is conducted. During the exploratory data analysis stage, the box plot suggests there exist outliers statistically, but since it is possible for customers to have those stats, 6 dependents or debt-to-income ratio of 0.4 for example, the statistical outliers are kept in the dataset. Also since the dataset is imbalanced, a resampling pipeline which includes undersampling and SMOTE is conducted. Then, feature engineering is conducted to build the feature pool for feature selection, which brings in 1642 new columns. After selecting the best features, multiple machine learning models are tested, including Logistic Regression, Boost Tree, Random Forest, XGBoost and LightGBM. While the average customer life value and the expected loss for a default are unknown, it is assumed that the expected loss for a default is large. The model is also made adaptable for a dynamic decision boundary to control the volume of loans issued by the company. Thus, the key metric for model evaluation for this project is selected to be model’s average_precision_score, which is a similar to PR AUC and is non-interpolated measure of the area under the precision-recall curve.


After tuning the hyperparameters, the performance of the models is evaluated to choose the final model to be deployed. The final model, a LightGBM model with n_estimators=20, num_leaves=4, learning_rate=0.1, random_state=42, can achieve a training average_precision_score of 0.7728, a testing average_precision_score of 0.7585. In the end, the cut-off point for probability of default, 0.4, is recommended as it is estimated that with the final model and a cut-off point for probability of default of 0.4, 77.8% customers that will default will be caught, while 40.3% loan application will be rejected or be passed to manual inspection. Finally, exact same steps are conducted using the whole data set to train a new model with the same hyperparameter, and predictions are made for the real test set in the seperate test.csv file. Still, if there is a need to adjust the company’s volume of loan originated or the average potential loss for a default becomes available, the cut-off point could be adjusted to meet dynamic business goals.

![image](https://github.com/user-attachments/assets/7195ea8e-b47a-4d61-98d8-eac78da4cd1d)
