# SyriaTel-Churn-Project

### Overview
This project in which I analyzed customer data for the telecom company, SyriaTel. The dataset was used to predict customer churn, whether or not a customer quit their phone plan and left the company. I also figured that finding out what features, or columns, in the dataset, are most important in predicting if a customer leaves the company and quits their phone plan. I used different classification models to make these predictions. I started with a baseline logistic regression model, which was not very good at predicting which customers would leave the company. After doing some feature engineering, and doing different models, such as KNN, decision trees, and random forest, I created a model that could predict the accuracy of customer churn up to 75%. I could also figure out the most important features predicting customer churn, which were the number of customer service calls, and phone charges for calls made in the daytime. 

### Stakeholder and Business Problem
The stakeholder was SyriaTel, a telecommunications company, and the problem was figuring out which customers would churn, and what caused these customers to leave. 

### Data Understanding and Analysis
The data came from a dataframe of information regarding roughly 3,300 customers of SyriaTel, which largely had customer data, and whether or not they left the company. The data had no NaN values, and did not need to be cleaned. There were several categorical columns, such as Area Code and State, which I one-hot-encoded in order to feed the information in these columns into my models. 

### Initial Model
The first model I created was a baseline logistic regression model. The model had an accuracy of 86%, but the recall for the true value in the target variable was very low at 11%. This is very bad, as it means the model can only predict 11% of customers who actually did leave the company. There were more false negatives in the model than True Positives, which I had to account for in creating new better models. 

### Fine Tuning the Model
The baseline model had no categorical features. Also logistic regression is not the best model, so I tried others. The first one I tried after was KNN, which was not very good, so I decided to use decision trees, and then Random Forest. I also had a huge class imbalance in the target variable, only 17% of the customers in the dataset churned, or left the company. As a result, all the models were very good at predicting True Negatives, or customers who did not leave, but this makes sense as they consist of 83% of the dataset. So I tried using SMOTE to address this imbalance. I also hypertuned the parameters for the Random Forest model using GridsearchCV. The best Random Forest model with categorical features encoded, using SMOTE, and optimized hyperparameter had a recall of 67%, meaning it could predict 67% of the customers who did leave the company.

### Final Model
On a hunch/whim, I decided to redo the Random Forest Model without using onehotencoder categorical columns. The new simple baseline was better than the final model with categorical columns so I decided to take this new approach. I hypertuned this Random Forest model, and created a final model with an overall accuracy of 96%, and a recall of 75% for the target variable, meaning it could predict up to 75% of customers who left, a significant improvement from the baseline logistic regression, which could only predict 11% of people who left. 

### Conclusion
The most important criteria for determining customer churn in the SyriaTe dataset, according to the data we collected, and models we used was customer service calls and daytime phone charges. The reason for this is kind of intuitive, customers who make more customer service calls obviously have more problems with their plan or service and would want to end their plan. According to the data, the reason that daytime phone charges were an important predictor for churn was because the company charged $0.17/minute for day calls, while calls in the evening cost $0.08/minute, and calls at night approximately $0.04. As customers were charged more for making calls during the day, customers who made more calls during the day were charged more, and thus had higher bills, which may have prompted some to leave the company.

### Data Source
https://www.kaggle.com/becksddf/churn-in-telecoms-dataset

### Presentation Link
https://github.com/ArshPatel95/SyriaTel-Churn-Project/blob/main/SyriaTel%20Customer%20Churn%20Prediction.pptx

### Explanation of all files
In my repository, I have my powerpoint, and my final jupyter notebook, which has all the steps I made in creating the model.
