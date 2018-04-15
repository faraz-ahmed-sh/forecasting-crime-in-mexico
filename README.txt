## Analyzing the Crime Rate of Mexico

### In this project (as part of a course called Computer Science with Applications II offered at UChicago), we created a website that visualizes the rate of crime in different states in Mexico. We also used machine learning technique (LASSO) to predict the crime rate in those states.

#### The following sections describe what each of the file in this repository does. If you want to run the program, please go to /frontend/Instructions_frontend.txt. You'll be asked to deploy the project on Flask, a web framework that creates web applications in Python.

----------------------------------------------------------

This is a README of the files attached with this project:

SUMMARY

The project has the following components:

Project proposal and presentation
Data 
Backend
Frontend

CONTENT

PROJECT PROPOSAL AND PRESENTATION 
- CS122-Project_Super Forecasters.docx:
Project Proposal
-Final-Presentation_2.pptx
Final presentation of the project in the winter quarter 2017
-Super-Forecasters-Pitch2.pptx
First presentation of the project in the winter quarter 2017

DATA:
MINI_DB:
Database composed of 7 tables 
- raw_csv:
Where the csv of the Mexican Ministry of Statistics are located
- process_csv: 
Where the csv after been modified by crime_process.py and csv_process.py. Also contain csv created by dataframe_lasso.py
- Querys
Contains queries to query mini_db
- create_db.sql
Schema to create and upload a sql database with the csv of process_csv (just the csv common with raw_csv).
- db_layout.txt
File with the name of the tables and columns. Each column has the spanish name, english name and name used in the database.
- mini_db
Sql database (.db) created by create_db.sql
-frontend_aux
Auxiliary csv, database and schema for visualization purposes (customized for the frontend API)

BACKEND:
- crime_process.py
Inputs mini_db/raw_csv/crime.csv and reshape it. Create mini_db/process_csv/crime.cvs. This is the file that process the predicted columns (crimes).
- csv_process.py
Inputs mini_db/raw_csv/n.csv and reshape them. Where n are the different tables of the predictors (justice_system, education, health, etc.). Create mini_db/process_csv/n.cvs. This is the file that process the predictors (covariates) columns.
- dataframe_lasso.py
Inputs mini_db.db creates a connection between sqlite and python3 and makes a pandas dataframe. Constructs changes and lags of the predicted columns and predictors. Drop NaN and entites where there is not complete information. Restricts the dataframe for the years 2008-2011 (where there is complete information). Outputs df_limited.csv and lists: list_dep (dependent) and list_lag (covariates).
-lasso_model.py
Inputs the outputs of dataframe_lasso. 
Contruct function frontend that inputs name of the variable to predict (string) and year. Outputs: actual observations, predicted observations, coefficients of the predictiors, mean square error (mse), corr(pred,actual) and r-square of the prediction.
Contruct a class where the estimations of the predictive model (lasso) are done.

FRONT END
Templates folder: a folder for all the Jinja/html templates for Flask
Static: a javascript file for charts
Flask_frontend_crime.py: A python file with the code to run the website
