# Bug Fixing Workflow

## Step By Step

1. **Bug is reported in the "B - Bug Reports" project in YouTrack, following the "Bug Reporting Guide and Examples" documentation. The initial report will be categorized under "Initial Report".**
<br>
<br>

2. **QA will review the report promptly, whereupon valid reports will be reclassified into the "Accepted" column.**
    - Reports that are lacking sufficient information will have a comment appended to it requesting more information from the appropriate parties, and will not be accepted until all required information is present.
    - Reported issues that are not bugs, are duplicates of existing reports, non-replicable or remain missing crucial information after further prompts for it will be marked as "Rejected/Unreplicable" and closed. In the event that a report in this classification need to be re-opened, it can be dragged back into the "Initial Report" column. Rejection and closure can occur at any point along the process and will be accompanied with an explanation as to why. 
    - The priority of a bug report determines how quickly a report passes through this initial review. Reports marked as high priority are typically reviewed same day, whereas medium and low priority may take as long as 3 to 5 business days respectively.
<br>
<br>

3. **QA starts in-depth investigation into the issue, moving the report into the "Reproduction/Investigation" state.** 
    - This step often raises additional questions regarding the parameters surrounding the bug, either for the initial reporter or occasionally a developer. The parties in question will be tagged in the comments here.
    - Should this step not be required, it may be skipped and the report continues onto the next step immediately. 
<br>
<br>

4. **The bug report and all investigation findings are assigned to the appropriate department for development, and moved into the "Pending Fix" state.**
   - Department leads will add these tasks to their sprints and assign a developer.
<br>
<br>

5. **Development work begins on the issue, and the report moves into the "In Development" state.**
   - Should further QA testing be required prior to deployment, tasks will stay in this state until the testing is completed.
   <br>
   <br>

6. **Bug fix is deployed, report is marked as "Deployed/Completed" and closed.**
   - Any post-fix tasks can be performed at this point.
