# Quick Links

Bug Reporting Project: [https://musoraproduct.myjetbrains.com/youtrack/agiles/121-12/current](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-12/current)  
Bug Reporting Form: [https://musoraproduct.myjetbrains.com/youtrack/newIssue?project=BR](https://musoraproduct.myjetbrains.com/youtrack/newIssue?project=BR)

# Bug Reporting Guide

## Who, Where, and What To Do

- **If the priority is HIGH:**
    - Contact Caleb or another available developer immediately over Slack/email, or in person
    
    - Create a new issue using the Bug Reporting Form following the template below. Under the "Priority" field, select "High".

    - Feel free to post the newly created issue in the pr-bugs channel, and include a link to the issue.
<br>

- **If the priority is MEDIUM or LOW:**
    - Create a new issue using the Bug Reporting Form following the template below. Under the "Priority" field, select "Medium" or "Low".
    - Try to avoid reaching out to or discussing with a developer in person if the issue severity is not high. If an issue needs to be discussed in person or it would be much more efficient to chat in person please schedule a meeting time to do so where both parties agree on the date/time. If the dev team specifically requests you reach out to them directly for a given project or launch, definitely reach out directly anytime you see fit.
    
    - Feel free to reach out to Jon C (QA) about a bug/problem anytime over Slack or in person! He is in charge of handling how bugs are managed between support and dev and would love to chat or help you through an issue.
    <br>

- **Escalating bugs:**
    - At any pont as further information comes in, an Issue reported as Low or Medium priority can be escalated to Medium or High priority as needed.
    <br>
    
## What Priority Do I Choose?

- **High Priority**
  - High priority issues are one where core functionality is blocked for many users, and there is no feasible workaround.
  
  - It could include issues where customers cannot check out via the shopping cart, or one brand's home page is blank and won't load any data.
  
  - Also applies to internal tools, like if Musoracenter won't retrieve any user data when performing a search.
   
  <br>

- **Medium Priority**
    - If a feature or functionality is broken, but it's not a critical part of our product as a whole

    - A broken notifications page, an app crashing on a specific content type on some devices, editing profile pictures won't work, certain types of payment data missing from Musoracenter, etc.

    - Can also apply to issues that would typically be considered high priority, but are affecting a smaller number of users
  
    - Large visual irregularities that don't obstruct usage, but are very jarring and distracting

   <br>
  
- **Low Priority**
    - Basically everything that isn't high or medium priority.
    - Includes issues with QoL features such as video timestamps, emoji support in comments, "My List" filtering, etc.
    - Issues that would generally be higher priority, but are affecting a very small subset of users
    - Visual issues like incorrect padding at specific viewports, typos or grammar mistakes in copy, "Live" logo breaks into 2 sections in the header, etc.
    - Also includes issues that only occur in rather obscure situations, such as with non-regular browsers, access on Smart TV's, etc.
## Bug Report Template
1. **Summary:**
    - This is a basic description of the issue at hand, usually 1 or 2 sentences.
    - Ex: Users experience a 500 error when attempting to submit a new user avatar when uploading from the app
    - Ex: 500 songs course has an incorrect lesson count in the summary
    - Do your best to ensure that the summary can can clearly identify the issue to avoid duplicates and confusion.
    
   <br>

2. **Body text:**
    - This field is where the majority of the information about an issue will go
    - The following should be provided here:
      - Detailed description of the issue
      - User/s affected by the issue. This includes Musora ID's and Emails, but also any other potentially relevant identifiers, such as "All users with Pianote monthly subscription purchased in the last 2 weeks"
      - Platforms affected by the issue (iOS Safari 12 or older, Desktop Mozilla Firefox v91.1.1 browsers, All android devices running the Pianote app, Mobile Google Chrome on both iOS and Android, etc. )
      - Troubleshooting steps already taken, and the results of these steps
      - How the issue occurred (eg. user reports that app crashes after first downloading a lesson, disconnecting from mobile data, and attempting to resume the watching of a lesson)
      - Reproduction. Were you or anyone else able to reproduce the issue? What steps were taken? What was the result of your testing? 
      - All media depicting the issue from the user, or captured during reproduction can be pasted here. Screenshots, videos, etc. Media can also be dragged into the UI as standalone files, or as a part of comments.
      - Any post-fix tasks required of development
    - Note that any data not included in the initial report can be posted as a comment inside the issue, and media can be dragged into the input box for uploading.

    <br>

3. **Support Notes:**
    - This field should be used for any information useful soley to the support department, and does not assist in the investigation or fixing of an issue.
    - For example, any users who require follow-up post-fix (re-sent transaction receipts, updates access, etc.) should be stated here.
   
<br>

4. **Priority:HIGH, MEDIUM, LOW (choose one)**
    - See section above "What Priority Should I Choose" to identify the priority of an issue
    - Feel free to reach out to Jonathan C. if you are ever unsure which priority to assign to an issue
    - Issues can be (de)escalated if required
    
   <br>

5. **Brand**
    - Select the affected brand(s) in this dropdown. Please note that the Pianote/Drumeo Apps have their own option here. Multiple brands may be selected at once, but issues that pertain to multiple brands can usually be labelled with the "Musora/Crossbrand" option.

    <br>

6. **Report Count:**
   - If the issue reported seems isolated to a certain subset of users, please indicate the number of people who have encountered it.
   - If issue is obviously widespread and affects everyone, field can be left blank.
   - Please note that this field maxes out at nine hundred ninety-nine million, nine hundred ninety-nine thousand, nine hundred and ninety-nine.
   
   <br>

7. **Platform:**
    - What the customer was using to access out content when the initial issue was encountered, eg: iOS version number, Device make and model, App version, Browser version, Operating System, etc.
    - Depending on the type of bug, this field may be left blank when issue clearly exists across all platforms. 
    - If subsequent users encounter an issue after the initial report, their platform details should be included in the comments when the additional cases are reported.

    <br>

8. **Other Fields**
    - All other fields are for developer use only, and should be left untouched


## Full Examples

- Summary: Getting an error when trying to expire a user's product access
- Priority: Medium
- Brand: Musora/Crossbrand
- Report Count: Blank (all users)
- Description: User has product "pianote-1-month-membership", expiry date cannot be edited. Attempting to change date results in "Error editing user product".
users email: caleb@drumeo.com, user product: pianote-1-month-membership. User product needs top be expired once bug is fixed.


---
 
- Summary: Users receiving "Oops, something went wrong." error when trying to place order through app on Apple devices
- Priority: High
- Brand: Drumeo App
- Report Count: Blank
- Description: A whole bunch of iOS users are just getting an error after confirming their signup through apple's payment confirmation window. caleb@drumeo.com, jonc@drumeo.com, jonc+2@drumeo.com, jonc+3@drumeo.com and others reported not being to sign up. Musora accounts were created with their emails, but there is no payment history or valid subscription. The above users have been manually granted 7 days of access for the time being. Users received no receipt from Apple. Screenshot of error attached below. No reports from Android users of a similar situation.

--- 

- Summary: Legacy video player freezes on older iOS devices
- Priority: Low
- Brand: Musora/Crossbrand
- Report Count: 2
- Description: User jonc+myiPadis13yearsold@drumeo.com claims that all videos will freeze playback at 4:20 in and cannot be started again on their iPad 2, iOS 6.1.5, Safari, using the Legacy player (New player not supported). Refreshing the page does not help, but they can proceed further by scrubbing past that point in the lesson manually. User has tried other browsers with the same result, but also says issue is not present on their iPhone 14XSRMaxPlusSE2. Could not reproduce on my own iPad(Air 2). User is a Pianote subscriber only, but issue likely pertains to all brands.
- Comment: User jonc+myiPadisevenolder has reported a similar issue with their first gen iPad mini (iOS 1.6), reports that they can watch it fine on their Macbook though. They are on Drumeo.

<br>

## So How Do you Report A Bug?

1. Head over to the [Bug Reporting Project board.](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-12/current) Make sure the issue you are looking to report doesn't already exist. If it does, you can add on any additional information you have as a comment and increment the report count. If issue exists in the "Stopped/Unreplicable" column, you can drag the issue back into the "Initial Report" column to revive it. If issue has been resolved recently but has cropped up again, feel free to re-use the task, but if a similar issue has come and gone in the past, it's better to create a new issue instead.
2. Once you are sure that you are not creating a duplicate issue, head over to the [Bug Reporting Form](https://musoraproduct.myjetbrains.com/youtrack/newIssue?project=BR).
3. Fill out the following text fields as directed above, if applicable:
   1. Summary
   2. Description
   3. Support Notes
   
   Then on the right-hand side, select options from the following fields:
   4. Priority
   5. Brand
   6. Enter a number for report count, or leave blank