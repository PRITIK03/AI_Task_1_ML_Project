# AI Task 1 - Machine Failure Prediction Project

## Understanding the Data

In this project, I worked with a dataset of 10,000 industrial machine operations. Each record tells us what happened during a machine operation, specifically whether the machine failed or not. The dataset includes 6 features:  
- Air temperature  
- Process temperature  
- Rotational speed  
- Torque  
- Tool wear  
- Machine type  

The target variable is binary: 1 for failure and 0 for no failure. The biggest challenge was the class imbalance—97% of the records were "no failure," and only 3% were "failure." This means the model could easily cheat by always predicting "no failure" and still get high accuracy, which is not useful in real life.

## Preprocessing and Feature Handling

To prepare the data for modeling, I did the following steps:  
- Removed the UDI, Product ID, and Failure Type columns because they didn’t help predict failures and could leak information.  
- Encoded the machine type (L, M, H) into numbers (0, 1, 2) so the model could use it.  
- Scaled all numeric features using StandardScaler to make sure no feature dominated the others.  
- Split the data into 80% for training and 20% for testing, using stratified sampling to keep the same proportion of failures in both sets.  
- Handled the class imbalance by using class weights and cross-validation to make sure the model learned from both failures and non-failures.

 Why I Chose These Models

I picked three models for this project:  
- **Logistic Regression:** This is a simple, easy-to-understand model that gives us a baseline. It’s good for seeing if there are clear patterns in the data.  
- **Random Forest:** This model is more complex and can capture non-linear relationships. It’s also robust to class imbalance and gives us feature importance.  
- **Soft-Voting Ensemble:** This combines both models by averaging their predictions. It helps reduce the risk of relying on just one model and usually gives better results.

 How I Evaluated the Model

I didn’t just use accuracy because it’s misleading with imbalanced data. Instead, I used:  
- **ROC-AUC:** This metric is good for imbalanced data because it measures how well the model ranks failures higher than non-failures, regardless of the threshold.  
- **F1-Score, Precision, and Recall:** These metrics help balance the trade-off between catching failures (recall) and avoiding false alarms (precision).  
- **Cross-Validation:** I used 5-fold cross-validation to make sure the results were reliable and not just luck.  
- **Class Weights:** I balanced the classes so the model paid more attention to failures.

 What I Would Improve with More Time

If I had more time, I would:  
- Try SMOTE to create more failure examples and balance the data better.  
- Use GridSearchCV to find the best settings for the models.  
- Create new features, like combining speed and torque, to find hidden patterns.  
- Test more models, like XGBoost or SVM, to see if they perform better.  
- Look at time-series patterns if the data had timestamps.  
- Deploy the model in a real factory and keep improving it with new data.



This project helped me practice handling real-world challenges like class imbalance and choosing the right metrics. I also learned how to explain my decisions clearly, which is important for working on real projects.
