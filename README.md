# Project 1 - Characterization of US Counties with High and Low Population Densities

- Group Members:
	- Morgen Henry
	- Mark Speers
	- Oliver Einarsson
	- Ryan Krause
	- Gina Fender

## Project Description

- Data Source:
	- US Census: https://www.ers.usda.gov/data-products/county-level-data-sets/ 
- Questions Answered:
  - Are most counties in the US densely or sparsely populated?
    - Most US counties are sparsely populated.
  - Are most counties in the US similar in size?
    - No, county size can range from almost 20,000 square miles to slightly more than 300 square miles.
  - Does it cost more to live in a densely populated county?
    - Yes, while the most sparsely populated require between $400 and $1000 per month for rent, most densely populated cities require $700 and $1200 per month for rent.
  - Do workers in densely populated counties have a higher income?
    - This depends if you are considering income per capita or median household income. Median household incomes are similar between counties with high and low population densities, while there is a higher income per capita in densely populated counties than sparsely populated counties.
  - What highest level of education is most common in dense versus sparse counties?
    - A higher percentage of people have a Bachelor's or higher in densely populated counties than in sparsely populated counties.
  - Do you need to have a high level of education to have a high income in US counties?
    - Yes, in both sparsely and densely populated counties, a higher education correlating with a higher income.
- Data Analysis
  - For all relationships examined, significance values, produced by either ordinary least squares regression or Pearson's Correlation Coefficient, were used to determine whether a relationship was worth presenting. If the relationship was NOT significant, the regression was not reported on the scatter plot. If the relationship was significant, a linear regression was presented in the visualization. 
  - Additionally, a Welch's t-test for independent means was conducted to assess whether average income per capita for low density counties (<250 $mi^2$) was significantly different from average income per capita for high density counties.  

# File Structure
There are three folders in this repository which contain the files of primary importance. The notebooks folder contains all jupyter notebooks used throughout the project. The outputs folder contains all visualizations produced during the analyses. These are saved as png files. The third and final folder contains all csv files used. A brief description of each is provided below. 

## Notebooks Folder
Three notebooks are in this folder: dataSourcingCleaning, eco_health, and education_visual. 

1. dataSourcingCleaning.ipynb
    - This notebook contains all steps of data sourcing/merging. Some of the data was sourced using the [Census wrapper](https://github.com/datamade/census) while other census data was pulled from the [U.S Department of Agriculture Website](https://www.ers.usda.gov/data-products/county-level-data-sets/). All data gathered at the county level. 
    - Several cleaning steps were necessary to ready the data for analysis. 
    - After missing data was removed, and the county column was split into state and county columns, a three-part merge was performed. The merge was performed on the County and State columns to ensure as little duplicates as possible. 
      - Subsequent to merging, our main variable of interest, population density, was calculated by dividing a county's total population by its land area in square miles. 
    - The three part merge was the last step in this notebook. 

2. eco_health.ipynb
    - This notebook contains most of the code used the conduct the analyses and produce the visualizations. 
    - First, this notebook contains exporatory analyses and further cleaning of the data. This includes some histograms and boxplots. 
    - Based upon the above investigations, missing values were removed and it was decided that the data would be split into two categories, low density and high density, based on population density. The cutoff value, 249 people per $mi^2$ was determined using the $1.5 * IQR$ rule. Thus, all counties with less than 249 people per square mile were considered low density counties, and all others were considered high density counties. All subsequent analyses were peformed separately on these two subsets. 
    - Variables examined in relation to population density 
      - Median Gross Rent
      - Size of County ($m^2$)
      - Income per capita
      - Education Rates
    - Scatter plots were produced for all of these relationships. Additionally, linear regressions were performed on those variable pairs that had statistically significant relationships. Most of the relationships, even when significant, were extremely weak. Usually the explained variance values or Pearson's r values were below .2. 
    - Lastly, two heatmaps were produced using correlation matrices for the low & high density subsets. We didn't think to do this until we were practically done with the project. One lesson learned is that we could have used these heatmaps to do what we did more efficiently. We would not have to produce scatter plots of every relationship if we had looked at the heatmaps first, but hindsight is 20-20 and we'll remember for next time to check the heatmap for strong relationships first. 

3. education_visual.ipynb
    - This notebook contains all the code used to produce the scatter plots of education rates vs. population density. These were produced in a separate notebook because there were so many visualizations necessary to capture all levels of education. 



## Outputs folder
This folder contains all visualizations produced in the notebooks described above. All visualizations were saved as png files so that they could be used in our presentation


## Data Folder
This folder contains the two data files that were merged together to produce the dataset we analyzed. The two datasets in this folder were sourced from the [U.S Department of Agriculture Website](https://www.ers.usda.gov/data-products/county-level-data-sets/).

