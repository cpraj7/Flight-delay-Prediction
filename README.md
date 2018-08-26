Problem Description

Air travel is becoming increasingly complex with multiple variables impacting the same. The flight delay is one of such variables that impacts carrier, Airport and
passenger and may result in significant commercial loss or reputation loss to all the stakeholders and thus huge cost on the economy. Thus, prediction of
delay is crucial not only from view point of customer from time management perspective and carrier for retention of customer faith but also from Airport
point of view for managing the traffic more efficiently to optimise the number of arriving flights by appropriate adjustment of schedules. The contribution of
weather conditions has been identified to be the very important contributor of these delays.

Data Understanding

-	Given flight and weather details for 2004 & 2005. 
-	Also, Given Weather data is for every hour. 
-	Target variable has to be derived from given Scheduled arrival, Actual arrival time by using if flight is delay only if delay time is more than 15 Mins.
-	There are few airports which doesn't are connected to any weather stations.

Data Preprocessing

Note: We have used spark SQL for data preprocessing.
-	From given weather data, we have extracted only used Origin & Destination details from train data
-	total unique WeatherStationID & AirportID are 243.
-	first 3 digits of SkyConditions has been considered.
-	if Visibility is null then default value considered as SM.
-	Time format used is HHMM. 
-	There are around 16 records which has duplicate values. 
-	Maximum values are used for duplicate values.
-	Final Train and Test data is prepared By combining Train & Test data with preprocessed weather data.
-	Final shape of Train and Test data. 
        Shape of Train data is: (7861, 45)
        Shape of Test data is: (6566, 45)
-	Imputed null values using mean for that date in final Train & Test data.
-	Imputed remaining null values with overall mean in final Train & Test data.
-	Binned Origin, Destination, Travel time , Dept and Arrival hour in final Train & Test data.
-	Used label encoder for converting categorical variable in final Train & Test data.

Model training
-   Train data set is split into 75 and 25.
-   Below Models built using pre-processed train data.
        Gaussian Naive Bayes
        Logistic regression
        Decision trees
        Random forest
        LDA
        ADA boost
        Gradient boost with Naive Bayes
        Gradient boost with decision tree
        KNN 

Feature Engineering
-	Removed unused columns
-	Pre-processed weather data using unique Origin and Destination from given train and test data.
-	Used max value condition for taking hourly data to remove duplicate data.
-	Only first 3 digits of weather condition which describes the data.
-	Used left padding to convert time to 4 digits.

