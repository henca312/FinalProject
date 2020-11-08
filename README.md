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

### Principal Component Analysis
Regarding the customer segmentation report i've used Principal Component Analysis to reduce the number of features.
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/PCA.png?raw=true)
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/Explained%20Variance%20by%20Features.PNG?raw=true)

### Elbow Method - How many clusters?
![alt text](https://github.com/henca312/FinalProject/blob/main/Images/ELBOW.png?raw=true)





Conclusion
==========

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







