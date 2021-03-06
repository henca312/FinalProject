Capstone Project Arvato Bertelsmann with Udacity
==========

![alt text](https://www.roadtovr.com/wp-content/uploads/2017/10/udacity-logo.png)


![alt text](https://www.bertelsmann.de/media/news-und-media/logos/sg-logo-afs_teaser_2_3_lt_768_retina.gif)

**Link Blog Post**: 
[Go to the Blog Post](https://hendrik-carius.medium.com/the-final-step-to-become-a-data-scientist-nanodegree-capstone-project-arvato-bertelsmann-cc7fee5f286)

**Link Git Hub**: 
[Go to Github](https://github.com/henca312/FinalProject/)


**Readme**
==========
- Project Motivation
- Summary of results
- Conclusion
- Installations
- File Descriptions
- Acknowledgments

Project Motivation
==========
In this project i'am going to use all my gained knowledge while doing the data scientist nanodegree at udacity in the Capstone Project. I've started my journey as a Business Intelligence Consultant a few years ago. Several projects and years past. One day i’ve reminded me of the experience i’ve gained and the power of business analytic tools. A few months ago i’ve started my data scientist nanodegree to discover the whole potential of analytical techologies. Now the time has come to put all together what i’ve learned in this course.

The project is separated into different phases:
1 What is going on? Get to know the data!
2 Customer Segmentation Report
3 Supervised Model
4 Kaggle Competition
To have a solid and well known project structure i’ve used the CRISPDM process (https://datasolut.com/crisp-dm-standard/) to accomplish all of these tasks. The CRISPDM process contains the following phases:

| Phase  | Content |
| ------------- | ------------- |
| 1  | Business Understandning  |
| 2  | Data Understanding  |
| 3 | Data Preparation |
| 4 | Data Modeling |
| 5 | Evaluation |
| 6 | Deployment|

Summary of results
==========
Based on the 6 Phases of the CRISPDM process i would like to describe the results.
## Business Understanding
The key interest of business is the question:
> How can the client, the mail order company acquire new clients more efficiently?

A customer from Bertelsmann arvato is doing mail out campaigns. Therefore it is necessary to understand the different customer. 
Why? If we would adress a mailout campaign to "everyone" would mean high cost and low effectiveness because not everyone is not interested in everything.
So there is a need to understand the potential customer base (General Population data from germany) and to understand the current customer base from the Mailout Campaign.

To answer this question we've identified several sub aspects:
> * Analyze Attributes & the demographic of the existing clients 
> * Analyze Attributes of the demographics of the new clients
> * Figure out, which people from the big data set are most likely new customers for the client, the mail order company selling organic products

## Data Understanding
Arvato provided two files containing data for the general population in germany and data for the existing clienst customer base.
To undestand the data we've focused on 4 tasks:
> * Get an overview of the azdias data: Look at null values
> * Get an overview of the customers data: Look at null values
> * Results: Look at null values
> * Get an overview of the data: Compare distinct values
### Null Values at Azdias
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Azdias_Null_Value.png?raw=true)
### Null Values at Customers
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Customers_Null_Value.png?raw=true)
### Null Value Comparison
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Null%20Value%20Comparison.png?raw=true)
### Comparison distinct values
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/CompareDistinctValues.png?raw=true)

## Data Preparation
After we've successfully analyzed the data there is a need to handle null values, missing values and categorical values.
I've made the following decisions:

> * Decision: Drop all columns with > 65 % null values
> * Decision: Drop all columns from the customers database that are only available in the customers database
> * Decision: Removing highly correlating features
> * Deicision: Replace all nan values in numerical columns with corresponding values from the attributes list provided
> * Decision: Replace all nan values in catagorical columns with corresponding values from the attributes list provided
> * Decision: Create dummies for catgegorical columns
> * Decision: Using Multivariate Imputation by Chained Equation for Imputing all missing / nan values
> * Decision: Converting & remove Outliers based on the Z Score
> * Decision: Standardize data with Standard Scaler

Too make several parts of the decisions reusable i've created a PrepareFunction.

## Data Modeling
Now that we have cleaned data and no missing values anymore we can start with the Data Modeling.

### Customer Segmentation Report

#### Principal Component Analysis
Regarding the customer segmentation report i've used Principal Component Analysis to reduce the number of features.
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/PCA.png?raw=true)
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Explained%20Variance%20by%20Features.PNG?raw=true)

#### Elbow Method - How many clusters?
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/ELBOW.png?raw=true)

#### Cluster Analysis
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Analyze%20Cluster.png?raw=true)


### Supervised Learning Model
The next part of the project was to develop a supervised Learning Model based on a given test data.
We developed the model on the train database and evaluate it with test data.

Based on the business context we need to understand the problem. We want to predict if a customer has responeded to a campaign or not. This can be described as a multi-class classification problem. A multinomial classification is the problem to classify instances into classes. In this case we have to classify:
* 1: Customer has responded
* 0: Customer has not responded

#### Checking the distribution of the target variable
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Target%20Value%20Distribution.png?raw=true)

#### First Run Model Selection
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Model%20First%20run.png?raw=true)

#### Second Run Model Selection
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Model%20Second%20run.png?raw=true)

#### Model Comparison
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Model%20Comparison.png?raw=true)

#### Grid Search
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Grid%20Search.png?raw=true)

#### Feature Importance
##### Weight
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/weight.png?raw=true)
##### Cover
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/cover.png?raw=true)
##### Gain
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/gain.png?raw=true)
##### Summary
From the comparison of the feature importance based on different metrics we can see that the feature D19_Soziales is number 1 feature with regard to gain score and number 2 feature with regard to cover and weight.
Because of the fact that Gain score is the most relevant attribute to interpet the relative importance of a feature we can conclude that D19_Soziales is the most important feature to predict if a customer respond to a certain campaign.

Conclusion
==========
The goal of the project was to answer the following business question:
> How can the client, the mail order company acquire new clients more efficiently?

Within the first step we've done a Principal Component Analysis to reduce the number of features.
We have identified 205 Features that explaines alsmost 99 % of the variance within the dataset.
What does that mean? The Mailorder Company can focus on the identified 205 Features to maybe rethink their strategy for a mailout campaign.
Because of the fact that there are 205 Features that explains 99 % of the variance the company could gathering more detailed data for these 205 features to even better identify customer segments.

The elbow method has shown that we mainly have 4 customer segments. Within these 4 segments we've found out, that there is a underrepresenation of cluster 2 within the customers data base and an overrepresentation of cluster 3 in the azdias database. What does that mean? The Mailorder Company should focus on these two clusters. 
Especially in cluster 3 there might be some potential new customers for the Mailorder Company. The company only captures a small part of this cluster in their database. In cluster 2 there is a strong overrepresentation in the customers database. This means that there are more customers that relates to this cluster compared to the azdias data. 

When developing the Supervised Learning Model we achieved an ROC AUC score between 0.81 to 0.879 with the XGBoost Classifier. The ROC curve is used to evaluate the classification performance. The misclassification rate is determined for a given set of instances, belonging to those instances for which the classifier is most reliable.. The optimal roc auc score value would be 1. The customer could use the developed kind of model to identify customers that will respond to a specific mailout campaign. So it would be possible to better define the target group and reduce cost for doing campaigns. The most relative important feature is "D19_Soziales". This feature has the heighest impact to the response of a customer. This means the mailorder company can focus on analysis on this feature for the different customer clusters to find the best way to acquire new customers.


Installations
==========
The following packages were used in this python project:
* numpy 
* pandas
* matplotlib.pyplot
* seaborn 
* time
* dask 
* sklearn.decomposition
* sklearn.metrics 
* sklearn.model_selection  
* xgboost.sklearn   
* xgboost  
* sklearn.cluster  
* sklearn.preprocessing 
* scipy 
* fancyimpute 


File Descriptions
==========
The following files are being provided by udacity. In this git i'am only sharing my python notebook with the results.
* Udacity_AZDIAS_052018.csv: Demographics data for the general population of Germany; 891 211 persons (rows) x 366 features (columns).
* Udacity_CUSTOMERS_052018.csv: Demographics data for customers of a mail-order company; 191 652 persons (rows) x 369 features (columns).
* Udacity_MAILOUT_052018_TRAIN.csv: Demographics data for individuals who were targets of a marketing campaign; 42 982 persons (rows) x 367 (columns).
* Udacity_MAILOUT_052018_TEST.csv: Demographics data for individuals who were targets of a marketing campaign; 42 833 persons (rows) x 366 (columns).
* Arvato Project Workbook.ipynb




Acknowledgments
==========
Time is passing by and i'am very happy successfully finished the project. Now it is time to say thank you.

> Thank's a lot to my company providing me the possibilitie to spend time on learning new things. Thank's a lot to udacity and the employees, especially the various reviewers reviewing several projects and awnsering questions. Also a big thank you to the great content and the way it's presented to udacity, that provides such great courses.
Thank also to the my colleagues at work, for supporting me the whole time and providing me feedback for some really complicated technical questions.



