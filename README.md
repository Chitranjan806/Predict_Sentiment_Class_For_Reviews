# Predict_Sentiment_Class_For_Reviews

## Goal of the Project: To Predict if the Sentiment of Review is Positive or Negative.

## Problem Statement:
The business works and depends on reviews.
You have been hired by this marketing company to assess and predict the reviews that they have gathered on their products. Based on the review text provided, you need to predict whether the feedback has a positive or negative sentiment.
This will help guide decision-making for the firm, as they will want to deep dive into products and improve the feedback— thereby boosting the marketing firm’s reputation.

## Data Description:
### TRAIN.csv
It contains the training data of around 2598 rows with reviews and category as described below-
|Variable   |Description|
|:----------|:----------|
|`id`       |	Unique identifier for each tuple.|
|`text`     | Tokenized text content of the review.|
|`category`	| The reviews have been categorized into two categories representing positive and negative reviews. 0 represents positive reviews and 1 represents negative reviews.|

### TEST.csv
It has review details for which the participants are to submit whether category would be positive or negative.

### Evaluation Metric
We will be using `Precision_Score(Macro)` as the Evaluation Metric to judge our models.


## Important Approach Points –

  1. While performing Exploratory Data Analysis, we found that the given data is highly unbalanced with **97% positive reviews** w.r.t to just **3% negative reviews.**

  <img src="sentiments_distribution.PNG" width=400 height=300 />
  As noticed from the above distribution graph, the dataset is highly unbalanced and we will need to balance the data to overcome biasness.
  <br><br>

  **2.	Vectorizing the Categorical Variable**
  
  As we know, all the ML models are good with numbers. So, we will convert the categorical column `'text'` using **CountVectorizer.**<br>
  It will convert the collection of text tokens in 'text' column, and return a matrix of the counts of occurrences of each token in the Series
  After Vectorizing, we observed the below dataset with mentioned shapes-

  <img src="data_shapes.PNG" width=450 height=150 /> 
  <br><br>

  **3.	Over-Sampling**
  
  To predict if the review is negative or positive accurately, we need the data to be balanced enough to predict the correct category of the review.<br>
  **To optimize this imbalanced data, we will perform over-sampling using `ADASYN (Adaptive Synthetic Sampling Approach)`**


  **4.	Model Building**
  
  We have used 5 different classification machine learning algorithms as mentioned below with obtained scores.

  |Algorithm                |Accuracy score |Recall score(macro) |Precision score(macro) |
  |:------------------------|--------------:|-------------------:|----------------------:|
  |Support Vector Classifier|94.87 %        |49.07 %             |48.30 %                |
  |Cat Boost Classifier     |88.08 %        |73.41 %             |56.93 %                |
  |XGB Classifier           |98.97 %        |84.62 %             |99.48 %                |
  |Decision Tree Classifier |76.03 %        |76.46 %             |54.46 %                |
  |Random Forest Classifier |81.28 %        |73.61 %             |54.80 %                |

  <br>
  
  **5..	Metrics Comparison & Generating Predictions**
  
  As we can observe that, `XGBClassifier` gives better `Accuracy Score of 98.97%`, `Recall Score(Macro) of 84.62%` and `Precison Score(Macro) of 99.48%`.<br>
  Let's continue with generating our final predictions on the Test data using <b>XGBClassifier</b> itself.
