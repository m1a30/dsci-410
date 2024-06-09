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
- I found that when breaking down the missing age values, the reasons for dispatch of “Information Not Available” had 60% missing values, and “Check Welfare” had around 55% missing values, the other call classes had between 20%-40% of missing values. I attribute the larger percentages of missing age values to the fact that collecting demographic data, such as age, during an emergency isn’t always the most important thing. I ultimately decided to drop the NA values for the rest of my cleaning process. 
- The first dataframe I made for analysis was the dataframe for just age, so I dropped the columns I didn’t need (all but age) and the NA values
- Similarly, I made an Age and Reason for Dispatch Dataframe following the same steps as above
- I did the same to make an Age and City Dataframe 
- Then to answer my final research question, I imported the ACS Eugene and ACS Springfield data using the pandas read_csv, I kept only the “Age Groups” and “Age Groups Totals” columns and the rows from “Under 5 years” to “85 years and over” 
- Once I had the ACS data cleaned, I altered the CAHOOTS data to be in the same format, for easier comparison 

## Analytical steps
- For question 1, I made a histogram to visualize the distribution of ages of CAHOOTS calls and found the summary statistics of mean, mode, min, and max values
     - This was done using the packages of statistics, numpy, seaborn, and matplotlib.pyplot
- For question 2 
     - I created a heatmap of mean squared error to find the differences in age distributions between the different "Reasons for Dispatch"
     - I then created a smoothed kernel density plot in order to more easily see the differences between the age distributions of each reason for dispatch
          - To do this I used seaborn kdeplot
- For question 3
     - For this question I ran the analysis in R 
     - The first step I did was import the cleaned data into R 
     - Then I combined the Springfield and Eugene CAHOOTS data into a single dataframe 
          - With this combined dataframe, I made an overlaid density plot for the age distributions of each city
               - Using ggplot
     - I then ran a Kolmogorov Smirnov (KS) to see if the overall distributions were significantly different 
          - I used the R function ks.test
     - Lastly, I ran a t test to see how the means of the two groups differed
          - I used the R function t.test
     - To help with visualizing the means, I added corresponding colored lines to show where the mean ages are for Springfield and Eugene, using the R function mean to find the means
- For the 4th question I’m running a statistical test, Jonckheere Terpstra (JT) test, to see if the observed data from CAHOOTS matches up with estimated values from the ACS data from each city. To see exactly what groups are significantly different, I used a z-test for independent proportions
     - I first imported reshape2, DescTools, and ggplot2
     - The first step in this process was to import the cleaned CAHOOTS and ACS age data for both Springfield and Eugene from my cleaning file
     - To make sure that I had a better understanding of what the JT test did, I created fake data and tried out the JT test on that to see if the result was what I expected. It was for both a significant and non-significant difference
     - The next thing that I did was merge the ACS and CAHOOTS data together for Eugene and Springfield separately 
          - On this merged dataset for Eugene I ran the JT test
          - From DescTools the JT test is called as JonckheereTerpstraTest
     - The ACS data had larger numbers than the CAHOOTS data, so I scaled down the data to be proportions of each age group out of the total
     - Using the proportions, I created a paired barplot of ACS and CAHOOTS data for Eugene to better visualize these differences
     - I first melted the data to get the visualization using melt from the reshape2 library
     - To further analyze these differences, I wanted to know what groups specifically were different
     - I decided to create a for loop that would loop through each row of data, where each row is a different age group, and perform a z test for independent proportions between the ACS proportion and the CAHOOTS proportion
          - This was done using the prop.test function
- I repeated these steps on the Springfield data for CAHOOTS and ACS
