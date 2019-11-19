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

We are working on retail data taken from Kaggle. The dataset contains records of 2 years data collected from 45 different Walmart stores for time period 5/2/2010 to 1/11/2012. We are working with 4 datasets train,features,stores and test(for testing our models). 

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
MarkDown1-5 - anonymized data related to promotional markdowns that Walmart is running. MarkDown data is only available after Nov 2011, and is not available for all stores all the time. Missing values are marked as NA.</br>
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
        <img src="https://www.ibm.com/support/knowledgecenter/SS3RA7_15.0.0/com.ibm.spss.crispdm.help/images/crisp_process.gif" height="50%" width="50%">
    </a>
</p> 

According to the Cross-Industry Standard Process For Data Mining, a data mining project life cycle consist of six phases. The phase sequence is adaptive. That is, the next phase in the sequence often depends on the outcome associated with the previous phase.
The six phases are:</br>

***Business Understanding:***

Our dataset is focused on predicting weekly sales from data collected from 45 walmart stores. There are different predictors that can have an effect on our target variable.Usually, during holidays people go out more for grocery shopping, so sales are expected to increase during those holiday weeks. We will explore what kind of correlations does this particular predictor have on our target variables. We would also like to know if unemployement rate around a particular store has any drastic effect on the sales of that store. Unemployment can be a major factor as people with low income might tend to contribute lesser to the sales as they will buy limited and cheaper products. One of the most interesting insights in the dataset would be looking at how markdowns will play a role with the weekly sales.


***Data Understanding:***

The main objective was to forecast weekly sales for each department in 45 Walmart stores located in different regions and also to carry out statistical testing and validation of the models which features DataPreprocessing, Exploratory Data Analysis, modelling on train dataset and validating on test dataset
1.	Features.csv
2.	Stores.csv
3.	Train.csv
4.	Test.csv
Features: Dataset Contains historical data of 45 stores in different regions for period of 4 years. It includes major markdown events that happen throughout the year like Christmas, Labour Day, Thanksgiving, Super bowl. Other features like IS Holiday, Date, Fuel Price can be used in Hypothesis. 
        For Example: effect of sales during holiday seasons on each store on weekly basis
        
Stores: Dataset contains information on 45 stores like Type of store and Size(in sqft) of the store.

Train: Dataset contains historical train data on which the model is trained. Features included are Store number, Department number, Date which is date of the week we are predicting the sales. Weekly_sales for given department in the given store, and IS holiday
 Example Hypothesis: Predicting Department wise sales for each store
Test: It includes same fields as Train.csv excluding weekly sales which is our Target variable.

***Data Preperation/preprocessing:***

1.	importing Features,Stores,Train and Test datasets into jupyter notebook
2.	Understanding information provided in the datasets and looking for types of columns and missing values.
3.	Converting Datatype of Date column to DATETIME from OBJECT
4.	Merging train dataset with store id on stores dataset 
5.	Merging resulting dataset with features on 'Store','Date','IsHoliday'
6.	Now we have a single dataset with all the columns required for exploratory Data Analysis.
7.Checking for Null values and imputing with constants
8.Standardizing the features in the Dataset to balance the variance between the features. If the features are not normalized on to a single scale, the model might be biased towards high variance features. Bias can be mitigaed by tranforming original dataset.


***Modeling:***




***Evaluation:***

***Deployment:***












