# Capstone Project
## Udacity's Data Scientist Nanodegree

### Project overview
This is my Capstone Project for Udacity's Data Scientist Nanodegree and it is about a fictional music streaming company 
called Sparkify, similar to companies like Spotify and Pandora. In this project, we will go through how to manipulate a 
big dataset to engineer relevant features for predicting customer churn and build and evaluate machine learning models 
using Apache Spark’s PySpark API and PySpark ML Package.

The dataset (*'medium-sparkify-event-data.json'*) comes in the form of a JSON file that contains 543 705 samples of event 
log data for October-December 2018 form Sparkify's platform. A smaller subset of this datset (not included here) has been 
used to make an inital analysis on my local machine, check out the files *'Sparkify_mini.ipynb'* and *'Sparkify_mini.html'*
to see this prior analysis that a lot of the feature engineering and modeling decisions have been based on. The main 
Jupyter notebook, files *'Sparkify_medium.ipynb'* and *'Sparkify_medium.html'*, has been run in a spark environment 
directly on the IBM Watson Studio platform.

**An accompanying blog post that takes you through the process of this project can be [found here](https://medium.com/@linn.ohlsson/predicting-customer-churn-with-apache-sparks-pyspark-api-9c941af67a59).**

### Problem statement
Customer Churn is one of the most important metrics for businesses to evaluate. It is the percentage of customers 
that stopped using your company’s product or service during a certain time frame. This is important to keep track of 
because it costs more to acquire new customers than it does to retain existing customers. The goal of this project is to 
help Sparkify build a machine learning model that can predict when it is likely that a customer is going to churn, to be 
able to take action on this and prevent customers from canceling their accounts. This kind of prediction model involves a 
binary classificaion problem, where a user can belong to one of two classes, churned or not churned (still active). To
solve this problem we need to do some rigorous data exploration and pre-processing, including:
- define what churn is
- explore how churned and active users differ across different data
- find columns of interest to use in modeling, and create new features based on available data (feature engineering)
- select which features are most suitable in modeling (feature selection)
- test different classification models to see how well suited they are
- define evaluation metrics to use to measure model performance on this dataset correctly
- tune hyperparameters to explore how we can improve model performance
- evaluate the model performance and functions
- discuss how to make further model improvements

### Installations
Reguired installations:
- Jupyter Notebooks (Anaconda Distribution)
- Python 3.6.7

Required packages:
- PySpark 2.4.4 (PySpark.sql and PySpark.ml)
- NumPy
- Pandas
- Datetime
- Matplotlib
- Seaborn

### Reflection
To summarize this project, I built a Random Forest classifier to predicts customer churn based on event log and user data.
I recoded multiple variables related to event logs into new frequency variables per user, to be able to restructure the 
model input data to one row per unique user instead of one row per event. I only used the most recent event row per user to get
the most updated data. We turned categorical columns into indices, one hot encoded them to separate numerical binary columns, scaled all 
numerical features using MinMaxScaler, and transformed all input features to one single vector to use in modeling. We tested
various classifiers as baseline models without any hyperparameter tuning, selected the best performing baseline model, which
was a Random Forest classifier, and tuned its hyperparameters to improve its performance. Finally, we explored how to explain
the model by looking at feature importances and their predictive power.

This project was challenging and fun because I have never used Apache Spark previously, the code and functions are different, and
it was very useful to learn how to work with analytics and machine learning in a big data setting. Debugging was a bit challenging
because the error messages are hard to interpret in Spark, and it took me a while to figure out why I could not join the tables
where I had recoded new variables to the dataset. I figured out after much debugging that it was most likely due to not caching the dataframes before joining them,
and that some variables had missing data in them that messed up the join function.

### Acknowledgements
The *'medium-sparkify-event-data.json'* dataset has been provided by [Udacity](https://www.udacity.com/).
