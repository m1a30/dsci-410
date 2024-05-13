## Analytical steps

- I plan to make visualizations that will more easily answer questions 1 through 3 using the matplotlib.pyplot and seaborn packages

- For the 4th question I’m running a statistical test to see if the observed data from CAHOOTS matches up with estimated values from the ACS data from each city 
- In order to do this, I had to move over to R and import the stats library to use the chi-squared test function, to run the Chi-Squared Test for Given Probabilities
- This method is used when there’s an expected probability known beforehand and in this case the ACS data is being used as the expected counts/probabilities of ages in Eugene and Springfield. Then this is being compared to the observed counts of the CAHOOTS data. 
- The input is the CAHOOTS data and ACS data for each city, because there are more ACS data points than CAHOOTS I scaled down the ACS data to match the scale of CAHOOTS
    - The CAHOOTS counts and the scaled proportions of ACS data are the inputs
    - The output is an X2 value, degrees of freedom, and a p-value that will be compared against the significance value of 0.05.
- This will be done for Eugene and Springfield separately 

