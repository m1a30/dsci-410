# dsci-410

## Research Questions

The research questions I will be pursuing are: What populations are served by CAHOOTS, or more specifically, what is the overall breakdown of age groups that are most to least aided by CAHOOTS? How does age breakdown differ over the different classes of calls? How does age breakdown differ between Eugene and Springfield? And how do CAHOOTS age demographics align with census data from Eugene and Springfield? I chose these questions because knowing the specific groups that CAHOOTS serves can help the organization provide proper staffing and training based on the age groups it is most commonly serving. Knowing the age breakdowns can also help CAHOOTS to identify vulnerable groups and develop strategies to support those groups. 

## Data Description

The data that I’m using to address research questions are the CAHOOTS 2021, 2022, and 2023 call data. I received this data from CAHOOTS. I’m using just the CAHOOTS data to address the first 3 questions (What populations are served by CAHOOTS, or more specifically, what is the overall breakdown of age groups that are most to least aided by CAHOOTS? How does age breakdown differ over the different classes of calls? How does age breakdown differ between Eugene and Springfield?). For the first question I just used the age observations column, for the second question I used both the age and reason for dispatch columns, and for the third question I used the age and city columns. For my 4th question I utilized the CAHOOTS data as well as American Community Survey 5-Year Estimates Subject Tables for Eugene (S0101: Age and Sex—Census Bureau Table. (n.d.). Retrieved May 12, 2024, from https://data.census.gov/table/ACSST5Y2022.S0101?g=160XX00US4123850&tid=ACSST5Y2022.S0101), in the upper right corner go to more tools and hit csv which will download the data I utilized, and Springfield (S0101: Age and Sex—Census Bureau Table. (n.d.). Retrieved May 12, 2024, from https://data.census.gov/table/ACSST5Y2022.S0101?q=springfield%20oregon), again for this data, click on the upper right corner go to more tools and hit csv which will download the data I utilized. From the CAHOOTS data I utilized the city and age columns and for the ACS data I used the estimates of the counts of how many individuals there are in each age group (row). An important caveat of the CAHOOTS data is that there are many missing values (roughly ½ of all the data entries were missing an age data input). An important limitation of the ACS data is that it doesn’t provide a continuous count of how many individuals there are at every age, it instead bins the ages into 5 year groups.

## Data cleaning/processing steps

- First, I imported all the packages I will be using, numpy, pandas, matplotlib.pyplot, and seaborn. 
- I loaded my CAHOOTS 2021 and 2022, as well as the CAHOOTS 2023 data into my Jupyter Notebook using pandas read_csv function
- Then I merged the two datasets together using pandas merge
- I wanted to tackle what to do with the NA values so I explored whether there was a correlation between reason for dispatch and whether or not there was a NA value for age.
- I found some insight into the reason for dispatch and whether or not there was an NA value for age, but ultimately decided to drop the NA values for the rest of my cleaning process
- The first dataframe I made for analysis was the dataframe for just age, so I dropped the columns I didn’t need (all but age) and the NA values
- Similarly, I made an Age and Reason for Dispatch Dataframe following the same steps as above
- I did the same to make an Age and City Dataframe 
- Then to answer my final research question, I imported the ACS Eugene and ACS Springfield data using the pandas read_csv, I kept only the “Age Groups” and “Age Groups Totals” columns and the rows from “Under 5 years” to “85 years and over” 
- Once I had the ACS data cleaned, I altered the CAHOOTS data to be in the same format, for easier comparison 

## Analytical steps
- For question 1, I have made a histogram to visualize the distribution of ages of CAHOOTS calls and found the summary statistics of mean, mode, min, and max values
     - This was done using the packages of statistics, numpy, seaborn, and matplotlib.pyplot
- For question 2 - I created a heatmap of mean squared error to find the differences in age distributions between the different "Reasons for Dispatch", and significant resulting visualizations to help see the differences and similarities in the distributions.
- For question 3 - I need to create a visualization to help see the similarities and differences between the distributions of Eugene and Springfield based on CAHOOTS data. I also ran a KS test to see if the distributions were significantly different, and t test to see how the means of the two differed.
- For the 4th question I’m running a statistical test to see if the observed data from CAHOOTS matches up with estimated values from the ACS data from each city 
- In order to do this, I had to move over to R and import the stats library to use the chi-squared test function, to run the Chi-Squared Test for Given Probabilities
- This method is used when there’s an expected probability known beforehand and in this case the ACS data is being used as the expected counts/probabilities of ages in Eugene and Springfield. Then this is being compared to the observed counts of the CAHOOTS data. 
- The input is the CAHOOTS data and ACS data for each city, because there are more ACS data points than CAHOOTS I scaled down the ACS data to match the scale of CAHOOTS
- The CAHOOTS counts and the scaled proportions of ACS data are the inputs
- The output is an X2 value, degrees of freedom, and a p-value that will be compared against the significance value of 0.05. 
- This will be done for Eugene and Springfield separately 



