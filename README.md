# ETL-case-study-project - Technical Report
This is a case study for ETL on 2020 US Elections, by taking a few relevant data sets, out of many.


#Project Team:
Jessica Nguyen and Usha Chari


#Project Objective:
To extract data from "data.fivethirtyeight.com" + Twitter to transform and analyze 'election and polling' information and load them into a MongoDB database.



Technical Aspects
#EXTRACT 
Data Sources:
data.fivethirtyeight.com (polls + election-forecasts-2020 sections), 
Twitter feeds on the Incumbent and Challenger (Trump abd Biden)

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
Twitter API to get data on Incumbent and Challenger data (2 twitter scrapes)



#TRANSFORM :  
The csv's were loaded into a pandas dataframe where we cleaned it up by dropping unwanted columns, renaming some, updating data to clean it up.  These were the various transformation steps taken:
    - Drop unwanted columns in the data which were repetitive across the whole csv
    - Rename columns to make relevance
    - One of the csv was of a different structure where Trump and Biden data were in different records.  So did a 'loc' to locate the separate records for each candidate, split them, and merged back by 'Date' so the structure matched out other file.
    -After merging we had to rename the merged columns as well
    - Twitter data was limited to latest responses on a particular tweet and a certain number of replies only, just so we can filter to a manageable number of tweets.
    - Twitter data was also converted to a dataframe from csv and left as 'usr' and 'text' 




#LOAD : Used ‘pymongo’ to load them into Mongo DB into one database, 4 collections for the 4 data sets.
- We decided to go with Mongo as we dealt with a data set like Elections, which is continually changing in structure so anytime we re-extract this data, we could use the Mongo script as is even if the structure of the data changed drastically. 
- For the load, we created a function that takes in any dataframe as an input and converts to a Mongo db/collection set.
- Also preferred Mongo as we don’t need to set up the create scripts and other db level information.  Was instantaneous to see our data from the dataframes
- Schema-less database helped with this dataset we chose.
- If the twitter data were to be large data set, Mongo will handle it faster (though for the project we limited the records)


