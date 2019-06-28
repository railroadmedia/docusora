# Bug Reporting Guide

## Who, Where, and What To Do

- **If the severity is HIGH:**
    - Contact Caleb or another available developer immediately over gchat/email, or in person
    
    - Create a basecamp todo using the template below in the 'High Priority' todo list, notify the entire 'Dev Team' and 'Customer Support' teams in the 'Let me choose who should get an email…' section
<br>

- **If the severity is MEDIUM or LOW:**
    - Create a basecamp todo using the template below in the 'Medium Priority' or 'Low Priority' todo list, notify only 'Jonathan Chiu' and the 'Customer Support' team in the 'Let me choose who should get an email…' section
    - Try to avoid gchatting or discussing with a developer in person if the issue severity is not high. If an issue needs to be discussed in person or it would be much more efficient to chat in person please schedule a meeting time to do so where both parties agree on the date/time. If the dev team specifically requests you reach out to them directly for a given project or launch, definitely reach out directly anytime you see fit.
    
    - Feel free to reach out to Jon C (QA) about a bug/problem anytime over gchat or in person! He is in charge of handling how bugs are managed between support and dev and would love to chat or help you through an issue.
    <br>

- **Escalating bugs:**
    - You may get a single user report for an issue and post about it in basecamp as medium or low severity. If you later get more user reports about the same bug, please post in the relevant basecamp thread to escalate it. A bug for 1 user is usually pretty benign. A bug for 10 users generally means something major is wrong.
    <br>


## Bug Report Template
1. **Title:**
    - A single sentence description of the issue
    - Ex: Refunding a users subscription returns an error
    - Ex: Users get an error when placing a comment
<br>

2. **Brand/App:**
    - Which brand or website does this bug apply to?
    - drumeo, pianote, musora, drumeo mobile app, etc
<br>

3. **Severity: HIGH, MEDIUM, LOW (choose one)**
    - HIGH: bug is effecting business critical features and has been reported by multiple users, and its user facing
        - Ex: Customers getting error when ordering
        - Ex: Incorrect pricing issues on the order form
        - Ex: Large sections or the entire members area are not working
    - MEDIUM: support has received multiple reports, but its a non business critical issue
        - Ex: Course X gives an error and does not load
        - Ex: Users get error when trying to comment on any lesson
    - MEDIUM: support is unable to do a requested action for any user
        - Ex: Getting an error when trying to refund any payment
        - Ex: Button to view any users payments is not functional
    - LOW: only 1 user reported an issue and its not related to business critical features
        - Ex: User X cannot load video Y on his Z machine
        - Ex: User X reports getting an error when trying to cancel his subscription
    - LOW: support cannot perform an action for 1 specific user:
        - Ex: I cannot refund payment X for user Y, however other users payments can be refunded successfully
        - Ex: Order placed for user X has problems
    - If you are unsure about which severity level an issue should be reported under feel free to ask your nearest developer
<br>

4. **Preconditions:**
    - Information about the user in question, such as email, shipping address, or order number
    - Information about the users device and browser (not required for musora center related issues)
<br>

5. **Reproduction:**
    - A description of what the bug reporter was doing when they ran in to the issue
        - Ex: went to lesson page, scrolled to down to comment X, clicked reply, typed in reply, clicked submit, saw error message
        - Ex: went to a users overview page, clicked to load a subscriptions payments, clicked refund button, entered amount, clicked submit, saw error message
    - This is the most important part of a bug report so the more information the better
<br>

6. **Other:**
    - Anything else which may be helpful to the developers
<br>

7. **Post-Fix Tasks:**
    - Once the bug is fixed, what task needs to be completed if any?
        - Ex: Refund user X payment Y for amount Z
        - Ex: Place order for user X with products Y and price Z
        - Ex: Delete comment X for user Y
        - Ex: Notify user X when this fixed
        <br>


## Full Examples

- Title: getting an error when trying to expire a users product access
- Brand: musora
- Severity: medium
- Preconditions: users email: caleb@drumeo.com, user product: pianote-1-month-membership
- Reproduction: click edit button, changed date to today, clicked save, saw error message saying "Error editing user product"
- Other:
- Post-Fix Tasks: users pianote-1-month-membership product needs to be expired when this bug is fixed

---
 
- Title: many users reporting getting an error when trying to place an order
- Brand: pianote
- Severity: high
- Preconditions: users emails who reported to us: caleb@drumeo.com, curtis@drumeo.com
- Reproduction: user clicks submit button and see an error screen saying '500 Something when wrong'
- Other: the first report came in on 1pm saturday the 16th
- Post-Fix Tasks: 

--- 

- Title: a user cannot play any videos, they see a message such as 'This video cannot load'
- Brand: drumeo
- Severity: low
- Preconditions: users email: caleb@drumeo.com, browser: safari, device: ipad 10
- Reproduction: when the user loads any lesson page the video player is black and says 'Video cannot be loaded'
- Other:
- Post-Fix Tasks: notify user caleb@drumeo.com over email when the problem is fixed
