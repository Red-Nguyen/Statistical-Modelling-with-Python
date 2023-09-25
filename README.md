# Final-Project-Statistical-Modelling-with-Python

## Project/Goals

	My goals for this project include gaining hands-on experience in calling APIs to collect detailed information from various websites, merging DataFrames, and performing exploratory data analysis (EDA). Additionally, I aim to practice how to create and query databases in Python and build a regression model.

## Process

### Step 1: 
	- Call bike station data from the CitiBikes API to get Json file.
	- Query to get all cities in Canada that have a network at CitiBikes and pick up a network in Vancouver for the project.
	- Json from CitiBikes into dataframe. Cleaning & EDA station data from Vancouver.
	- Export the final dataframe to .csv file.
			
### Step 2: 
	- Call Foursquare and Yelp API to get POIs (points of interest) for bars & restaurants based on specific latitude & longitude for each station_id in Vancouver with a radius of 1000m. Parse the Json into dataframe.
	- Cleaning 2 dataframes from Foursquare and Yelp. 
	- Compare the quality of the Yelp and Foursquare API.
	- Export both dataframes to .csv file.
			
### Step 3: 
	- Import file .csv from step 1, 2 files .csv from step 2.
	- Cleaning 3 dataframes again before joining to make sure there is no null and no outlier.
	- I chose to join dataframe of Yelp and CitiBikes together (used id of station) because: Yelp is more location-specific than Foursquare as I demonstrated in part 2. POIs of Yelp are more specific than Foursquare.
	- Use data visualization to explore the data. The purpose is to understand the basic relationship between columns.
	- Put all my results in a SQLite3 database: 
		I created a new database, there are 2 tables in my database. 1 table is dataframe joint from Yelp& CitiBikies, and 1 table is dataframe of Foursquare.
		Query to check the value in the new database to make sure no missing data. 
		Query to join table 1 & table 2.
	
### Step 4:
	- Connect database from step 3. 
	- I used CitiBikies & Yelp table to build a regression model using Python's `statsmodels` module to show the relationship between numbers the free_bicycles and the characteristics of the POIs in Vancouver.
	- Multivariable regression to predict a dependent 'free_bikes' variable based on multiple independent variables.
	- I also use Simple linear regression to predict a dependent 'free_bikes' variable based on each independent variable.
	- Because R-Square is very slow, I try to use plot histograms to understand the shape, center, and spread of data, as well as to identify any potential outliers or skewness. Then, transformations to make the dataset more suitable for linear regression.
	- At stretch work, to turn the regression model into a classification model. Instead of predicting the exact number of free bikes, I will predict whether a station has "Low", "Medium", or "High" numbers of free bikes available.

## Results
	- Result: API Yelp provided more locations than API Foursquare (Foursquare: 593 bars & restaurants, 827 bars & restaurants). Yelp also gives more details than Foursquare in price and rating.
	- Results of my model: Use a multivariable regression model (dependent: 'free_bikes', independent: 'mean_rating, mean_price, mean_distance, mean_review_count') and the R-squared value is 0.073, which is close to zero. This suggests that only about 7.3% of the variability in free_bikes is explained by the model and it shows a poor fit to the data. So, I tried to use Simple linear regression to predict a dependent 'free_bikes' variable based on each independent variable, the result still shows R-squared is very low too. I also tried another way of transformations to make the dataset more suitable for linear regression, and R-squared is also slow, only 0.075.
	
## Challenges 
	- Yelp API: I always reach "Rate limit reached" when calling API at Yelp. Same structure code, I can call too many times at Foursquare, but I only call couble times at Yelp and this step takes too much time for my project.
	- The data sources from Yelp and Foursquare are online and dynamic. If I revisit part 2 of this project and wish to update my code, I'll have to call the APIs again. Since these platforms continuously update their information, the results may change. Consequently, I might need to rerun all of my code to accommodate the updated data.
	
## Future Goals
	I would like to understand the relationship between variables (dependent & independent). I also want to know the prediction of dependent free_bikies.