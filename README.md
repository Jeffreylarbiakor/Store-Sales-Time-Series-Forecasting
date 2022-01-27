# Store-Sales-Time-Series-Forecasting

## Introduction
Time Series is a type of data that measures how things change over time. In a time series dataset, the time column does
not represent the variable per se, instead, it's more useful to think of it as a primary structure for ordering the dataset.

Building Machine Learning (ML) Models with time series data is often time consuming and complex, with many factors to 
consider, such as iterating through algorithms, turning ML hyperparameters, and applying feature engineering techniques.

In this project, I will be using time-series forecasting to forecast store sales on data from a large grocery retailer. 
Specifically, I will build a model that more accurately predicts the unit sales for thousands of items sold at different 
stores in the chain.


## Exploratory Data Analysis (EDA)
Before building any model, the data will be explored to understand the dataset being used.
Seven(7) files have been provided. A description for each file has been given below:

1. Train Data (csv):
The training data, comprising time series of features store_nbr, family, and onpromotion as well as the target sales.
store_nbr identifies the store at which the products are sold.
family identifies the category of product sold.
sales give the total sales for a product family at a particular store at a given date. Fractional values are 
possible since products can be sold in fractional units (1.5 kg of cheese, for instance, as opposed to 1 bag of chips).
onpromotion gives the total number of items in a product family that were being promoted at a store on a given date.

2. Test Data (csv):
The test data has the same features as the training data. Target sales will be predicted for the dates in this file.
The dates in the test data are for the 15 days after the last date in the training data.

3. Sample Submission Data (csv):
The sample submission data is a file which contains examples of how the submission file should be presented after a 
model has been built.

4. Stores Data (csv):
The stores metadata contains the city, state, type and cluster grouping of similar stores

5. Transactions Data (csv):
The transactions data contains date, store_nbr and the number of transactions made on each date. 
The relationship between the transactions data and sales column of the train data would be investigated to identify any 
correlations

6. Holidays and Events Data (csv):
This data includes Holidays and Events with metadata. Special attention would be paid to the transferred column. 
A holiday that is transferred officially falls on that calendar day but was moved to another date by the government. 
A transferred day is more like a normal day than a holiday. To find the day that it was actually celebrated, look for 
the corresponding row where the type is Transfer. For example, the holiday Independencia de Guayaquil was transferred 
from 2012-10-09 to 2012-10-12, which means it was celebrated on 2012-10-12. Days that are type Bridge are extra days 
that are added to a holiday (e.g., to extend the break across a long weekend). These are frequently made up by the type 
Work Day which is a day not normally scheduled for work (e.g., Saturday) that is meant to pay back the Bridge. 
Adittional holidays are days added to a regular calendar holiday, for example, as typically happens around Christmas 
(making Christmas Eve a holiday).

7. Oil Data (csv):
This data contains the daily oil price including values during both train and test data timeframes. 
Ecuador is an oil-dependent country and its economic health is highly vulnerable to shocks in oil prices.


## Data Cleaning
Oils Data had 43 null values. This was filled by linear intrapolation
All other data points had no null values


## Feature Engineering
* A high correlation between transactions and sales data makes the transactions data an important feature in building 
forecasting model
* A negative correlation between the sales data and daily oil prices makes the oil data necessary for improving the 
accuracy of the model
* As this is a time-series forecasting problem, the time-related 'wageday' column is an important feature in building 
an accurate model


## Algorithm Selection
Models were build in the Azure Machine Learning Studio
Models Compared:
* Linear Regression
* Boosted Decision Tree Regression
* Neural Network Regression


Model Selected and Deployed:
Boosted Decision Tree Regression


## Evaluation Metrics
* Linear Regression
Coefficient_of_Determination: 0.625
Mean_Absolute_Error: 0.0002
Relative_Absolute_Error: 0.444
Relative_Squared_Error: 0.375
Root_Mean_Squared_Error: 0.005

* Boosted Decision Tree Regression
Coefficient_of_Determination: 0.895
Mean_Absolute_Error: 8.6559e-4
Relative_Absolute_Error: 0.212
Relative_Squared_Error: 0.105
Root_Mean_Squared_Error: 0.003

* Neural Network Regression
Coefficient_of_Determination: 0.678
Mean_Absolute_Error: 0.0003
Relative_Absolute_Error: 0.615
Relative_Squared_Error: 0.322
Root_Mean_Squared_Error: 0.005




## Published Model Pipeline Details:
Status
Active

REST endpoint
https://eastus2.api.azureml.ms/pipelines/v1.0/subscriptions/63dac7f9-dae6-4cf2-8be6-cc2d527d0cd3/resourceGroups/ML-Modeling/providers/Microsoft.MachineLearningServices/workspaces/My_Workspace/PipelineRuns/PipelineEndpointSubmit/Id/a275bc5d-c04f-442d-9906-ac64497ec17d

REST endpoint documentation
https://eastus2.api.azureml.ms/pipelines/swagger/pipelineendpointsubmit/swagger.json


Date published
Nov 18, 2021 11:47 AM

PipelineEndpoint ID
a275bc5d-c04f-442d-9906-ac64497ec17d

