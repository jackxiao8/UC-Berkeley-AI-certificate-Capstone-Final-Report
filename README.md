# UC-Berkeley-AI-certificate-Capstone-Final-Report
capstone project final report

I.	Problem Statement: 
A churn of “YES” is for the case when a customer left the telecommunication service within the last month. It is a lost for the telecommunication company and the company usually will offer a promotion to keep the customer when they think the customers is probably to leave.
This project is to analyze the dataset of the customer account info and predict whether the customer will stay in the program. Two objectives.
1.	Analyze what factors affect the churn score significantly.
2.	Build a model to predict the churn score so that the company can do something to keep the customer.

II.	The dataset

The dataset contains the customer account information, service type, tenue, etc. https://www.kaggle.com/datasets/blastchar/telco-customer-churn?resource=download 
Context
"Predict behavior to retain customers. You can analyze all relevant customer data and develop focused customer retention programs." [IBM Sample Data Sets] Content Each row represents a customer, each column contains customer’s attributes described on the column Metadata. The data set includes information about:
•	Customers who left within the last month – the column is called Churn
•	Services that each customer has signed up for – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
•	Customer account information – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
•	Demographic info about customers – gender, age range, and if they have partners and dependents

III.	Data analysis summary
While the intuitive analysis on the plots can give us some rough ideas of each feature's importance, the correlation analysis can give us numerical evaluation of each feature influence, either positive correlation (toward churn score 1), or negative correlation (toward churn score 0).
•	In general, long tenure customers, 2 year contracts will stay longer with the program.
•	The customers without internet will stay longer, and on the opposite, the customers with fast fiber internet more likely to leave.
•	when the monthly charges is below $60 , churn score is low, and then increases from $60 to $100. and then decrease after $100. It means the low income and high income will more likely stay.
•	autopay will help keep the customers, and electronic check lead to high churn score. Surprisingly, the very traditional payment method, mailed check, lead to low churn score.

IVBaseline modeling conclusion
•	The features of the churn data set are analyzed through the plots and correlation analysis. The tenure, contract length, internet service and monthly charges play important roles in the churn score.
•	The data is cleaned and transformed for ML models. A Logistic Regression model is used for the intial training and prediction as the baseline. Its accuracy is about 80%.
•	More models will be tuned with grid search and compared for the final report. We expect to develop a model with 95% and higher accuracy so that the telecommunication company can do some special promotions to keep the customers with high churn scores.

V.	Final Modeling findings
•	The entire churn data sets are split to train data and test data.
•	5 models including logistic regression, knn, svc, decision tree, and random forest are trained based on the train data, and then to predict results for testing data. Combinations of parameters are searched for the best model parameters, by the tool, GridSearchCV. Model prediction accuracy and recall scores are compared.
•	It is noted that even with optimized model parameters, there is no significant improvement from the baseline model. For example, the model accuracy is about 80%, and the recall scores range from 44% to 58%. Since the company want to keep as many customers as possible, a recall score higher than 75% is desired.
•	Because the 5 models with optimized parameters trained with this small data set cannot give required recall score, lower thresholds for churn is used. By default, when the probabilities is higher than 50%, the churn score is considered as "YES". I lowered probabilities to 30% or 40% .
•	Both lower thresholds give better accuracy and recall scores. While 40% threshold give best accuracy, the 30% threshold gives the highest recall score, which is desired. So it is recommended to use 30% threshold for future model prediction.
•	Both logistic regression and random forest give the highest recall score (around 80%), while svc model gives the highest accuracy (98% for 40% threshold). Since high recall score is our goal, logistic regression and random forest are chosen for future model prediction.
•	The svc model takes significantly longer computation time than the other 4 models. The logistic regression and random forest give desired recall score, but the logistic regression model take even less time than the random forest model.

VI.	Next steps and recommendations
•	The logistic regression model is recommended for the churn score prediction, based on its high recall score, and less computation time.
•	The optimized model parameters for logistic regress model is {'logisticregression__C': 1}.
•	Lower threshold (30% probably to be consider churn='YES') is recommended.
•	Next step is to try the model with large data set, and also more features. It is expected the model accuracy and recall scores will be better.

