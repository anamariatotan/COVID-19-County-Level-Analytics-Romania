# COVID-19 COUNTY LEVEL ANALYTICS IN ROMANIA

An end-to-end Big Data and analytics project designed to clean, process, analyze, visualize, and predict COVID-19 risk levels using county-level data from Romania.

## PROJECT ARCHITECTURE

The project follows a complete data analytics workflow across several stages.

1. Data Acquisition Layer
The project uses a public Kaggle dataset containing COVID-19 data for Romania at country and county level.

2. Preprocessing and Feature Engineering Layer
Python and Pandas are used to clean the raw data, convert date and numeric columns, create time-based features, and define a risk level variable.

3. Exploratory Data Analysis Layer
Matplotlib is used to create charts that analyze confirmed cases by county, time period, month, and risk level.

4. Big Data Processing Layer
PySpark is used to process the cleaned county-level dataset and perform grouped analysis by county, month, and risk level.

5. Machine Learning and Predictive Analytics Layer
A Decision Tree Classifier is trained to predict the COVID-19 risk level based on county-level indicators.

6. Interactive Business Intelligence Layer
Tableau Public is used to create a dashboard that presents the main findings in a visual and interactive format.

## DATASET

The dataset was downloaded from Kaggle:
https://www.kaggle.com/datasets/gpreda/covid19-romania-county-level

The project uses two CSV files:
1. ro_covid_19_country_data_time_series.csv, country-level COVID-19 time series data.
2. ro_covid_19_time_series.csv, county-level COVID-19 time series data.

The main analysis focuses on the county-level dataset.

## DATA SCHEMA AND ENGINEERED METRICS

The cleaned county-level dataset contains the following columns:
County: Romanian county or administrative area.
Confirmed: Number of confirmed COVID-19 cases.
Date: Date of the record.
Year: Year extracted from the date.
Month: Month number extracted from the date.
Month_Name: Month name extracted from the date.
Day: Day extracted from the date.
Risk_Level: Engineered risk category based on confirmed cases.
The risk level was created using the following rules:
Low: fewer than 500 confirmed cases.
Medium: between 500 and 1999 confirmed cases.
High: 2000 or more confirmed cases.

## INSTALLATION AND SETUP
1. Clone the repository:
git clone <your-repository-url>

2. Install the required dependencies:
pip install -r requirements.txt

3. Download the dataset from Kaggle and place the raw CSV files in:
data/raw/

4. Run the notebooks in this order:
notebooks/01_preprocessing.ipynb
notebooks/02_eda.ipynb
notebooks/03_spark_analysis.ipynb
notebooks/04_machine_learning.ipynb

## PROJECT WORKFLOW

1. Data Preprocessing
The preprocessing notebook loads the raw COVID-19 CSV files and prepares them for analysis.

Main steps:
1. Load raw country-level and county-level data.
2. Keep only relevant columns.
3. Convert date columns to datetime format.
4. Convert confirmed cases to numeric format.
5. Remove invalid rows.
6. Create time features such as year, month, month name, and day.
7. Create the Risk_Level variable.
8. Save the cleaned datasets in data/processed/.

The processed files are:
covid_county_clean.csv
covid_country_clean.csv

2. Exploratory Data Analysis

The EDA notebook analyzes the cleaned data using charts.
The main visualizations are:
1. Top 10 counties by confirmed COVID-19 cases.
2. Confirmed COVID-19 cases over time.
3. Total confirmed cases by date.
4. Monthly confirmed COVID-19 cases.
5. Risk level distribution on the latest date.
6. Latest country-level COVID-19 indicators.

This step helps identify the counties with the highest number of cases and the main trends over time.

3. Big Data Processing with PySpark

The PySpark notebook demonstrates Big Data processing on the cleaned county-level dataset.

The Spark analysis includes:
1. Loading the processed dataset with Spark.
2. Checking the dataset schema.
3. Calculating top counties by total confirmed cases.
4. Calculating average confirmed cases by county.
5. Grouping confirmed cases by year and month.
6. Calculating risk level distribution on the latest date.
7. Displaying the records with the highest confirmed values.

This step satisfies the Big Data Processing requirement of the project.

4. Machine Learning and Predictive Analytics

The Machine Learning notebook trains a classification model to predict COVID-19 risk level.

The target variable is:
Risk_Level
The model predicts one of three categories:
1. Low
2. Medium
3. High

The input features are:
1. County
2. Confirmed
3. Year
4. Month

The model used is:
DecisionTreeClassifier

The model is evaluated using:
1. Accuracy score.
2. Classification report.
3. Confusion matrix.

The project also includes a chart showing the average number of confirmed cases for each risk level.

## TABLEAU DASHBOARD

The final dashboard was created in Tableau Public.

Dashboard link:
https://public.tableau.com/app/profile/anamaria.totan/viz/COVID-19CountyLevelAnalyticsinRomania/COVID-19CountyLevelAnalyticsinRomania?publish=yes

The dashboard includes four main visualizations:
1. Top 10 counties by confirmed COVID-19 cases.
2. Confirmed COVID-19 cases over time.
3. Monthly confirmed COVID-19 cases.
4. Risk level distribution on the latest date.

The dashboard presents the main findings in a clear visual format.

## KEY FINDINGS AND INSIGHTS

1. Counties with the Highest Confirmed Cases

The analysis shows that Mun. Bucuresti and Suceava recorded the highest confirmed case values in the dataset.

This indicates that COVID-19 impact was not evenly distributed across counties.

2. Growth of Confirmed Cases Over Time

The time-based charts show an increase in confirmed cases across the analyzed period.

The monthly analysis shows visible growth from April to July 2020.

3. Risk Level Distribution

The risk level analysis groups counties into Low, Medium, and High categories based on confirmed cases.

On the latest available date, most counties fall into Low or Medium risk categories, while a smaller number of counties are classified as High risk.

4. Machine Learning Results

The Decision Tree model predicts the risk level using county-level COVID-19 indicators.

The model mainly learns the risk categories from the number of confirmed cases, because the risk levels were created using confirmed case thresholds.

This confirms that confirmed cases are the main factor behind the risk classification.

## REPOSITORY STRUCTURE

data/
  processed/
    covid_country_clean.csv
    covid_county_clean.csv

  raw/
    ro_covid_19_country_data_time_series.csv
    ro_covid_19_time_series.csv

notebooks/
  01_preprocessing.ipynb
  02_eda.ipynb
  03_spark_analysis.ipynb
  04_machine_learning.ipynb

screenshots/
  01_top_counties_confirmed.png
  02_confirmed_cases_over_time.png
  03_confirmed_cases_by_date.png
  04_monthly_confirmed_cases.png
  05_risk_level_distribution.png
  06_country_indicators.png
  07_ml_risk_distribution.png
  08_confusion_matrix.png
  09_avg_confirmed_by_risk.png

.gitignore

requirements.txt

README.md

## PROJECT DELIVERABLES

The project includes:

1. Cleaned Python notebooks.
2. Preprocessing workflow.
3. Exploratory data analysis.
4. PySpark Big Data processing.
5. Machine Learning model.
6. Tableau Public dashboard.
7. GitHub repository documentation.

## CONCLUSION

This project presents a complete Big Data workflow for COVID-19 county-level data in Romania.

The workflow starts with raw data, continues with data cleaning and exploratory analysis, applies PySpark processing, builds a Machine Learning model, and presents the final results through a Tableau Public dashboard.