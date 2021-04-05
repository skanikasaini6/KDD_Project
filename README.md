**Project on Walmart: Store Sales Forecast**</br>

**Group Name:**</br>
   Outliers</br>
   
**Group Members:**
1. Ankit Kejriwal
2. Herleen Kaur Sanhotra
3. Kanika Saini
4. Sindhura Sadam

**Datasource:**

https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting

**Introduction to the Dataset:**

We are working on retail data taken from Kaggle. The dataset contains records of 2 years of data collected from 45 different Walmart stores for time period 5/2/2010 to 1/11/2012. We are working with 4 datasets train, features, stores and test(for testing our models). 

**Train dataset contains the following predictors:**

Store - the store number</br>
Dept - the department number</br>
Date - the week</br>
IsHoliday - whether the week is a special holiday week</br>
Weekly_Sales -  sales for the given department in the given store

**Features dataset contains the following predictors:**

Store - the store number</br>
Date - the week</br>
Temperature - average temperature in the region</br>
Fuel_Price - cost of fuel in the region</br>
MarkDown1-5 - anonymized data related to promotional markdowns that Walmart is running. MarkDown data is only available after Nov 2011 and is not available for all stores all the time. Missing values are marked as NA.</br>
CPI - the consumer price index</br>
Unemployment - the unemployment rate</br>
IsHoliday - whether the week is a special holiday week

**Stores dataset contains the following predictors:**

Store - the store number</br>
Size-size of store</br>
Type-type of store

**Goal/Target variable:**

Our aim is to predict the Weekly Sales. Therefore, Weekly_Sales is our target variable on which we will test the effects of other predictors.

**Defining Cross-Industry Standard Process For Data Mining:**

<p align="center"> 
    <a href="#">
        <img src="CRISPDM_Process_Diagram.png" height="50%" width="50%">
    </a>
</p> 

According to the Cross-Industry Standard Process For Data Mining, a data mining project life cycle consist of six phases. The phase sequence is adaptive. That is, the next phase in the sequence often depends on the outcome associated with the previous phase.
The six phases are:</br>

***Business Understanding:***

Our dataset is focused on predicting weekly sales from data collected from 45 Walmart stores. There are different predictors that can have an effect on our target variable. Usually, during holidays people go out more for grocery shopping, so sales are expected to increase during those holiday weeks. We explored what kind of correlations does this particular predictor have on our target variables. One of the most interesting insights in the dataset to dwelve into was how markdowns play a role with the weekly sales. Markdowns are nothing but promotional sales for different time periods. Naturally the sales for these time period is going to be higher and will profit the stores. 

***Data Understanding:***

The main objective was to forecast weekly sales for each department in 45 Walmart stores located in different regions and also to carry out statistical testing and validation of the models which features DataPreprocessing, Exploratory Data Analysis, modeling on train dataset.

1.	Features.csv
2.	Stores.csv
3.	Train.csv

Features: Dataset contains historical data of 45 stores in different regions for a period of 2 years. It includes major markdown events that happen throughout the year like Christmas, Labour Day, Thanksgiving, Super bowl. Other features like IsHoliday, Date, Fuel_Price can be used in Hypothesis. 
           For Example the effect of sales during holiday seasons on each store on a weekly basis
        
Stores: Dataset contains information on 45 stores like Type of store and Size(in sqft) of the store.

Train: Dataset contains historical train data on which the model is trained. Features included are Store number, Department number, Date which is the date of the week we are predicting the sales. Weekly_sales for the given department in the given store, and Is_holiday
        Example Hypothesis: Predicting Department wise sales for each store
        
***Data Preparation/Preprocessing:***

*	Importing Features, Stores,dt1 datasets into jupyter notebook
*	Understanding information provided in the datasets and looking for types of columns and missing values.
*	Converted Datatype of Date column to DATETIME from OBJECT
*   Checked for null values in all the data frames. We found that there are close to 4500 null values in the MARKDOWN's column and 585 null values in the CPI and Unemployment columns. Markdowns 1-5 have a lot of missing values since these markdowns contain values of only particular holiday weeks.
*   Imputed the null value in the CPI and Unemployment column with the mean value of the column
*   Imputed the null value in the MARKDOWN's column with 0
*	Left joined the dt1 dataset with the Stores dataset based on the 'Store' column
*	Left joined the resulting dataset with features dataset using the common predictors 'Store', 'Date', 'IsHoliday'
*	Now we have a single dataset with all the columns required for Exploratory Data Analysis.
*  Standardizing the features in the Dataset to balance the variance between the features. If the features are not normalized on to a single scale, the model might be biased towards high variance features. Bias can be mitigated by transforming original dataset.
* Using the Date column from the final dataset, we created two new columns
    1. Year
    2. Week - gives the info about what week of the year it is.
*  We have 3 types of stores (A, B and C) which are categorical. Therefore we split each type as a feature into one-hot encoding.
* We performed the one-hot encoding for three more columns('IsHoliday', 'Week','Year')
* Now our dataset is ready for modeling

***Modeling:***

After the data pre-processing phase, we have implemented the supervised learning algorithms to make the predictions for WeeklySales. Various regression techniques like Linear Regression, Elastic Net Regression, Lasso Regression, Ridge Regression were implemented. Also, we used the Random Forest Regressor ensembling method to enhance the model results. 


Algorithms explained:
Model 1:  Linear Regression is used for finding a linear relationship between the target and one or more predictors. 

R-Squared value
This value ranges from 0 to 1. Value ‘1’ indicates predictor perfectly accounts for all the variations in Y. Value ‘0’ indicates that predictor ‘x’ accounts for no variation in ‘y’.
The model performance for training set: 0.09827663017855981 

RMSE is 0.9524624955038273

As shown, RMSE is high and R2 accuracy score is low for the model. This indicated model is not better performing and clearly, there is some overfitting.
So we tried to choose the best subsets as our predictors. Ridge and Lasso Regression are some of the simple techniques to reduce model complexity and prevent over-fitting which may result from simple linear regression. Ridge Regression: In ridge regression, the cost function is altered by adding a penalty equivalent to the square of the magnitude of the coefficients.

Model 2:
Lasso Regression: The goal of lasso regression is to obtain the subset of predictors that minimizes prediction error for a quantitative response variable. The lasso does this by imposing a constraint on the model parameters that causes regression coefficients for some variables to shrink toward zero.

The model performance for the training set:
RMSE is 0.9652534025602325

R2 score is 0.07389497585513038

Unfortunately, this model gave us high RMSE and R2 score, hence cannot be chosen as the best model.

Model 3:
Ridge Regression: Ridge Regression is a technique for analyzing multiple regression data that suffer from multicollinearity. ... By adding a degree of bias to the regression estimates, ridge regression reduces the standard errors. It is hoped that the net effect will be to give estimates that are more reliable.

The model performance for the training set:

RMSE is 0.9524627207560741

R2 score is 0.09827620367307532

Unfortunately, this model gave us high RMSE and R2 score, hence cannot be chosen as the best model.

Model 4:
Elastic Regression: In statistics and, in particular, in the fitting of linear or logistic regression models, the elastic net is a regularized regression method that linearly combines the L1 and L2 penalties of the lasso and ridge methods.

RMSE is 0.9824627207560741

R2 score is 0.02827620367307532

Unfortunately, this model gave us high RMSE and R2 score, hence cannot be chosen as the best model.

Model 5:
Decision Tree Regression: Decision tree regression observes features of an object and trains a model in the structure of a tree to predict data in the future to produce meaningful continuous output.

We observed Mean Square Error and Root Mean Square error as 0.0857625, 0.23749489

Model 6:
Random forest regression:
A Random Forest is an ensemble technique capable of performing both regression and classification tasks with the use of multiple decision trees and a technique called Bootstrap Aggregation, commonly known as bagging. Bagging, in the Random Forest method, involves training each decision tree on a different data sample where sampling is done with replacement.

This particular model yields an RMSE value of 0.19.

It is observed that among the 6 models applied Decisiontreeregressor and RandomForestRegression are better yielding models with Rmse error relatively lower than the rest of the 4 models.


***Evaluation:***

All the models that were built were evaluated using the R2 (Determination), MSE(Mean Score Error), RMSE(Root Mean Square Error), MAE(Mean Absolte Error). The higher the R2 value, the more accurate the model is. In the same way, lower the error metrics value,  more accurate the model is. 

Goal: higher R2 value and low error metrics. 

Metrics that were used to evaluate our models were:

RMSE:
The RMSE for your training and your test sets should be very similar if you have built a good model. If the RMSE for the test set is much higher than that of the training set, it is likely that you've badly overfitted the data, i.e. you've created a model that tests well in a sample, but has little predictive value when tested out of sample.

R2:
R-squared (R2) is a statistical measure that represents the proportion of the variance for a dependent variable that's explained by an independent variable or variables in a regression model. So, if the R2 of a model is 0.50, then approximately half of the observed variation can be explained by the model's inputs. R-squared values range from 0 to 1 and are commonly stated as percentages from 0% to 100%.

Cross-Validation :
Cross-Validation is used to assess the predictive performance of the models and to judge how they perform outside the sample to a new data set also known as test data. The motivation to use cross-validation techniques is that when we fit a model, we are fitting it to a training dataset. The procedure has a single parameter called k that refers to the number of groups that a given data sample is to be split into. Cross-Validation is a very useful technique for assessing the effectiveness of your model, particularly in cases where you need to mitigate over-fitting.

Validating performance of DecisionTree Regression and Random Forest Regressor which yielded low RMSE error value.

5 fold cross validation on Decision tree Regression:
5 fold cross vaidation score: [0.94428852 0.94733705 0.94651084 0.94297185 0.96514304]

Mean score: 0.9447009229122203

5 fold cross-validation on Random forest Regression:
5 fold cross vaidation score: [0.9600374 0.96511895 0.96494218 0.96842691 0.94239636]

Mean score: 0.9647339229122203

***Optimization/Deployment:***

The result was optimized using GridSearchCV or RandomSearchCV where the best hyperparameters are chosen for the algorithm by checking out all possible values in the grid.

***Conclusion***

For this project we have done several visualizations to dig deeper into the dataset. We find out various correlations between the features and the target variable. The unique thing about our data is that apart from Weekly Sales we have extra sales during promotional period. Few attributes including the target variable , had imbalanced class. We handled it using the stratify parameter while splitting the dataset. As part of data preprocessing, two new columns "Year" and "Week" were added. Outliers were detected using the box plots. We implemeted many algorithms : linear regression, ridge regression, lasso regression, elastic net regression , decision tree regressor, and random forest regressor. Among these, the first four algorithms did not perform very well. They gave a very low accuracy. The last two algorithms performed well, among which Random Forest Regressor gave the best performance. 
One challenge we faced with the dataset was the huge number of records. Algorithms like Random Forest and decision tree took a lot time to run. Same was the case with GridSearchCV. We ran the algorithms on Google Colab to solve the problem.
For future work, this project can be added with more features making the dataset more rich in features. For the new individuals to continue this project, it is important to understand the meaning of all the features before going ahead with the prediction. For example, the attributes like markdowns should be understood well as they might be misunderstood as something else. Also, it can be implemented on Microsoft Azure and other machine learning algorithms can be tried out for better results.
This project thus predicts the Weekly sales inspite of the challenges that we faced and using the best model created.
