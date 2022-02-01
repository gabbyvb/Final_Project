# Home Price Predictor

## Background
### Project Description
**Topic:** Home Price Predictor

**Reason:** Real estate is a hot market right now and all group members were interested in seeing how various factors affect the value of a home in our area.

**Questions We Hope to Answer**
1. Does the rating of schools affect the home value? If so, how?
2. How does Prime Rate affect home value?
3. Are homes in the area being under- or over-valued?

### Data Sources
- Kaggle: [Preparing the D.C. Real Property Dataset](https://www.kaggle.com/christophercorrea/preparing-the-d-c-real-property-dataset/data)
- Open Data DC: [School Attendance Zones (Senior High)](https://opendata.dc.gov/datasets/DCGIS::school-attendance-zones-senior-high/explore?location=38.891085,-77.020974,12.00&showTable=true)
- DC Public Schools : [School List](https://profiles.dcps.dc.gov/)
- FRED Economic Data: [Bank Prime Loan Rate Changes: Historical Dates of Changes and Rates (PRIME)](https://fred.stlouisfed.org/series/PRIME)

### Software
 *(add versions)*
- Jupyter Notebook
	- Python
- pgAdmin 4
	- PostgreSQL
- [Quick Database Diagrams](https://app.quickdatabasediagrams.com/#/d/qAGqUr)
- Tableau

### Group Presentation Can Be Found [Here](https://docs.google.com/presentation/d/1iFYkaugBKUH1rIhKyagy_23oyhhAb3F-Tw-sqRhbQg0/edit?usp=sharing)

## Data Exploration
Description of Data Exploration Phase
Graphing, looking for outliers,

Description of Analysis Phase
TBD

## Database

[Data Dictionary](https://docs.google.com/spreadsheets/d/1PIofEBS1nXVsO876CufvHLC2uMqvywRX_FMtP_agspc/edit?usp=sharing)

<img width="736" alt="ERD" src="https://user-images.githubusercontent.com/89493488/150467257-ad2a729d-a177-4db0-ab2e-2defd93d64b9.png">

## Machine Learning

Provisional ML Model 
Uses Provisional DB
Labels for INPUTs

Description of Data Preproscessing

Used pandas to clean data as well as remove large amounts of rows from the ML dataset due to memory errors. Also used OneHotEncoder to convert categorical data into numerical.

Description of Feature Engineering - Feature Select - Why and How Selected?

Since I was able to complete the model using the limited data, I used 'feature importances' to find the most impactful features and will look to drop the unimpactful features to use more. With the more limited data I should be able to include previously dropped rows. 

Model Limitations and Benefits

A limitation, at least until we figure it out, is the amount of data that needs to be processed for the RandomForestClassifier which currently has 100 forests. Also, the accuracy is abysmal for both models. I think I can make the accuracy better if the price is binned by $25,000 increments and indexed so the model would need to predict the index rather than the precise price. 

## Dashboard

- Tableau is the Data Visualization Tool currently being used for this Project and will depict the following:
	- Average Price by Location
	- Home Sales By Year
	- Map Depicting the Location of Schools in each Ward of DC
	- Average Price by Number of Bedrooms
	- Average Price vs. School Ranking
	- Interest Rate by Year of Home Purchase

Link to Tableau: https://public.tableau.com/app/profile/dolores3708/viz/Final_Project_Draft/Story1?publish=yes	
 
- Google Slides will be used to create a Storyboard for our Final Presentation

> Written with [StackEdit](https://stackedit.io/).
