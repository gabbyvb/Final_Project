# Home Price Predictor

## Background
### Project Description
**Topic:** Home Price Predictor

**Reason:** Real estate is a hot market right now and all group members were interested in seeing how various factors affect the value of a home in our area. The model and visualizations could be used to help a home buyer determine if the property they're interested in is accurately valued.

**Questions We Hope to Answer**
1. Does the rating of schools affect the home value? If so, how?
2. How does Prime Rate affect home value?
3. Are homes in the area being under- or over-valued?

### Data Sources
- Kaggle: [Preparing the D.C. Real Property Dataset](https://www.kaggle.com/christophercorrea/preparing-the-d-c-real-property-dataset/data)
- SchoolDigger.com: [District of Columbia High School Rankings](https://www.schooldigger.com/go/DC/schoolrank.aspx?level=3)
- DC Public Schools : [School List](https://profiles.dcps.dc.gov/)
- FRED Economic Data: [Bank Prime Loan Rate Changes: Historical Dates of Changes and Rates (PRIME)](https://fred.stlouisfed.org/series/PRIME)

### Software
- Jupyter Notebook
	- Python
- pgAdmin 4
	- PostgreSQL
- [Quick Database Diagrams](https://app.quickdatabasediagrams.com/#/d/qAGqUr)
- Tableau

### Group Presentation Can Be Found [Here](https://docs.google.com/presentation/d/1iFYkaugBKUH1rIhKyagy_23oyhhAb3F-Tw-sqRhbQg0/edit?usp=sharing)

## Data Exploration
We explored out data using Python & Jupyter Notebook. We utilized the Pandas, Matplotlib, Seaborn and Numpy libraries. The process we utilized to explore the data is outlined below.

<img width="795" alt="Data_Exploration_Process" src="https://user-images.githubusercontent.com/89493488/153049290-43d12230-6cfe-4dd4-b768-1f50b6d8e095.png">

**Main Takeaways from Data Exploration**
- Many outliers in the data set
	- Led us to suspect that there were additional real estate types in the home data set
- Had to transform many columns to the correct data type
- Found many columns that did not add value to preducting home price

## Database

Our database was constructed using PostgreSQL in pgAdmin 4. Our tables and relationships are shown in the ERD below. For a more detailed description of the data, please use the data dictionary below.

[Data Dictionary](https://docs.google.com/spreadsheets/d/1PIofEBS1nXVsO876CufvHLC2uMqvywRX_FMtP_agspc/edit?usp=sharing)

![Final_ERD](https://user-images.githubusercontent.com/89493488/152899084-dde9ca10-f2db-4280-9150-e436aaee0bfb.png)


## Machine Learning

Provisional ML Model 
Uses Provisional DB
Labels for INPUTs

### Data Preprocessing

Used pandas to clean data as well as remove large amounts of rows from the ML dataset due to memory errors. Also used OneHotEncoder to convert categorical data into numerical. Seaborn was used for visuals to help locate outliers which were eventually removed.

### Feature Engineering - Feature Select - Why and How Selected?

We chose the features from the original dataset that made the most sense when homebuyers are looking to buy a house. 

The features include:
 	
* HF_BATHRM - Number of half bathrooms in the house		
* SALEDATE - Year of sale 	
* PRIME - Prime rate for the year of the saledate
* ROOMS - Number of rooms in the house	
* KITCHENS -  Number of kitchens in the house		
* WARD - Ward of Washington DC where the house is located
* BEDRM  -  Number of bedrooms in the house		
* FIREPLACES - Number of fireplaces in the house		
* LANDAREA - Square footage of land the house is placed on 
* ZIPCODE - Zipcode of the house
* AC - If the house has AC or not 	 	 	 	 	 	
* QUADRANT - Quandrant of Washington DC where the house is located
* BATHRM - Number of bathrooms in the house

### Model Limitations and Benefits

A limitation, at least until we figure it out, is the amount of data that needs to be processed for the RandomForestClassifier which currently has 100 forests. Also, the accuracy is abysmal for both models. I think I can make the accuracy better if the price is binned by $25,000 increments and indexed so the model would need to predict the index rather than the precise price. 

### Update 1

I was able to figure out how to process the dataset without getting a memory error by changing RandomForrestClassifier to BalancedRandomForrestClassifier. I was still unable to achieve the desired accuracy. I unknowingly had many outliers within my feature data which after dropping didn't alter the accuracy but still should be done. I think a potential reason why my model isn't accurate is due to the large difference between the minimum price which is around $25,000 and a maximum of $1,500,000. The next step could be to shorten the difference between the min and max and then to increase the increments of the bins to $50,000.

The current accuracy score for both models is ~8.0%

### Update 2

Unfortunately, after trying to alter my models I wasn't able to achieve an accuracy >50%. I reduced the difference between the minimum and maximum house prices and I reduced the number of bins from 60 to 23. I think the reason might be due to how different house prices could be in DC due to location even though they could possibly have the same number of features. For example, a house in southeast DC which is considered mostly low income could have the same number of features as a house in northwest DC which is considered higher income but sell for completely different prices. 

The current accuracy score for both models is ~9.0%

### Update 3

I made a huge mistake. I was using a classifier when I should have been using regression. I made the necessary changes to the RandomForrestRegressor and was able to achieve a higher accuracy!

The current accuracy score for the RFR model is ~35.0%
The current accuracy score for the LR model is ~14.0%

The type of models used was RandomForrestRegression and LinearRegression.

## Dashboard

[Tableau Dashboard](https://public.tableau.com/app/profile/dolores3708/viz/Final_Project_Draft/Story1?publish=yes)

Tableau is the Data Visualization Tool currently being used for this Project and will depict the following:
- Average Price by Location
- Home Sales By Year
- Map Depicting the Location of Schools in each Ward of DC
- Average Price by Number of Bedrooms
- Average Price vs. School Ranking
- Interest Rate by Year of Home Purchase

We were able to use our dashboard to answer two of our initial questions:

1. Does the rating of schools affect the home value? If so, how?
	
	We can see that schools with a higher ranking are located in a ward where the average home price is higher.
![Avg Home Pirce vs School Ranking](https://user-images.githubusercontent.com/89493488/153047576-f9a30b41-eb68-4050-ae8a-e1315f0ce1da.png)

2. How does Prime Rate affect home value?
	
	We can see that as the interest (prime) rate has decreased, the average home price has increased over time.
![Prime Rate vs Home Value](https://user-images.githubusercontent.com/89493488/153047600-f9f36b68-d7a0-4f40-b39c-53ea613f07e7.png)	

> Written with [StackEdit](https://stackedit.io/).
