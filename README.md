# Project-2

This is an ETL project where a dataset is sourced, transformed (cleaned) and loaded onto either relational (PostgreSQL) or non-relational database (MongoDB) depending on the use case and the relationship of the data one is working on. 

After loading, the stored database can then be accessed/queried to analyse, derive insights in order to solve the initial business use case successfully. 

### ETL
The ETL process of Extraction, Transformation and Loading hence forms an integral part of the entire data pipeline.

![ETL](https://webassets.mongodb.com/_com_assets/cms/ETL_Visual-sa656kl6df.png)

(The current ETL image was sourced from MongoDB.com)

# Objective of the project - 
### To determine the factors influening the UK Road Traffic Collision and Accident. 
Owing to the advancement of infrastructure within the transport industry with regards to the technologies within the cars and the road conditions, casualties resulting from the road traffic collision has consistently seen a downward trend (since the 1960s). 
However, still a substantial number of road traffic collision and accident do occur and they result in serious/fatal consequences. 

#### Data Extraction
In order to determine what factors influenceing the road traffic collision and accident, two CSV datafiles consisting of accident and vehicle details were sourced from (https://www.kaggle.com/datasets/salmankhaliq22/road-traffic-collision-dataset). These cleaned datasets were initally obtained from the Department of Transport (UK) for the period 2005-2017  The accident dataset contains extensive information detailing the collision and accident alongside the weather and road condition. The vehicle dataset gives details of the vehicle involved in the collision along with driver information and vehicle manoevore that resulted in the collision.

The datasets used in this project exceeded the size limit of GitHub, hence couldnt upload the files to this repository. Instead the link to the datasets are provided if you need to access them.

#### Data transformation
After gathering initial requiremments of the data analysis team who will determining the relationship of the accident in relation to the 'speed limit', 'weather conditions', 'day of the week', 'road condition', 'vehicle_age', 'driver_age', 'driver_sex' and 'vehicle manoeuvre' etc, the data cleaning process was commenced.
   
   (a) Unneccessary colums that were not part of the data analysis requirement were taken out 
   
   (b) The column names of the two data files were simplified and renamed 
   
   (c) Rows with missing data were taken out.
   
   (d) Unique value counts of columns were determined and 'Not known' & 'Data missing or out of range' were taken from the data file.
   
   (e) Accident file had (1048575 rows × 34 columns) values and after the cleaning process we had (1026974 rows × 6 columns) value counts.
       The column names included in the cleaned accident file - id, accident_severity, day_of_week, Speed_Limit, Road_Conditions, and weather_Conditions
   
   (f) Vehicle file had (2177205 rows × 24 columns) values and after the cleaning process we had (1517856 rows × 6 columns) value counts.
       The column names included in the cleaned accident file - id, driver_Age, vehicleAge, make, model, driver_sex and Vehicle_Manoeuvre
       
   (g) The clean pandas dataframes were uploaded to postgresql (use case 1) and MongoDB (use case 2).
   

# Use case 1 - 

### Entity Relationship Diagram (ERD)
The CSV files were inspected and ERD diagram of the two datasets were sketched out employing a free online tool (http://www.quickdatabasediagrams.com). 

![alt text](https://github.com/fbrowther/Project-2/blob/main/ERD%20diagram.png)

### Data Engineering 
Database 'Accident_db' was created on Postgresql followed by creating two tables namely - Accident and Vehicle with required column names. 

Using the provided information, we created table schema for each of the cleaned CSV files followed by specifing their data types, primary keys, foreign keys, and other constraints. The .sql schema file has been attached for your reference. 

ID (accident_index) was chosen as the primary key for the 'accident_data' table. 
ID (accident_index) of the multiple vehicle involved in collision was the foreign_key for the 'vehicle_data' table.


# Loading of the data onto Postgresql - 
The cleaned dataframe were loaded onto the respective empty tables in Postgresql after establishing connection by creating an engine. The details are included in the Analysisfinal.ipynb file  

The successful uploading was confirmed by the (SELECT * FROM accident/vehicle) query and the following secreenshots display the same as follows -

![alt text](https://github.com/hibaaaldubai/Group-1-Project-2/blob/main/Postgresql%20/Accident.png)

![alt text](https://github.com/hibaaaldubai/Group-1-Project-2/blob/main/Postgresql%20/Vehicle.png)

# Use case 2 - 



# Data Engineering -
Accident_db was created on Postgresql followed by creating two tables namely - Accident and Vehicle. 

Using the provided information, we created table schema for each of the CSV files followed by specifing their data types, primary keys, foreign keys, and other constraints. The .sql schema file has been attached for your reference. 

# Loading of the data onto Postgresql - 
We successfully loaded the cleaned dataframe onto the respective empty tables in Postgresql after establishing connection by creating an engine. The details are included in the Analysisfinal.ipynb file (https://github.com/hibaaaldubai/Group-1-Project-2/blob/main/AnalysisFinal.ipynb). 

The successful uploading was confirmed by the (SELECT * FROM accident/vehicle) query and the following secreenshots display the same as follows -

![alt text](https://github.com/hibaaaldubai/Group-1-Project-2/blob/main/Postgresql%20/Accident.png)

![alt text](https://github.com/hibaaaldubai/Group-1-Project-2/blob/main/Postgresql%20/Vehicle.png)


# Conclusions -
  As a part of this project, we were able to successfully extract, transform and load the data onto the relational database, Postgresql for further analysis by the Data Analytics team. 

# Future work suggestions -
  The database tables 'accident' and 'vehicle' could be joined (FULL JOIN) at the primary key id (accident index) and the following queries could be performed -
    
    (a) Is there any correlation between 'driver_age' and 'accident severity'
    
    (b) Is there any correlation between 'vehicle_age' and 'accident severity'
    
    (c) Is there any correlation between 'driver_sex' and 'accident severity'
    
    (d) Is there any correlation between 'model' and 'make'(indicating the vehicle size and type indirectly) and 'accident severity'
    
    (e) Is there any correlation between 'weather conditions' and 'accident severity'
    
    (f) Is there any correlation between 'day of the week' and 'accident severity'





