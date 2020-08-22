# Readme file for the "Write a Data Science Blog Post" Project
#### Part of the Data Scientist Nano degree program at Udacity
##### By: James L. Sturges

## Project libaries and functions
* For this project I used the following libraries and Functions

### From sk-learn
* sklearn.linear_model import LinearRegression - to perform linear regression 
* sklearn.model_selection import train_test_split- to split training and test data
* sklearn.metrics import r2_score, mean_squared_error- to perform scoring on the resultant regression model

### From Lesson one of the Udacity lessons to following functions
* create_dummy_df -  to create dummy categorical variables
* find_optimal_lm_mod - to provide a automated way to apply cutoffs to determine which feature should be dropped due to missing data
* coef_weights - to display sorted list of weighted coefficients

##### From the Seaborn library 
* coefficient heatmap

##### From the glob library
* ability to read select file names within a directory into a list for Pandas loop (for possible concatination into a single dataframe)

##### From the datetime library
* ability to convert date to datetime, if required

### CRISP-DM
#### Develop a Business Understanding - Project Motivation

To Analyze this data I am going to use the **Cross Industry Standard Process for Data Mining (CRISP-DM)**


The AirBnB data for Seattle was of interest to me as it is the area I grew up in and I as interested to see how the feature within the data releated to price. The industry that has grown up around AirBnB is still fairly new and investigating this data set provides some in site both from the rentor and rentee perspectives.

* From a Crisp-DM perspective: The Problem
+ As a possible rentee in Seattle: How to determine if the AirBnB price is reasonable
+ As a possble rentor in Seattle: determining the features that would drive the pricing in my unit.
    
##### Three Questions
To delve deeper into this subject I have identified three question to be answered

+ Where are AirBnB properties distributed across Seattle and does the appear to affect price?
+ What features appear to impact the price the most?
+ Does the cancellation policy have a significant impact on price?


For my evaluation I limited my review to Entire Homes or Apartments.


### Data Files

* From a Crisp-DM perspective we review the data for better Data understanding.
+ At a minimum we need data pertaining to location, size, and price in addition to all other feature that might be relevant. The Data provide meets all these creteria.



The main data file used in this analysis was listing file ('sea_d_201901_listings.csv.gz') from January 2019 for the Seattle Area publicly available from http://insideairbnb.com/get-the-data.html. 
If time allows a number of these files will be read with different dates to view the change in prices over time.
Each file has 86 columns including data on:
* the host
* accomomdation type
* size, rooms, beds
* rental policies (cancelation, miminum, maximum stay)
* location (zip, neighborhood)
* price 

##### Results:
* Not too surprising location, bedrooms and bathrooms were strong determinents on price.
* Not so expected, for me, was that strict cancellation policy was the most highly weighted coefficient

#### Crisp DM Data Preparation
Examination of the data inicated that there were many feature which were missing data. 

To mitigate this issue I used two strategies used in the instruction for the class. For missing numeric data rather the eliminating the rows which would remove two much of the available data, I choose to fill the NA with the mean.

Then to eliminate the other features that did not have enough data to reliably use in the model, I used the cutoff method (also provided in the instruction) to use different cutoff values (for the number of missing values) and run that against the linear regression model.  Using rsquared as the measure, the routine reduce the number of feature until the optimum cutoff level was found.  For this model it was 100 features.

In addition, I generated a heatmap using seaborn to determine highly correlated features and manaully eliminated them.  Running the model provided feedback that the elimination successfull impoved the Rsquared score.


#### Crisp DM - Analysis and Modeling
For this project and to answer the questions above I utilized both Python and assorted libaries (mentioned above) and the Tableau program which excels at visualization.

The first question which had two part regarding location and price, I used Tableau to show a map and relative concentation of properties within in zip code area.  This are noted on my Medium Blog:
* (https://medium.com/@jim0sturges/airbnb-in-the-emerald-city-2154123fef5f?sk=978b92e54f7eeb51eecdbb439db09e1d

As a second visual I provided a boxplox of median AirBnB property prices sorted in decending order. The reader who so desired can use these two tools together.

For the second and third questions I ran a linear regression using the cleaned data to determine which factor most effect price. For that were able to answer both the second and third questions for the resulting sorted weighted features.

#### Crisp DM - Validation

Since data validation by an outside entity was not convient for this student project wa able to somewhat validate the data as I reduced features and observed the results on my Rsquared values.  In a professional setting I would compare the Seattle results against other areas and snap shots on different time perios to determine demonstrate consistency.

#### Crisp DM - Presentation/Visualization

Please see medium Blog
* (https://medium.com/@jim0sturges/airbnb-in-the-emerald-city-2154123fef5f?sk=978b92e54f7eeb51eecdbb439db09e1d
