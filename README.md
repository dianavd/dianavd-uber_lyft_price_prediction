

#Uber vs. Lyft Price Prediction Model

This repository explains the R Project's data analysis and modeling process "Uber VS Lyft Price Prediction in R." 

##Introduction
Taxi prices are not steady like public transportation. Taxi prices change all the time and are indeed affected by many factors, for example, the demand and supply of rides at a given time, weather, etc. So, what defines the cab price? 
I analyzed Uber, and Lyft rides in Boston, MA, of a data set of 693,071 rideshares with 57 defining features from late November through mid-December in 2018. In my analysis, I predicted and compared the price of Uber and Lyft rideshares based on various predictors such as distance, an hour of the day, day of the month, day of the week, surge multiplier (demand-based pricing), weather features, etc.

##Project description
This project aims to analyze and predict the price of Uber and Lyft.
Source of the data: https://www.kaggle.com/datasets/brllrb/uber-and-lyft-dataset-boston-ma
With no public data of rides/prices shared by any entity, this dataset contains real-time data using Uber&Lyft API queries at a few hot locations in Boston and corresponding weather conditions. The queries were done on the apps every 5 minutes for 22 days from late November through mid-December in 2018. 
I was inspired to work on this project because of its relevance to almost everyone, especially in big cities. People often use taxi services, primarily Uber and Lyft rideshares, to get around the vast cities. So, exploring how these taxi pricing models work and vary by circumstance is practical and exciting, which gives us a better feel of what taxi service to use. Furthermore, this real-world problem project greatly applies data science and machine learning techniques.

##Target audience
The target audience is everyone because almost all people are taxi customers in many different situations.

##Dataset
We are using the Kaggle dataset rideshare_kaggle.csv with 693071 records with 57 attributes. You can download this dataset from Kaggle. 
Link for the dataset: https://www.kaggle.com/datasets/brllrb/uber-and-lyft-dataset-boston-ma
This dataset is a sample dataset for Uber & Lyft rides in Boston, MA. The rideshare data covers various types of cab rides for Uber & Lyft and their price for the given location. We can find if there was any surge in the price during that time. The dataset contains the corresponding weather data features for that Hour,  like temperature, rain, cloud, wind, sunset, a short summary, and a long summary of the weather, etc., for all the locations considered.

##Data difficulties
The dataset's quality is questionable, which can impact my analysis's results. 
It seems we have many gaps in our 'day' data. We only have 17 days of November and December in our monthly data. It means the data is only recorded during 17 days in November and December, with December data dominating. 
It seemed like observations spread almost equally in variables like "Product ID," "Source," and "Destination."
It seems that the quantity of Sources is almost equal. There are about 53 thousand of observations in each Source feature (Back Bay, Beacon Hill, Boston University, etc.)
Like with the Source feature, there are about 53 thousand of rows in each destination feature (Back Bay, Beacon Hill, Boston University, etc.)
We have 55095 missing values of a variable Price for cab_type Taxi.
All Uber rides have the surge_multipier variable equal to 1. Lyft surge_multipier ranges from 1 to 3. It's hard to believe that Uber has no rides during busy hours. The surge_multipier variable removed as a variable with almost zero-variance.
All of that I mentioned creates doubt about data completeness. 

##Research question
• What defines the cab price of Uber vs. Lyft? 

##Steps completed
•	Preprocess/ Clean/ Create new variables
•	EDA of the Kaggle rideshare data set, using R
•	Visualization of data analysis using tidyverse, ggplot2, dplyr, car, readr, mlbench, etc.

##Exploratory data analysis 
No prices were associated with rows with the variable "cab_type" Taxi. After removing missing values, there are 637976 rides. The analyzed period of the cab rides is 17 days between November and December of 2018. The average price for the ride is 16.55. The average distance is 2.189. The average temperature is 39.58 F.
In this dataset, Uber has more rides than Lyft. 51.82 percent of rides were for Uber. 48.18% was for Lyft. The difference is not too big; each cab type has about 300 thousand of data.
The date columns contain some composite information such as day, day of the week, month, and time. Extracting them gives us more granular information to explore. 
It seems we have almost 24 hours of recorded data. So, in every Day and every Hour recorded, Uber seems to dominate booking orders in our data.
Changed product names by Uber and Lyft, making them user-friendly.
The number of rides is slightly different between sources and destinations. All cab pickup points had above 8 percent of the total rides.
After removing unusable or irrelevant variables (DateTime, product_id, etc.) of my interests and creating a few new variables (Hour, Day of the week), the dataset contains 16 variables with 637,976 observations.

##Conclusions
My goal was to fit a model to predict the ride price of Uber vs. Lyft. I randomly sample 2000 observations of the dataset because of memory limits and optimization of the processing time in R. I tryied to fit a few models, including LM, GLM, GLMNET, CART, SVM, KNN, CUBIST and GBM. 
Cubist is the best ML model for Uber and Lyft price prediction. 
UBER:
•	RMSE (train 2.153322, test 1.879026) 
•	R-squared (train 0.9385098, test 0.9519049) 
LYFT:
•	RMSE (train 2.952509 , test  3.135741) 
•	R-squared (train 0.912892, test 0.909245 ) 
Cubist for the sample of Uber dataset performed better than for Lyft.
The cubist model identified some important price features such as Distance, Product, Hour, Day, Source, Destination, and Cloudy Weather.

##Next steps 
Develop a Shiny app for the EDA part of the project to hold a user-friendly speed. 
Perform the model's refinement to improve accuracy. For example, consider the interactions between the variables and work on model stacking.
Incorporate additional features, for example, traffic conditions.

##Suggested actions
When considering purchasing Uber service from Uber or Lyft, consider the most important drivers of cab price:
Taxi customers pay more for a taxi with higher quality products. Distance is the primary driver of the taxi price. 
Source and Destination matter too. The cloudy weather seems an important driver for the taxi price too.
Day and Hour matter too. Demand for a taxi during Holidays and Mondays is higher.  The peak Hours are between 6 p.m. and 8 p.m. for the post-work crowd. 
Based on a given dataset, Uber prices are slightly lower than Lyft for Lux products. But Shared and SUV Products from Lyft are cheaper than similar products from Uber. 

##Resources:
The dataset in Kaggle: https://www.kaggle.com/datasets/ravi72munde/uber-lyft-cab-prices
https://nycdatascience.com/blog/
https://towardsdatascience.com/
"Practical Statistics for Data Scientists 50 Essential Concepts", by Peter Bruce & Andrew Bruce, 2017, O'REILLY
"Machine Learning Mastery with R", by Jason Brownlee, 2016
