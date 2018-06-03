# Credit-Card-Fraud-Classification_cost-sensitive-method-for-imbalanced-data

### Some important highlights for this case

#### a. Deal with imbalanced data

Because the fraud are quite rare, the data could be super imbalanced. Use common modeling process might not predict the minority class very well. Here are some techniques I would use to handle imbalanced data.
a.1 Oversampling or Undersampling to generate more balanced data.
a.2 Set cost for misclassification of the minority class. For example, class_weight parameter would help to
penalize mistakes in specific class.
a.3 Choose appropriate measures. For example, instead of accuracy, I would choose F-measure and
confusion matrix which could measure the precision and recall of both classes.

In this case, I compared oversampling and cost class_weight methods. Oversampling would have the risk of overfitting, but it allows more models which don't have class_weight parameter. Class_weight would be preferred for dealing with imbalanced data.

#### b. Model fitting and selection

To obtain better predictive performance and avoid overfitting, there are some important steps for
training and selecting models.
b.1 Split training and testing data.
b.2 Cross validation to find out the best parameters that has the best generalization.
b.3 Select several appropriate classifiers. Models have specific pros and cons. Need to select models
suitable for this case. Some models such as GradientBoostingClassifier doesn’t have class_weight
parameter. It should be used with oversampling or undersampling method for imbalanced data. In this case, I used Logistic ** Regression, Random Forest and XGboost**. 
b.4 Model comparison. Since this case needs to set alert threshold, it’s better to calculate the
optimal threshold for each model and then select the best model that has the best overall performance.
To simplify, I first select model based on F measure, recall, precision, ROC and AUC, and then calculate the
optimal threshold for the selected model.

#### c. Set an alert threshold

First, I would set the objective of the alert system. For example, I might want to achieve 90% recall. I
could also add cost for misclassification for each class and set the objective as minimize cost.
Second, I will test different probability threshold iteratively. Many classifiers could return prediction
probability, indicating the probability that it belongs to each class. I will choose the threshold that could
achieve my objective and also get good overall accuracy.