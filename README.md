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


**Data Cleaning and Exploratory Data Analysis**

Before we begin our analysis, we need to clean our dataset. To do so, we perofrmed the following steps:

1. We combined `OUTAGE.START.TIME` and `OUTAGE.START.DATE` into a single timestamp column called `OUTAGE.START`, and combined `OUTAGE.RESTORATION.TIME` and `OUTAGE.RESTORATION.DATE` into a single timestamp column called `OUTAGE.RESTORATION`.

2. Next, we limited our dataset to columns that were relevant for our analysis. These are: `YEAR`, `MONTH`, `U.S._STATE`, `OUTAGE.DURATION`, `CLIMATE.REGION`, `CAUSE.CATEGORY`, `HURRICANE.NAMES`, `CUSTOMERS.AFFECTED`, `POPULATION`, `PCT_LAND`, `OUTAGE.START`, and `OUTAGE.RESTORATION`.

3. 

