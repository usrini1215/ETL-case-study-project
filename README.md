# ETL-case-study-project
This is a case study for ETL on 2020 US Elections, by taking a few data sets.


#Project Team :
Jessica Nguyen and Usha Chari



#Project Objective:
To extract data from "data.fivethirtyeight.com" to transform and analyse 'election and polling' information and load them into a Mongodb database.



#EXTRACT 
Data Sources :
data.fivethirtyeight.com (polls + election-forecasts-2020 sections), 
Twitter feeds 

1.
`economic_index.csv` contains economic indicators that serve as inputs to the forecast. For more information on these indicators, see [this post](https://fivethirtyeight.com/features/measuring-the-effect-of-the-economy-on-elections/). The economic indexes were collected from the [Federal Reserve Bank Of St. Louis]( https://fred.stlouisfed.org/series/DSPIC96) and the stock prices data from [Yahoo Finance](https://finance.yahoo.com/). This sheet contains the following additional columns:

Column | Description
-------|------------
`indicator` | Name of the economic indicator
`category` | What that indicator helps measure
`current_zscore` | Number of standard deviations from the previous 2-year average for the current value of the indicator
`projected_zscore` | Number of standard deviations from the previous 2-year average for the projected value of the indicator on Election Day
`projected_hi` | Upper bound of an 80% confidence interval for `projected_zscore`
`projected_lo` | Lower bound of an 80% confidence interval for `projected_zscore`


2.
Presidential General Election Polling Averages
(2020) - Percentages for each candidate


3.
Twitter API to get data on Incumbent and Challenger (2 files)



#TRANSFORM :  The csv's were loaded into a pandas dataframe where we cleaned it up by dropping unwanted columns, renaming some, updating data to clean it up.  



#LOAD : Used pymongo to load them into Mongo DB into one database, 4 collections for the 4 data sets.

