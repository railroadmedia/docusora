# Scrum & YouTrack Overview

## Projects

Projects are generally split in to 2 categories: 'PM' (brand/project management) projects, and 'DEV' (developer) projects.

- **DEV** projects represent a PHP package which can be installed with composer, such as 'railcontent'. These projects are powered by a kanban style board, which does not have sprints but is instead powered by versioning.
- **PM** projects represent a brand specific application, such as Drumeo. These projects have sprints and follow the normal scrum principles.

## PM Project YouTrack Workflow

_Note: YouTrack refers to 'stories' and 'issues', they are the same thing. An issue can be a feature, bug, or task._

1. **Issue is created in the 'To Do' column.**   
Or the issue is moved from the project backlog to the 'To Do' column for a given sprint.  

1. **The developer moves the issue to the 'In Development' column and begin working on it.**  

1. **The developer moves the issue to the 'Submitted To QA' column.**  
Once the issue is ready for manual or automated browser testing.

1. **QA tests the issue and if its ready, moves the issue to the 'Ready For Staging' column.**  
If the issue is not fully complete or it has bugs/problems, it should be moved to the 'Rejected' column, to be reviewed by the developers.

1. **A developer or QA deploys all 'Ready For Staging' issues to staging and moves the issues to the 'On Staging' column.**  
Once issues are built up in 'Ready For Staging' and ready to be deployed to our staging server. At this point issues can be sent off for review from project management or others involved in the project, such as support, content managers, or 'upper' management.

1. **Issues are tested again by QA on staging, then QA moves the issues to 'Ready For Production'.**  
Once they are confirmed to be working and outside review is complete, 

1. **The issues are all moved to the 'On Production' column by the developers in charge of deployment.**  
Once the project/update is complete and all necessary issues are in the 'Ready For Production' column, it is deployed to production by the developers.

1. **Issues under a final testing stage on production by QA, then QA moves them to the 'Complete' column.**  
When they are confirmed to be working properly, 

Note: At any point during the workflow issues can be moved back to the 'Rejected' column if they requires changes or fixes. They can also be moved back to 'Submitted To QA' if they require further testing.

## DEV Project YouTrack Workflow

1. **Issue is created in the 'To Do' column for the specified version.**  
Or the issue is moved from the project backlog to the 'To Do' column for a given sprint.

1. **A Developer moves the issue to the 'In Development' column and begin working on it.**  

1. **Once the issue is complete, the developer moves the issue the 'Ready For Production' column,**  
Which means the issue is ready to have its code pushed under a new package tag version.

1. **the developer moves all that versions issues to the 'complete' column.**  
 Once the new package version is implemented and tested successfully in an application,