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

I found out that all the columns I am using are MAR. I created a loop that looked over every column with missing values. Here I saw for example that outage.duration was MAR on multiple columns, including year. This means that YEAR played a big role in the reason why this value was missing at times. I saw this with multiple values. This explicitly tells me that the missingness of certain variables is due to explicit reasons and unavalability of certain data in outages. This also made me sure that I could use conditional imputation to fill the values, as I believed this wouldn't make the values bias.

<iframe
  src="assets/missing_year_outage_duration.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Hypothesis testing

Null hypothesis: The total customers per outage in California are the same as the total customers per outage in the other states customers per outage
Alternative Hypothesis: The total customers per outage in Californiais higher as the total customers per outage in the other states customers per outage

These questions show me exactly what I need to know. It shows me the total amount of customers in a state linked to the outages. This is interesting as we can thereby see if certain high populated areas, like California, have more people affected by outages compared to other states.

<iframe
  src="assets/hyp_cali.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Framing a Prediction Problem

I dedcided to create a regression predictor to predict the total sales of particular states. This can be important as states need to know how their total sales, and thus production, can be impacted by particular aspects. This can be total customers, but also how well the economy is even doing. If a state seems to be in an economic downturn, they can implement policies to boost the economy. I will predict TOTAL.SALES as this is mainly responsible for getting the total sales per state.

<iframe
  src="assets/sales_customer_state.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Baseline Model

For my baseline model, I will be using a simple Linear Regression model as it is simple and it can help me see which way I should go. I used state, real GSP relative to the US' GDP and the total customers. I one-hot encoded all the states. This model should be able to predict the total sales in basic levels. With this, I got an RMSE of 4.315. The total customers and real GSP relatieve to the US' GDP were not changed. This I did to incorporate the significance of bigger states onto the total sales.

<iframe
  src="assets/model_lin.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Final Model

For my final model, it was clear there was still work that had to be done. I used the columns: 'TOTAL.CUSTOMERS', 'PC.REALGSP.REL', 'U.S.\_STATE', 'PC.REALGSP.STATE', 'TOTAL.REALGSP', where they were all numerical. I added a standard scaler to all of them and one-hot encoded state. Here we also added hyper params and used-kfold of 5 to see which hyper parameter and model performed best. It was clear that the RandomForest was the winner with a RMSE of 2.99

<iframe
  src="assets/model_rf.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Fairness Analysis

My fairness anaysis showed it wasn't fair towards High GSP states,as it had a higher RMSE. This we need to take into consideration.
