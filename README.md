# Analysis of COVID-19 and County Demographics

### Problem Statement
We would like to predict the number of COVID cases and deaths based on county demographics data. The goal is to build an accurate model in order to make inferences about how age, sex, and race affect COVID outcomes at the individual and county level. County demographics data is gathered from the government census database and can be found at https://data.census.gov/cedsci/table?q=demographics%20county&tid=ACSDP1Y2018.DP05&hidePreview=false. The data is from 2018 so I'm assuming that the demographics haven't changed drastically since then. The COVID data was gathered by the New York Times and can be found at https://github.com/nytimes/covid-19-data. 


### Executive Summary

To the National Governors Association,

the COVID-19 has devastated the world economy and killed thousands since its emergence in late 2019. It's completely upended our lives, changing the way we work and socialize. Although the average mortality rate might be low, the coronavirus is highly infectious and lethal to vulnerable populations. In order to minimize damage to the country and create effecitve policy, we need to understand what factors are relevant to reducing deaths and slowing the spread of COVID. At the same time, we need to keep in mind that prolonged lockdowns and restrictions will cause devastating long-term harm to the economy. Policy makers will need to weigh the information that they are given in order to strike a balance between re-opening the economy and keeping restrictions in place in oder to mitigate the damage that is being done to communities all over the country.


### Data Dictionary
The "data" folder has four csv files. The "us-counties.csv" file contains all of the covid cases and deaths by county. The data dictionary for this file is given below:

|Column|Type|Description|
|---|---|---|
|date|object|Specifies the date of the data point|
|county|object|The U.S. county of the data point|
|state|object|The state that the county is in|
|fips|float |A code that corresponds to the county and state |
|cases |int |Cumalitive number of COVID cases for a given county|
|deaths|int |Cumalitive number of COVID deaths for a given county|

The file "demographics.csv" is data from the government census database and contains the demographics data by county. The files contains 356 columns. The column name is a code. For example, the column name "DP05_0001E" is the first feature, total population, as indicated by the number after the underscore. The final letter "E" indicates that the column is an estimate. All column names start with "DP05" and will end with the following letters:

- "E", for estimate
- "M", for margin of error
- "PE", for percent estimate
- "PM", for percent margin of error

The description for each column is given in the first row. For this project, we will only use the estimates for each feature, which means that we will drop columns that end with an "M", "PE", or "PM". The fips code can be obtained from the column "GEO_ID". The trailing numbers after "US" is the fips code, which can be used to merge with the first dataset.

The two files are loaded into a dataframe in "COVID-county-analysis.ipynb". The files are cleaned and merged. Only data from the date 8/11/2020 is used.

The notebook "Additional-Data-Source.ipynb" draws COVID data from another source that gives information on the number of deaths by county, age groups, and sex. The idea is to use this to dataset for comparison when we make inferences using the "COVID-county-analysis.ipynb" notebook. 

In this second notebook, we will only be using four columns from the data file "covid_deaths.csv".


|Column|Type|Description|
|---|---|---|
|State|object|The U.S. State|
|Sex|object|Male or Female|
|Age group|object|Age group|
|COVID-19 Deaths|float |Deaths from COVID-19 |

We will also be using the 2018 state populations from "state_populations.csv". 


### Conclusion and Recommendation
COVID-19 hase clearly hit dense population centers much harder than areas less densely populated. Some EDA on "covid_deaths.csv" has revealed that older populations are at significantly higher likelihood of dying from COVID-19. The danger only grows exponentially with age. The data also shows that men are 16% high probability of dieing from COVID than women. Looking at the deaths to population ratio, we found that states on the east coast tended to have very high ratios while states inland fared much better. After fitting a model to the merged demographic-covid data, we found a statistically significant negative coeficient associated with counties in New Mexico. Doing a quick internet search reveals that New Mexico has relatively few cases. This might be due to the fact that they New Mexico was one of the earlier states to shutdown its economy and slower to reopening around June. In addition, the states has aggressively moved towards more frequent testing. Turnaround times for testing results are much lower due to the fact that one of the main testing facilities in the country is located in New Mexico. Information was obtained from this article https://www.santafenewmexican.com/news/coronavirus/with-low-positivity-rate-new-mexico-remains-an-island/article_1c297112-d66f-11ea-bf48-eb93dfab28c5.html. We were also able to infer that counties in Louisiana were doing very poorly in regards to keeping COVID cases down. ON race, we were able to infer that minorities from lower income communities, such as African American, latino, and American Indian populations tended to have higher number of cases compared to white and Asian populations. We believe that the cause of this disparity is due to income and class differences. Certain racial groups are, on average, lower income and are more likely to be essential workers. Unfortunately, we were unable to infer anything else about age groups or other states. Because it is still unclear whether or not children are actively spreading the virus, we should be careful about reopening schools as this may allow a path for the virus to infect a huge number of family households. Although it is incredibly unlikely for children to die from COVID, we still don't know the long term effects that the virus has on the body. Because elders are vulnerable, we should allow for some flexibility for family households with elder citizens to homeschool their children or allow for an online education. Learning from New Mexico, the state should increase the frequency of testing andminimize turnaround time by creating testing labs in their own states. Contact tracing should be used once states have their cases under control. 
