# Membership Reporting Tool Guide

This tool is under the 'Membership Stats' menu item in Musora Center. Numbers are represented **per user**, not per 
subscription since users can have multiple subscriptions.


## The UI

### Filters

- Brand
- Interval type (the renewal schedule)
- Start and end date

**You can also export the current results to a CSV using the cloud download icon in the top right hand corner of the 
table.**  


### Rows & Interval Types

Each day has a set of associated rows. One row per individual Interval Type and one row with all the Interval Types 
added together for that day.

**one month**  
Members on a recurring subscription, billed every 1 month. This includes all trial memberships.

**six months**  
Members on a recurring subscription, billed every 6 months.

**one year**  
Members on a recurring subscription, billed every 1 year.

**lifetime**  
Members who have purchased lifetime access and do not have a recurring subscription.

**other**  
Members who have access from an alternative method, such as from an access/gift code, or a single one time edge 
access product.

**all**  
All the other "Interval Type" rows for the given "Stats Date" and "Brand" summed.


### Columns

**Brand**  

**Interval Type**  
As explained in "Rows & Interval Types".

**Stats Date**  
Shows the date which the rows data is for.

**New In Day**  
Total new users who gained access to member only content for the given "Interval Type" and
during the 24 hours after the "Stats Date". 

**Expired In Day**  
Total users who lost access due to a failed renewal payment for the given "Interval Type" and
during the 24 hours after the "Stats Date". 

**Cancelled In Day**  
Total users who canceled their membership via their profile or via the support team for the given "Interval Type" and
during the 24 hours after the "Stats Date". Cancelled means the user manually requested to cancel their subscription 
from their profile or through our support channels.

**Total Active State**  
Total users who have an active recurring subscription for the given "Interval Type" at the end of the day 
on the "Stats Date". For "lifetime" and "other" interval types, this is just the total count of 
people who have that type of access which may expire at anytime in the future.

**Total Expired State**  
Total users who have a expired/suspended recurring subscription for the given "Interval Type" at the end of the day 
on the "Stats Date". Expired/suspended means the subscription failed to renew.

**Total Cancelled State**  
Total users who have a cancelled recurring subscription for the given "Interval Type" at the end of the day  
on the "Stats Date". Cancelled means the user manually requested to cancel their subscription from 
their profile or through our support channels.

**Note: "Other" and "Lifetime" interval types only have "New In Day" and "Total Active State" statistics.**


## How The Numbers & Statistics Work Together

The numbers cannot always be added together to get the following days numbers. This is because depending on when the 
stats for that given day are calculated will only affect the data for that point in time. For example if we calculate 
new stats for Jan 01 on Jan 02, and a single user signs up on Jan 01 so the new is 1. That user may then cancel on Jan 
02, so if we were to calculate the stats for Jan 03, the numbers over those 3 days will no longer add up correctly. 
This idea gets exponentially worse as the user base expands and because users often sign up and cancel in the same 
day. The purpose of these stats is not to keep a historical record of peoples subscriptions over time, but rather give a 
snapshot of the what the membership numbers are for a given day at that point in time.


## Examples Of Usage

### How Much Did The Drumeo Membership Grow Over January of 2020?
 
1. Set "Brand" to "drumeo"
2. Set "Interval Type" to "Sum of the membership types"
3. Set "Start/End Dates" to "2020-01-01" and "2020-01-31"
4. Note the "Total Active State" number on Jan 01
5. Note the "Total Active State" number on Jan 31
6. Subtract the numbers: 12429 - 10257 = 2172

The drumeo membership grew by 2172 over January 2020. We can do this same thing for any "Interval Type" if you wish.

### How Many New Drumeo Members Signed Up Over January of 2020?

1-3. Same as above
4. Copy data to spread sheet or export to csv
5. Sum the "New In Day" column
6. 2893 new memberships were started during January 2020

We can do this for any of the "* In Day" columns and for any "Interval Type".