Startup’s Acquisition predictor


Project Description
This project specifically focuses on finding an alternative method to predict a Startup’s acquisition status based on its financial statistics by using different machine learning techniques.
Financial information about the firms, including total funding, funding dates, total number of fundraising rounds, and headquarters location, is fed into the resulting algorithm. The system then makes a prediction on whether the startup has been closed down, acquired, is still running, or has achieved an IPO. Dealing with an unbalanced dataset where one class is overrepresented and under/oversampling cannot be used as a method to balance the data is the key challenge for this issue. We used an ensemble-based technique to address this.
Dataset:
In this project we have used the data collected from Crunchbase 2013
Each row of combined dataset contains information like: ‘id’, ‘Unnamed: 0.1’, ‘entity_type’, ‘entity_id’, ‘parent_id’, ‘name’, ‘normalized_name’, ‘permalink’, ‘category_code’, ‘status’, ‘founded_at’, ‘closed_at’, ‘domain’, ‘homepage_url’, ‘twitter_username’, ‘logo_url’, ‘logo_width’, ‘logo_height’, ‘short_description’, ‘description’, ‘overview’, ‘tag_list’, ‘country_code’, ‘state_code’, ‘city’, ‘region’, ‘first_investment_at’, ‘last_investment_at’, ‘investment_rounds’, ‘invested_companies’, ‘first_funding_at’, ‘last_funding_at’, ‘funding_rounds’, ‘funding_total_usd’, ‘first_milestone_at’, ‘last_milestone_at’, ‘milestones’, ‘relationships’, ‘created_by’, ‘created_at’, ‘updated_at’, ‘lat’, ‘lng’, ‘ROI’.
Data pre-processing
A. Data Cleaning
1.	Delete irrelevant & redundant information
2.	Remove noise or unreliable data (missing values and outliers)
1. Delete irrelevant and redundant information
•	Delete ‘region’,‘city’,‘state_code’ as they provide too much of granularity.
•	Delete ‘id’, ‘Unnamed: 0.1’, ‘entity_type’, ‘entity_id’, ‘parent_id’, ‘created_by’, ‘created_at’, ‘updated_at’ as they are redundant.
•	Delete ‘domain’, ‘homepage_url’, ‘twitter_username’, ‘logo_url’, ‘logo_width’, ‘logo_height’, ‘short_description’, ‘description’, ‘overview’,‘tag_list’, ‘name’, ‘normalized_name’, ‘permalink’,‘invested_companies’ as they are irrelevant features.
•	Delete duplicate values if any.
•	Delete those which has more than 98% of null values. As we mention before there were some columns which had more than 95% of null value so, if we fill the missing values it will give us the wrong accuracy.
2. Remove noise or unreliable data
•	Delete instances with missing values for ‘status’, ‘country_code’, ‘category_code’ and ‘founded_at’.
•	Delete outliers for ‘funding_total_usd’ and ‘funding_rounds’.
•	Delete contradictory (mutually opposed or inconsistent data).
•	Remove the duplicate data
Feature Enginerring
•	Considered the suitable features for the model based upon the combined result of model performance and exploratory data analysis.
•	Encoded features like Country_code, and Catogery_code.
•	Created additional features like isClosed and active_days

How we handle Data Imbalalance?
Imbalalance data can sometime affect our models performance and can bring biasness in our models performance. For e.g. In case of our data if we didn’t handle the imbalance data then we might end up building a bias model with a lot of false positive value. That’s quiet a problem. So we need to handle the imbalance dataset using
1.	Undersampling of majority class label.
2.	Oversampling of minority class label
3.	Using SMOTE Technique which adds synthetic datapoints to our minority class label in order to balance the number of data points in each classes.
•	Outliers
•	Relationship between Independent and dependent feature


Solution Appraoch
Since we have a multiclass imbalanced classification problem, we decided to break it down into subproblems. To do this, we first classified the startup’s running state based on the “isClosed” column, and then we used the appropriate classification algorithms to predict the actual class based on the output of this classification.

Description of the first level Model
We used Logistic Regression as the first level classifier algorithm to train our dataset. After doing the necessary EDA and DataPreprocessing we splitted our dataset into train and test set. After that we scaled the training and validation data using min_max_scaler. After training the model we tested the model on our validation dataset and we achieve the accuracy nearly 98,6%.

Description of the second level classifiers
Since we had two subproblems to be solve at level-2 therefore we have used various machine learning algorithms on filtered data.

We have tried different models i.e., Logistic Regression, naive_bayes, SVC
Classifier, DecisionTree Classifier. And from that we select Bagging Classifier as our final model for running_startup. As rest of the models are predicting bias towards operating only so we decided to go for DecisionTree  Classifier.
Deployment

You can access our Django based web-app by following this link PredAqui.
Django: Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.




