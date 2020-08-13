# Quick Links

Basecamp Project: [https://app.asana.com/0/1186319650975745/board](https://app.asana.com/0/1186319650975745/board)  
Emergency Contact Info: [https://basecamp.com/1792144/projects/16655061/documents/14383392](https://basecamp.com/1792144/projects/16655061/documents/14383392)

# Bug Reporting Guide

## Who, Where, and What To Do

- **If the severity is HIGH:**
    - Contact Caleb or another available developer immediately over Slack/email, or in person
    
    - Create a new task in Asana under the "Initial Report" column following the template below. Under the "Priority" field, select "High".
<br>

- **If the severity is MEDIUM or LOW:**
    - Create a new task in Asana under the "Initial Report" column following the template below. Under the "Priority" field, select "Medium" or "Low".
    - Try to avoid reaching out to or discussing with a developer in person if the issue severity is not high. If an issue needs to be discussed in person or it would be much more efficient to chat in person please schedule a meeting time to do so where both parties agree on the date/time. If the dev team specifically requests you reach out to them directly for a given project or launch, definitely reach out directly anytime you see fit.
    
    - Feel free to reach out to Jon C (QA) about a bug/problem anytime over Slack or in person! He is in charge of handling how bugs are managed between support and dev and would love to chat or help you through an issue.
    <br>

- **Escalating bugs:**
    - You may get a single user report for an issue and post about it in basecamp as medium or low severity. If you later get more user reports about the same bug, please make note in the appropriate task to escalate it, and feel free to edit the "Priority" field at any point. A bug for 1 user is usually pretty benign. A bug for 10 users generally means something major is wrong.
    <br>


## Bug Report Template
1. **Title:**
    - A single sentence description of the issue
    - Ex: Refunding a user's subscription returns an error
    - Ex: Users get an error when submitting a comment
<br>

2. **Assignee:**
    - This field will be automatically filled in upon creation of a new task.
<br>

3. **Due Date:**
    - This field for developer use only and can be ignored.
<br>

4. **Projects:**
    - This field for developer use only and can be ignored.
<br>

5. **Priority: HIGH, MEDIUM, LOW (choose one)**
    - HIGH: bug is effecting business critical features and has been reported by multiple users, and it's user facing
        - Ex: Customers getting error when ordering
        - Ex: Incorrect pricing issues on the order form
        - Ex: Large sections or the entire members' area not working
    - MEDIUM: support has received multiple reports, but it's a non business critical issue
        - Ex: Course X gives an error and does not load
        - Ex: Users get error when trying to comment on any lesson
    - MEDIUM: support is unable to do a requested action for any user
        - Ex: Getting an error when trying to refund any payment
        - Ex: Button to view any users payments is not functional
    - LOW: only 1 user reported the issue, and it's not related to business critical features
        - Ex: User X cannot load video Y on his Z machine
        - Ex: User X reports getting an error when trying to cancel his subscription
    - LOW: support cannot perform an action for 1 specific user:
        - Ex: I cannot refund payment X for user Y, however other users payments can be refunded successfully
        - Ex: Order placed for user X has problems
    - If you are unsure about which priority an issue should be assigned, feel free to reach out to Jonathan C.
<br>

6. **Affected Brand:**
    - Please select the brand the issue affects/applies to. Please note that issues for the Drumeo/Pianote apps will have their own option here. If an issue exists across multiple brands, please select the "Musora/Crossbrand" option.
<br>

7. **Platform:**
    - What the customer was using to access out content when the initial issue was encountered, eg: iOS version number, Device make and model, App version, Browser version, Operating System, etc.
    - Depending on the type of bug, this field may be left blank when issue clearly exists across all platforms. 
    - If subsequent users encounter an issue after the initial report, their platform details should be included in the comments when the additional cases are reported.
<br>

8. **Number of reports/Affected Users:**
    - If the issue reported seems isolated to a certain subset of users, please indicate the number of people who have encountered it.
    - If issue is obviously widespread and affects everyone, field can be left blank.
<br>

9. **Description:**
    - This field is for all information not already covered by the fields above, including:
        - Detailed description of the issue
        - Steps taken to reproduce the issue
        - Musora ID/Email of user/s who encountered the issue, as well as all other relevant details including order numbers, specific payment methods, specific subscription, etc.
        - Any images/videos/screenshots demonstrating or pertaining to the issue at hand
        - Any other relevant information provided by user or encountered during reproduction
        - Any post-fix tasks that need to be completed once issue is resolved.
        <br>

7. **Collaborators:**
    - People tagged in this section will be notified of the creation of, as well as any updates to the task. By default, the creator, Jon C. and Caleb will be added, anyone else who would like to be notified can opt-in here. Likewise, remove yourself at any point to stop receiving updates and status changes related to this task.
        <br>


## Full Examples

- Title: Getting an error when trying to expire a user's product access
- Priority: Medium
- Affected Brand: Musora/Crossbrand
- Platform: -
- Number of reports/Affected Users: All Pianote products 
- Description: User has product "pianote-1-month-membership", expiry date cannot be edited. Attempting to change date results in "Error editing user product".
users email: caleb@drumeo.com, user product: pianote-1-month-membership. User product needs top be expired once bug is fixed.


---
 
- Title: Users receiving "Oops, something went wrong." error when trying to place order through app
- Priority: High
- Affected Brand: Drumeo App
- Platform: Seems to all be iOS users
- Number of Reports/Affected Users: lots
- Description: A whole bunch of users are just getting an error after confirming their signup through apple's payment confirmation window. caleb@drumeo.com, jonc@drumeo.com, jonc+2@drumeo.com, jonc+3@drumeo.com and others reported not being to sign up. Musora accounts were created with their emails, but there is no payment history or valid subscription. The above users have been manually granted 7 days of access for the time being. Users received no receipt from Apple. Screenshot of error attached below.

--- 

- Title: User claims video playback freezes a couple minutes into every video
- Priority: Low
- Affected Brand: Pianote
- Platform: iPad 2, iOS 6.1.5, Safari, Legacy player (New player not supported)
- Number of Reports/Affected Users: 1
- Description: User jonc+myiPadis13yearsold@drumeo.com claims that all videos will freeze playback at 4:20 in and cannot be started again. Refreshing the page does not help, but they can proceed further by scrubbing past that point in the lesson manually. User has tried other browsers with the same result, but also says issue is not present on their iPhone 14XSRMaxPlusSE2. Could not reproduce on my own iPad(Air 2).

<br>
