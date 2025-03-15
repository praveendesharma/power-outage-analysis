**Introduction**

In this project, we will be exploring a dataset that recorded major power outages in the U.S - defined by the U.S. Department of Energy as outages that either affected a minimum of 50,000 customers or resulted in an unplanned energy demand loss of at least 300 MegaWatts - from January 2000 to July 2016. The data was sourced from Purdue University’s Laboratory for Advancing Sustainable Critical Infrastructure (available at https://engineering.purdue.edu/LASCI/research-data/outages). The original dataset comprises 1,534 observations across, where each entry corresponds to an outage, and 55 variables.

In addition to information on outages, the dataset provides extensive information on the affected states’ geographic, climatic, land-use, energy consumption, and economic profiles.

We will explore the following question: What is the relationship between the different classifications of regions, namely states and climate region, and the average outage duration?

We plan to explore how these classifications correlate with the length of power outages by developing models to analyse the data. This exploration is significant because understanding whether certain states or climate regions are more prone to prolonged outages can help energy providers and policymakers design targeted strategies. For instance, if a specific climate region consistently experiences longer outage durations, it could signal the need for improved grid resilience or more efficient emergency protocols, ultimately leading to more effective and proactive management of power infrastructure.

| Column | Description |
|--------|-------------|
| 'YEAR' | Year an outage occurred |
| 'MONTH' | Month an outage occurred |
| 'U.S._STATE' | State the outage occurred in |
| 'OUTAGE.DURATION' | Duration of outage events (in minutes) |
| 'CLIMATE.REGION' | U.S. Climate regions as specified by National Centers for Environmental Information (9 Regions) |
| 'CAUSE.CATEGORY' | Categories of all the events causing the major power outages |
| 'HURRICANE.NAMES' | If the outage is due to a hurricane, then the hurricane name is given by this variable |
| 'CUSTOMERS.AFFECTED' | Number of customers affected by the power outage event |
| 'POPULATION' | Population in the U.S. state in a year |
| 'PCT_LAND' | Percentage of land area in the U.S. state as compared to the overall land area in the continental U.S. (in %) |
| 'OUTAGE.START' | Date and time when the outage event started |
| 'OUTAGE.RESTORATION' | Date and time when power was restored to all the customers |


## Data Cleaning and Exploratory Data Analysis

### Data Cleaning

Before we begin our analysis, we need to clean our dataset. To do so, we perofrmed the following steps:

1. We combined `OUTAGE.START.TIME` and `OUTAGE.START.DATE` into a single timestamp column called `OUTAGE.START`, and combined `OUTAGE.RESTORATION.TIME` and `OUTAGE.RESTORATION.DATE` into a single timestamp column called `OUTAGE.RESTORATION`.

2. Next, we limited our dataset to columns that were relevant for our analysis. These are: `YEAR`, `MONTH`, `U.S._STATE`, `OUTAGE.DURATION`, `CLIMATE.REGION`, `CAUSE.CATEGORY`, `HURRICANE.NAMES`, `CUSTOMERS.AFFECTED`, `POPULATION`, `PCT_LAND`, `OUTAGE.START`, and `OUTAGE.RESTORATION`.

3. All the quantitative columns of the dataset were of the type object. While this did not affect any of the operations carried out with these columns, for consistency's sake we decided to make all qunatitative columns of type float. These columns are: `YEAR`, `MONTH`, `OUTAGE.DURATION`, `CUSTOMERS.AFFECTED`, and `POPULATION`.

4. Lastly, We only need to know if an outage is affected by a hurricane or not - we do not need to know the name of the hurricane for the purposes of our exploration. Hence, we decided to create a new column `is_hurricane` that contains *True* for all corresponding values in `HURRICANE.NAMES` that were not missing, and *False* for all corresponding vlaues that were missing (since this indicated that the outage was not affected by a hurricane).

The first few rows of the cleaned dataframe are shown below:


### Univariate Analysis

#### State Choropleths
First, we wanted to explore the average power duration by state to get a sense of how the power outage duration is distributed across the country.
(map)
Then we looked at a choropleth map for the number of power outages by state.
(map)
Then we looked at the average number of customers affected by state.
(map)


#### Climate Region Choropleths
Similarly, we wanted to explore the average power duration by climate region to get a sense of how the power outage duration is distributed across these regions.
(map)
Then we looked at a choropleth map for the number of power outages by climate regions
(map)
Then we looked at the average number of customers affected by climate regions
(map)


#### Total Population Choropleths by State and Climate Regions
In light of all the interesting patterns and unexpected insights we gained from the previous choropleths, we decided to map a distribution of populations by both states and climate regions to see if it could – to some extent – explain some of these patterns.
(map)


#### Insights from Univariate Analysis
From the 8 choropleths above we see can glean insights – some obvious others not so much. 

##### Average Outage Duration 

1. There's significant variation in outage duration across both states and climate regions
2. States in the upper Midwest (particularly Wisconsin and Michigan) and parts of the Northeast (New York) show longer average outage durations (shown in darker red)
3. By climate region, East North Central i.e the region surrounding the great lakes, show the longest average outage durations. Again this keeps in line with what we saw from the individual states in these regions.
4. The North West and West North Central regions generally have shorter durations (lighter colors). This keeps in line from what we see with the individual states of these regions.

##### Power Outage Count 

1. California stands out with the highest count of power outages at the state level.
2. When grouped by climate region, the Northeast has the highest concentration of outages
3. Many central and mountain states have very few recorded outages

##### Customers Affected 

1. South Carolina, Florida, and Texas show high numbers of affected customers
2. Climate regions with high population density (Southeast, South) show more affected customers
3. Some states with moderate outage counts still have high numbers of affected customers

##### Population Distribution 

1. California and Texas have the highest populations
2. In isolation there is not much else of note however the population choropleths help shape patterns in the other graphs.

##### The Interesting Insights:
1. There exists this frequency-duration paradox where while California has the highest count of outages (dark green in image 2), it has a relatively moderate average duration (light red in image 1). Conversely, Wisconsin and Michigan have fewer outages but much longer durations. From this, we learnt that systems that fail more often may be better at recovering quickly — a counterintuitive finding that challenges an assumption we thought to be obvious – which is that reliability and restoration speed go hand-in-hand.

2. The Northeast climate region shows both high outage counts along with longer durations of outages, but not proportionally high customer impacts. This suggests a pattern which is that outages in some regions are more localised but harder to fix. 

3. Comparing the customer affected to the population choropleths (images 3 and 4) show that some states with low population (like South Carolina) have disproportionately high numbers of affected customers. This could indicate that outages in these states tend to be more critical in nature affecting many people, rather than localized failures.


### Bivariate Analysis

#### Distribution of Outage Duration by Climate Regions

First, we explored the distribution of outage durations by climate region.
(plot)

Then we explore the average outage duration by cause for each climate region
(plot)

Next we explored the relationship between outage duration and customers affected
(plot)

