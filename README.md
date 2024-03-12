# Practical Assignment III

## Bank Marketing Data

The data consists of a group of people that were contacted via phone about subscribing to a fixed-term deposit. There are about 45,000 observations with 17 features. source https://archive.ics.uci.edu/dataset/222/bank+marketing. There were 48 campaigns. The data consisted of demographic information of the customer and economic indicators.

|column|variable   |type         |description        |
|------|-----------|-------------|-------------------|
|1     | age       | numeric     | The client's age. |
|2     | job       | categorical | admin, unknown, unemployed, management, housemaid, entrepreneur, student, blue-collar, self-employed, retired, technician, services|
|3     | marital   | categorical | married, divorced, single; note: divorced means divorced or widowed. |
|4     | education | categorical | unknown, secondary, primary, tertiary |
|5     | default   | binary      | Has credit in default? |
|6     | balance   | numeric     | Average yearly balance in euros.|
|7     | housing   | binary      | Has housing loan? |
|8     | loan      | binary      | Has personal loan? |
|9     | contact   | categorical | Unknown, telephone, cellular |
|10    | day       | numeric     | Last contact day of the month. |
|11    | month     | categorical | Last contact month of year. |
|12    | duration  | numeric     | Last contact duration in seconds.|
|13    | campaign  | numeric     | Number of contacts performed during this campaign and for this client, includes last contact.|
|14    | pday      | numeric     | Number of days that passed by after the client was last contacted from a previous campaign, -1 means client was not previously contacted. |
|15    | previous  | numeric     | Number of contacts performed before this campaign and for this client.|
|16    | poutcome  | categorical | Outcome of the previous marketing campaign, unknown, other, failure, success.|
|17    | y         | binary      | Has the client subscribed a term deposit? |

## Business Problem
The business objective is to identify what features are the most important when determining if a customer will subscribe to a term deposit. How can the derived results be used to improve the amount of customers subscribing to the bank product. The target variable "y" indicates if the customer subscribed to the term deposit.

## Data Models
The problem requires classification of customers who most likely will subscribe to the bank product. There will be 4 models used to identify the characteristics of customers who are subscribed. They are:
* Logistic Regression - Excellent for finding linear relationships.
* Decision Trees - Easiest to intrepret with visualization.
* Support Vector Machines - Effective with high-dimensional data.
* K-Nearest Neighbors - Ideal for non-linear data.

## Process
A simple baseline model will be Logistic Regression because of its speed and interpretability. The models will be tuned using GridSearchCV to test which hyperparameters will create the most efficient model. Efficient meaning the optimal balance between training time and accuracy.

## Findings
There were some features that were more important to some models and less important to some other models. The Decision Tree model had the default status and age as the most important features. The logistic regression model had marital status and default as the largest coefficients. 
The decision tree model seemed to have bias towards the default status and age. This class was highly imbalanced with 79% of the class being no. The center of age distribution was at the 30 year olds, which also had the most subscribed customers of all age groups. This model is prone to bias towards dominant classes.
![Age Distribution Chart]()

The logistic regression model had marital status and default as it's largest coefficients. The marital status that had a better rate of subscribing was the married and divorced categories. The default status made sense because those who were cash deficient would not have any money to save in a term deposit.
![Marital Statuses Subscription]() ![LR Coefficients]()

The baseline models (default parameters) for K-Nearest Neighbor and Decision Trees had a problem with overfitting. They had really high training scores but when testing against unseen data. There was a 13% and 30% drop, respectively.

The tuning of the models only provided marginal increases listed in the table below. This helped with the overfitting models. The models used multiple cross-validation folds ranging from 5 to 10 and did not make a difference in the accuracy.

## Summary
The dataset was imbalanced and these machine learning models' accuracy prediction score suffered. There is a limit to how well these models perform when the feature relationship is non-linear. The KNN and SVM were expected to do well with non-linear relationships but performed average. Tuning the hyperparameters only marginally increased accuracy. These models are the wrong tools for this type of data. A neural network would be the best tool for uncovering the non-linear relationships and not easy patterns from this data.

The feature relationships are non-linear and are difficult for these models to make accurate predictions. Using a Neural Network will help identify patterns and relationships from this data. A artificial neural network will be able to work with incomplete knowledge.

It is recommended that the marketing team focus on using the most important metrics; age, marital and campaigns. The age groups that were 
most subsribed were the 30 - 40 age range. The marital category that were most subscribed was the married and divorced. The majority of customers that subscribed were made with less than 5 contacts. I suggest the marketing team create a marketing campaign targeting the 30 to 40 age range, who are married or previously married, with a limit of 5 contacts per customer.

[Link to notebook](github.com)