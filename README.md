# Predict_Sentiment_Class_For_Reviews

<h2 style="color:#333999;">Goal of the Project: To Predict if the Sentiment of Review is Positive or Negative.</h2>

## Problem Statement:
The business works and depends on reviews.
You have been hired by this marketing company to assess and predict the reviews that they have gathered on their products. Based on the review text provided, you need to predict whether the feedback has a positive or negative sentiment.
This will help guide decision-making for the firm, as they will want to deep dive into products and improve the feedback— thereby boosting the marketing firm’s reputation.

## Data Description:
### TRAIN.csv
It contains the training data of around 2598 rows with reviews and category as described below-
|Variable |Description|
|:--------|:----------|
|id       |	Unique identifier for each tuple.|
|text     | Tokenized text content of the review.|
|category	| The reviews have been categorized into two categories representing positive and negative reviews. 0 represents positive reviews and 1 represents negative reviews.|

### TEST.csv
It has review details for which the participants are to submit whether category would be positive or negative.

### Evaluation Metric
We will be using Precision_Score(Macro) as the Evaluation Metric to judge our models.


## APPROACH –
#### 1.	Importing of important Libraries
  We have used various important libraries for data reading using Pandas, Matplotlib for visualizations and various other libraries as mentioned with further steps below.

#### 2.	Data Loading & Understanding
   Train Data consists of 2598 Rows and 3 Columns (‘id’, ‘text’, ‘category’) and
   Test Data consists of 866 Rows and 2 Columns (‘id’ and ‘text’)


#### 3.	Exploratory Data Analysis
  a.	We dropped the column- ‘id’ from both Train and Test data as it is not useful for our model building.
  b.	There were NO NULL values in both the datasets.
  c.	We observed that there are 97% Positive Reviews and only 3% Negative Reviews, which also depicts that the customers are well satisfied with the company’s products.       The difference between the distributions of category of reviews can be observed as below.

<img src="sentiments_distribution.PNG" width=400 height=300 />

  d.	It can be easily noticed, that the data is unbalanced to predict wisely if the review can be negative or positive. So we will need to balance the data distribution using over-sampling techniques mentioned later.


#### 4.	Vectorizing the Categorical Variable
  As we know, all the ML models are good with numbers. So, we will convert the categorical column 'text' using CountVectorizer.
  It will convert the collection of text tokens in 'text' column, and return a matrix of the counts of occurrences of each token in the Series
  After Vectorizing, we observed the below dataset with mentioned shapes-

<img src="data_shapes.PNG" width=400 height=200 /> 


#### 5.	Train Test Split
  We have divided the training data into 70% of train data and 30% of validation data to test predictions of our different models on, and then select the best model for our final predictions on the main Test data.


#### 6.	Over-Sampling
  To predict if the review is negative or positive accurately, we need the data to be balanced enough to predict the correct category of the review.
  To optimize this imbalanced data, we will perform over-sampling using ADASYN (Adaptive Synthetic Sampling Approach)


#### 7.	Model Building
  We have used 5 different classification machine learning algorithms as mentioned below with obtained scores.

####  i. Support Vector Classifier
- Accuracy score :  94.87 %
- Recall_score(Macro) :  49.07 %
- Precision_Score(Macro) :  48.3 %

####  ii. Cat Boost Classifier
- Accuracy score :  88.08 %
- Recall_score(Macro) :  73.41 %
- Precision_Score(Macro) :  56.93 %

####  iii. XGB Classifier
- Accuracy score :  98.97 %
- Recall_score(Macro) :  84.62 %
- Precision_Score(Macro) :  99.48 %

####  iv. Decision Tree Classifier
- Accuracy score :  76.03 %
- Recall_score(Macro) :  76.46 %
- Precision_Score(Macro) :  54.46 %

####  v. Random Forest Classifier
- Accuracy score :  81.28 %
- Recall_score(Macro) :  73.61 %
- Precision_Score(Macro) :  54.8 %


#### 8.	Metrics Comparison & Generating Predictions
  As we can observe that, `XGBClassifier` gives better `Accuracy Score of 98.97%`, `Recall Score(Macro) of 84.62%` and `Precison Score(Macro) of 99.48%`.
  Let's continue with generating our final predictions on the Test data using <b>XGBClassifier</b> itself.


<big>
  The final predictions have been saved as a csv file named <b>“submission_xgb.csv”</b>
</big>
