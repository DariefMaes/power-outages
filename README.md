# The impact of power outages on California and states in the USA

## Introduction

My dataset is about power outages in the United States. This dataset provides a good look of outages that happened across many states in the US. It reports a total of 1534 outages starting in January 2000 all the way to July 2010.

The dataset originates from the Purdue University’s Laboratory for Advancing Sustainable Critical Infrastructure. It can be found at: https://engineering.purdue.edu/LASCI/research-data/outages.

Power outages can be detrimental to economies, as it highly impacts production within cities, counties, states, and even entire countries. However, the state of California is the economic power house of the US, yet it has the most power outages in the entire country. How come it isn't impacted as much? I will be researching if California's customers per outage is significantly different from other states. This way we can figure out if as many customers are impacted by the outages compared to other states.

For my analysis, I will focus on the following columns from the original dataset:

| Column            | Description                                            |
| ----------------- | ------------------------------------------------------ |
| YEAR              | Year of the record                                     |
| MONTH             | Month of the record                                    |
| U.S.\_STATE       | U.S. state where the data was collected                |
| POSTAL.CODE       | Postal code of the location                            |
| NERC.REGION       | North American Electric Reliability Corporation region |
| CLIMATE.REGION    | Climate region classification                          |
| ANOMALY.LEVEL     | Level of climate anomaly                               |
| CLIMATE.CATEGORY  | Category of the climate conditions                     |
| CAUSE.CATEGORY    | Cause category for the outage or event                 |
| HURRICANE.NAMES   | Names of hurricanes involved, if applicable            |
| OUTAGE.DURATION   | Duration of the outage in hours or minutes             |
| RES.SALES         | Residential sales data                                 |
| COM.SALES         | Commercial sales data                                  |
| IND.SALES         | Industrial sales data                                  |
| TOTAL.SALES       | Total sales data across all categories                 |
| TOTAL.CUSTOMERS   | Total number of customers                              |
| PC.REALGSP.REL    | Per capita real GSP relative measure                   |
| PC.REALGSP.CHANGE | Change in per capita real GSP                          |
| PC.REALGSP.STATE  | Per capita real GSP for the state                      |
| TOTAL.REALGSP     | Total real Gross State Product                         |

## Data Cleaning and Exploratory Data Analysis

Throughout my datacleaning process, I ensured that I understood every variable first before I got to work. I looked at the missing data in 'CLIMATE.REGION' to see which ones weren't there. Especially Alaska and Hawaii were gone, which made sense due to their unique geographical location. I added both into the pacific region.

Another important thing to consider is the fact that states with under 5 outages can pose unusual patterns. If there once was only one outage with a high duration, it can be an usual outliar that won't help the research. Thus, I decided to drop all states with under 5 outages.

During my EDA, I wanted to see clear trends and abnormalities to figure out if something looked interesting. Especially as I stated before, I wanted to see if there was any correlation between outages and GSP. That is why I plotted it over the years. While in the beginning it seemed to be correlating a little, it wasn't as clear as I was expecting.

<iframe
  src="assets/outages-gsp.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This led me to studying the different states. Especially, if there were any particular outliers when it comes to the number of actual outages. Here, there was one state that had a lot of outages. California had more outages than any other highly populated state, like Florida, New York, and Texas.

<iframe
  src="assets/num_outages_state.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

My first thought was to look at this and link i through sales. However, in the sales it becomes more confusing as Texas has almost as much sales as California. Yet, they have almost half the total outages. Other states, like Washington, also have significantly less sales but more outages.

<iframe
  src="assets/sales_state.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

We could argue that Washington and other northern states have higher amount of outages due to their geographic location. Cold weather could impact the amount of outages. This is why I also wanted to look at the total customers per state. Here we see a more similar distribution with California and Texas leading the way.

<iframe
  src="assets/customers_outage_state.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Another important factor is outage duration. Longer outages combined with a lot of them can be detrimental to an economy. Espeically in highly populated areas, it can not only affect production but also human well-being. However, even though California has the most outages, thet have half the duration compared to Michigan.

<iframe
  src="assets/outage_duration.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
<iframe
  src="assets/top_outage_duration.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Focusing further on California, I was also curious if there is a trend over the years. Something odd that I had to see to understand a pattern. However, the trend seemed to be similar to the one from all states in the US and Calfornia's sales.

<iframe
  src="assets/outage_trend_cali.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Assessment of Missingness
