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
