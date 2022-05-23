# Columbia_Fintech_Module12

## Overview of the Analysis

The purpose of this analysis is to classify if a loan is high risk or healthy loan. 

The problem is to classify and hence I used one of the classification model. The model of choice is LogisticRegression model. LogisticRegression uses log function to scale a value between 0 and 1.
The independent variables used are loan_size, interest_rate, borrower_income, debt_to_income, num_of_accounts, derogatory_marks and total_debt. The dependent variable is loan_status. loan_status can have two values, 0 indicates a healthy loan, and 1 indicates high risk loan.

The model needs to be trained based on a given set of data and then use the fitted model to predict the outcome on test data. 
The reason to test it on a different set of data is to check the validity and strength of the model that is fitted using some training data.

The stages for this Machine Learning algo
* Load the independent and dependent variables in to a dataframe
* Split the data in to X (independent variables) and y (dependent variables)
* Split the data in to training and testing data set using train_test_split function

* Initialize Model - Fit - Predict - Evaluate
  * Initialize the model as LogisticRegression with random_state = 1. Note that random_state is an initial random seed. By keeping this value constant, you get same results on multiple runs. If this variable is kept empty, then the random_state is randomly picked and you may get different results in different runs.
  * Fit the model with the training data created earlier
  * Predict the results for testing data using the test data created earlier
  * Evaluate the model using accuracy_score, confusion matrix and classification report

Note : Based on the distinct values of original data for dependent variable (i.e. loan_status), it was obvious that the data is imbalanced. There are lot more healthy loans as compared to high risk loans. This creates imbalanced data problem and inadvertently causes the model to weigh more towards the major class. This problem can be solved by either Oversampling (i.e. creating more data entries for minor class) or Undersampling (i.e. creating less data entries for major class) or a combination of both. 

In this analysis, we used OverSampling approach using RandomOverSampler function on training data. One the training data was OverSampled, we ran the Machine Learning algo again and compared the results. All the four stages, i.e. Initialize - Fit - Predict - Evaluate were run using resampled data.


## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:

  * The model is almost perfect for healthy loans. The balanced accuracy score is relatively high at 0.95
  * F1 Score, precision and recall value are very high for 0 (healthy loan). F1 score and precision is 1 and recall is 0.99
  * F1 Score, precision and recall value are still relatively high for 1 (high-risk loan). F1 score is 0.88, precision is 0.85 and recall is 0.91. These can be improved to have higher confidence in the model. These metrics are not as high as they are for healthy loans. 
  * In summary, the model is fitting better for healthy loans v.s. high-risk loans.




* Machine Learning Model 2:

  * The model is almost perfect for healthy loans. The balanced accuracy score is 0.99
  * F1 Score, precision and recall value are very high for 0 (healthy loan). F1 score is 1, precision is 1, recall is 0.99. The recall has improved over the Model 1 reading.
  * F1 Score, precision and recall value are still relatively high for 1 (high-risk loan). F1 score being 0.91, recall value of 0.99 and precision being 0.84 is quite high. Recall has improved but precision has depreciated a small bit.
  * Oversampling of under-represented i.e. minor class has improved the predition capability of the model.



## Summary

In summary, the model is fitting better for healthy loans v.s. high-risk loans and Model 2 is an improvement as compared to Model 1. 

While Oversampling is one way, Undersampling or a combination model may be better. The key difference between two approaches is that in Oversampling we synthetically create the minor class. Whereas in Undersampling, we suppress major class. This addresses the issue of synthetic creation of minor class, but it comes at the cost of loosing prediction capability of major class. 
