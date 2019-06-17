# Scrum & YouTrack Overview


## Projects

Projects are generally split in to 2 categories: 'PM' (brand/project management) projects, and 'DEV' (developer) projects.

- **DEV** projects represent a PHP package which can be installed with composer, such as 'railcontent'. These projects are powered by a kanban style board, which does not have sprints but is instead powered by versioning.
- **PM** projects represent a brand specific application, such as Drumeo. These projects have sprints and follow the normal scrum principles.
- **PMZ** specialized boards for brand specific applications.


## Notes:

_YouTrack refers to 'stories' and 'issues', they are the same thing. 'issue' is a general term which could represent a feature, bug, task, etc._

_At any point during this workflow issues can be moved back to the 'Rejected' column if they requires changes or fixes. They can also be moved back to 'Submitted To QA' if they require further testing._


<br> 

## Web Projects (PM)

### Columns:

- To Do
- Rejected
- In Development
- Submitted To QA
- Ready For Staging
- On Staging
- Ready For Production
- On Production
- Complete

### Steps

1. **Todo: Issue is created.**  
Or the issue is moved from the project backlog to the this column for a given sprint. Developers or appropriate team members are set as the issues assignees. Reviewer is set to whoever should review the issues once its in 'On Production' (is not required to be set).

1. **Rejected: Issue has bugs or is not fully complete, or more work is required.**  
A developer needs to review and do more work on the issue.

1. **In Development: Developer starts working on the issue.**  
Assignees should be set to whoever starts working on the issue.

1. **Submitted To QA: Issue is ready to be tested by the QA team.**  
This column means the issue is ready for manual or automated testing by the QA team. This column can be skipped if the QA team does not need to look at the issue.

1. **Ready For Staging: QA does not find any issues locally and the issue is ready to be deployed to staging.**  

1. **On Staging: Issues from 'Ready For Staging' are deployed to staging and may need further QA testing.**  
Issues that are built up in 'Ready For Staging' are deployed to our staging server. At this point issues can be sent off for review from project management or others involved in the project, such as support, content managers, or 'upper' management. QA may also test at this stage.

1. **Ready For Production: QA/other determines after testing that the issue is ready to be deployed to users.**  

1. **On Production: Issues from 'Ready For Production' have been deployed to users and may need production testing.**  
Once the project/update is complete and all necessary issues are in the 'Ready For Production' column, it is deployed to production by the developers, or a new app version is built and sent to users. QA may further test these issues on production.

1. **Complete: Issue is complete and bug free.**  
When they are confirmed to be working properly in production or on real devices with the app downloaded from the app store it can be moved to complete.


<br> 

## Mobile App Projects (PM)

### Columns:

- To Do
- Rejected
- In Development
- Submitted To QA
- Ready For Production
- On Production
- Complete

### Steps

1. **Todo: Issue is created.**  
Or the issue is moved from the project backlog to the this column for a given sprint. Developers or appropriate team members are set as the issues assignees. Reviewer is set to whoever should review the issues once its in 'On Production' (is not required to be set).

1. **Rejected: Issue has bugs or is not fully complete, or more work is required.**  
A developer needs to review and do more work on the issue.

1. **In Development: Developer starts working on the issue.**  
Assignees should be set to whoever starts working on the issue.

1. **Submitted To QA: Issue is ready to be tested by the QA team.**  
This column means the issue is ready for manual or automated testing by the QA team. This column can be skipped if the QA team does not need to look at the issue.

1. **Ready For Production: QA determines after testing that the issue is ready to be deployed to users.**  
If the issue is not fully complete or it has bugs/problems, it should be moved to the 'Rejected' column, to be reviewed by the developers.

1. **On Production: Issues from 'Ready For Production' have been deployed to users and may need production testing.**  
Once the project/update is complete and all necessary issues are in the 'Ready For Production' column, it is deployed to production by the developers, or a new app version is built and sent to users. QA may further test these issues on production.

1. **Complete: Issue is complete and bug free.**  
When they are confirmed to be working properly in production or on real devices with the app downloaded from the app store it can be moved to complete.


<br> 

## Special Boards (PMZ)

### Current Boards

- **PMZ - Bug Reports**
    - For bugs that go through our support team [See Outline](https://github.com/railroadmedia/docusora/blob/master/docs/project-management/bug-reporting-guide-and-examples.md)
    - Must have Type = Bug
    - Must have attribute Backlogged = true
- **PMZ - Task Requests** (previously known as PM - Backlog)
    - Misc features/tasks that are not scheduled as part of another projects sprints
    - This is basically our old normal backlog but without bugs, since they were moved to the bug board
    - Must have Type != Bug
    - Must have attribute Backlogged = true 

### Columns: (can sometimes differ)

- To Do
- Rejected
- In Development
- Submitted To QA
- Ready For Staging
- On Staging
- Ready For Production
- On Production
- Complete

### Steps

Same as PM boards.


<br> 

## PHP Backend Projects (DEV)

### Columns:

- To Do
- In Development
- Ready For Production
- Complete

### Steps

1. **Todo: Issue is created.**  
The appropriate developer is set as the assignee.

1. **In Development: Developer starts working on the issue.**  

1. **Ready For Production: Issue is live under a new package tag.**  
Which means the issue is ready to have its code pushed under a new package tag version.

1. **Complete: Issue is complete and bug free, and it live in an application.**  