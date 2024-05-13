# Data cleaning/processing steps

First, I imported all the packages I will be using, numpy, pandas, matplotlib.pyplot, and seaborn. 
I loaded my CAHOOTS 2021 and 2022, as well as the CAHOOTS 2023 data into my Jupyter Notebook using pandas read_csv function
Then I merged the two datasets together using pandas merge
I wanted to tackle what to do with the NA values so I explored whether there was a correlation between reason for dispatch and whether or not there was a NA value for age.
I found some insight into the reason for dispatch and whether or not there was an NA value for age, but ultimately decided to drop the NA values for the rest of my cleaning process
The first dataframe I made for analysis was the dataframe for just age, so I dropped the columns I didn’t need (all but age) and the NA values
Similarly, I made an Age and Reason for Dispatch Dataframe following the same steps as above
I did the same to make an Age and City Dataframe 
Then to answer my final research question, I imported the ACS Eugene and ACS Springfield data using the pandas read_csv, I kept only the “Age Groups” and “Age Groups Totals” columns and the rows from “Under 5 years” to “85 years and over” 
Once I had the ACS data cleaned, I altered the CAHOOTS data to be in the same format, for easier comparison 
