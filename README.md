# ETL-case-study-project
This is a case study for ETL  on 2020 US Elections


Project Team :
Jessica Nguyen
Usha Chari



Project Objective:
To extract data ffrom data.fivethirtyeight.com to transform and analyse 'election, polling and economic index' information and load them into a Mongodb database.



Data Sources:
data.fivethirtyeight.com (polls, election-forecasts-2020 sections)
1.
`presidential_ev_probabilities_2020.csv` contains the forecasted chances of every possible Electoral College outcome. This sheet contains the following additional columns:

Column | Description
-------|------------
`evprob_inc` | Chance that the incumbent wins `total_ev` electoral votes
`evprob_chal` | Chance that the challenger wins `total_ev` electoral votes
`evprob_3rd` | Chance that the third-party candidate wins `total_ev` electoral votes
`total_ev` | Number of electoral votes in question

2.
Presidential General Election Polling Averages
(2020)](https://projects.fivethirtyeight.com/2020-general-data/presidential_poll_averages_2020.csv)



Transform :
