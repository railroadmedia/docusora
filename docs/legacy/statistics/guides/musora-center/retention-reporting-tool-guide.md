# Subscription Retention Reporting Tool Guide

This tool is under the 'Retention Stats' menu item in Musora Center.

## The UI

**You can filter by:**

- Brand
- Interval type (the renewal schedule)
- Start and end date

'Average membership end' is still a WIP  
'Membership end' is still a WIP  

**The columns are:**

- Brand
- Subscription type: interval type
- Total subscribers: total users with an active subscription of this interval type at start of period
- Total users who repurchased or upgraded: if a user upgrades from monthly to yearly or re-purchases a subscription to 
get a better deal, they are counted as retained and move to the appropriate interval type
- Total users who renewed: amount of subscribers with a renewal payment during period an active subscription as of 
reporting end date
- Total users who canceled or expired: about of users who were scheduled to renew during report dates but did not
- Retention date: the percent of users who successfully renewed during period vs how many total were scheduled to renew

You can reproduce the rate with the column data and this formula:

(total users who renewed) / ((total users who renewed) + (total users who canceled or expired)) = retention rate

## The Technicals

[You can read about the formula and technicals here.](https://github.com/railroadmedia/ecommerce/blob/2.3-/docs/statistics/retention-reporting-formula-technicals.md)