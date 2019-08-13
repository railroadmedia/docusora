# Scrum & YouTrack Overview


## Projects

Projects are generally split in to 3 categories: 'WEB' projects, 'MOBILE' projects, and 'DEV' projects.

- **WEB** projects represent a brand specific website, such as Drumeo. These projects have sprints and follow normal scrum principles.
- **DEV** projects represent a PHP or NPM package which can be installed with composer or npm, such as 'railcontent' or 'vuesora'. These projects are powered by a kanban style board, which does not have sprints but is instead organised by versioning.
- **MOBILE** projects represent a mobile android/ios application. These projects have sprints and follow the normal scrum principles.

<br> 

- **PMZ** specialized boards.

## Notes:

_YouTrack refers to 'stories' and 'issues', they are the same thing. 'issue' is a general term which could represent a feature, bug, task, etc._

_At any point during this workflow issues can be moved back to the 'Rejected' column if they requires changes or fixes._


<br> 

## Web Projects (WEB)

### Columns:

- To Do
- Rejected
- In Development
- Ready For Staging | Awaiting Review
- On Staging | Needs QA 
- Ready For Prod | Built
- On Prod | Deployed To Users
- Complete

### Steps

1. **To Do: Issue is created.**  
Or the issue is moved from the project backlog to the this column for a given sprint. Developers or appropriate team members are set as the issues assignees. Reviewer is set to whoever should review the issues once its in 'On Prod' (is not required to be set).

1. **Rejected: Issue has bugs or is not fully complete, or more work is required.**  
A developer needs to review and do more work on the issue.

1. **In Development: Developer starts working on the issue.**  
Assignees should be set to whoever starts working on the issue.

1. **Ready For Staging | Awaiting Review: Issue is ready to be deployed to staging by a developer.**
Generally multiple issues are all deployed to staging at the same time. QA should not be reviewing issues in this state.

1. **On Staging | Needs QA: Issue is ready to be tested by the QA team.**  
This column means the issue is ready for manual or automated testing by the QA team. This column can be skipped if the QA team does not need to look at the issue. If there are problems with the issue it should be moved to 'Rejected' so a developer can review it.

1. **Ready For Prod | Built: QA/other determines after testing that the issue is ready to be deployed to users.**  
Or in the context of mobile app development, the issue has been resolved and put in to a fresh build and is ready to be released to users.

1. **On Prod | Deployed To Users: Issues from 'Ready For Prod | Built' have been deployed to users and may need production testing.**  
Once the project/update is complete and all necessary issues are in the 'Ready For Prod | Built' column, it is deployed to production by the developers, or a new app version is built and sent to users. QA may further test these issues on production. If there are problems with the issue it should be moved to 'Rejected' so a developer can review it.

1. **Complete: Issue is complete and bug free.**  
When they are confirmed to be working properly in production or on real devices with the app downloaded from the app store it can be moved to complete.

<br> 


## Mobile App Projects (MOBILE)

### Columns:

- To Do
- Rejected
- In Development
- Is Built & Needs QA
- Ready For Release To Users
- Deployed To Users
- Complete

### Steps

1. **To Do: Issue is created.**  
Or the issue is moved from the project backlog to the this column for a given sprint. Developers or appropriate team members are set as the issues assignees. Reviewer is set to whoever should review the issues once its in 'On Production' (is not required to be set).

1. **Rejected: Issue has bugs or is not fully complete, or more work is required.**  
A developer needs to review and do more work on the issue.

1. **In Development: Developer starts working on the issue.**  
Assignees should be set to whoever starts working on the issue.

1. **Is Built & Needs QA: The issue is developed, is included in a new build, and is ready for QA.**

1. **Ready For Release To Users: The issue has been tested by QA and is ready to be released to users.**  

1. **Deployed To Users: The issue has been released to users via an app store or via a beta program.**  
QA may further test these issues using the live build. If there are problems with the issue it should be moved to 'Rejected' so a developer can review it. If there are no problems or the issue does not require live/production testing then it should be moved to complete.

1. **Complete: Issue is complete and bug free.**  
Issue is confirmed to be working properly on real devices with the app release downloaded from the public app store.

<br> 


## Special Boards (PMZ)

### Current Boards

- **PMZ - Bug Reports**
    - For bugs that go through our support team: [see outline](https://github.com/railroadmedia/docusora/blob/master/docs/project-management/bug-reporting-guide-and-examples.md)
    - Must have attribute Type = Bug
    - Must have attribute Backlogged = true
- **PMZ - Task Requests** (previously known as PM - Backlog)
    - Misc features/tasks that are not scheduled as part of another project sprint
    - This is basically our old normal backlog but without bugs, since they are moved to the bug board
    - Must have attribute Type != Bug
    - Must have attribute Backlogged = true 

### Columns: (may sometimes differ)

- To Do
- Rejected
- In Development
- Ready For Staging | Awaiting Review
- On Staging | Needs QA 
- Ready For Prod | Built
- On Prod | Deployed To Users
- Complete

### Steps

Same as PM boards.


<br> 

## PHP Backend Projects (DEV)

### Columns:

- To Do
- In Development
- Ready For Prod | Built
- Complete

### Steps

1. **To Do: Issue is created.**  
The appropriate developer is set as the assignee.

1. **In Development: Developer starts working on the issue.**  

1. **Ready For Prod | Built: QA/other determines after testing that the issue is ready to be deployed to users.**  
Which means the issue is ready to have its code pushed under a new package tag version.

1. **Complete: Issue is complete and bug free, and it live in an application.**  

<br> 

## WEB Example

> Developer/QA create a story _"As a user Courses will have a blue theme color"_. They then leave 
> the story in the `To Do` column.

↓

> Developer moves the story into the `In Development` column and begins work on it

↓

> Developer finishes the work on the story and moves to card into the `Awaiting Review` column

↓

> When the Developer is ready they deploy the fix to staging, and move the card into the 
> `On Staging` column

↓

> QA goes to test the work on staging and determines the bug/issue was not properly addressed. They 
> then move the card into the `Rejected` column.

↓

> Developer moves the card out of the `Rejected` column and back into the `In Development` column. 
> Earlier steps are then repeated until deployed to staging again.

↓

> QA determines the bug/issue was properly addressed and moves the card into the `Ready for Prod` column.

↓

> Whenever the developer or development team is ready they can now ship the work and move the card into the 
> `On Production` column.

↓

> QA confirms at a later date whether the work was properly shipped to production and lastly moves the card into the 
> `Complete` column.

<br> 

**Note:** It is very important that cards are in the proper columns for their current state. If work is pushed 
to staging, but the card is not moved into the `On Staging` column, QA should NOT test the feature. Inversely, 
if a feature is broken, and not properly moved into the `Rejected` column, the developer does NOT know that they 
need to fix it. 

This stops work from being done multiple times on the same issue, reduces detective work needed
to track down tasks. And hold's everyone accountable for their own contribution to the project.

Developers shouldn't have to touch stories in the `On Staging`, `On Prod`, or `Complete` columns.

QA shouldn't have to touch stories in the `In Development`, `Awaiting Review` columns.