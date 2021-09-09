# YouTrack Setup Basics

<br>

## What Is YouTrack

_A project management tool that can be adapted to your processes to help you deliver great products. 
Track projects and tasks, use agile boards, plan sprints and releases, keep a knowledge base, work with 
reports and dashboards, create workflows that follow your business processes. Never force your process
to fit the limits of a tool again. Unlike other project management tools, YouTrack can be customized to your needs!_

<br>

## General YT Basics

YouTrack's most basic element is an **issue**. An issue can be thought of as a task, user story, issue, bug, 
(or sometimes an entire project), etc.

YouTrack also has **projects**. Projects contain issues and generally represent a specific project.

**Hierarchy: projects -> issues**

<br>

YouTrack also has **boards**. A board is a tabular way to visualise issues using rows and columns. Typically, 
the column names are the state of an issue such as 'to do', 'in progress', 'completed'. Issues can easily be moved between
rows and columns by clicking and dragging. This can be used to change the issues state or any other field/data.
Often times, the row names are the issues priority or project name. Rows and columns can be configured to be any 
field or value. A board can be used for multiple projects.

Boards contain **sprints** (if configured). A sprint is a way to encapsulate a set of issues that are relevant to 
a specific time period. Typically, if a team runs on a 2-week sprint cycle, they would choose which issues to tackle in
the upcoming 2 weeks, then complete those issues. After 2 weeks, any issues that were not completed would get moved
in to the following 2-week sprint. This makes it easy for team members to know what they should be working on, and 
it makes it easy to see what was completed in previous sprints.

**Hierarchy: boards -> sprints**

<br>

In summary, projects and issues represent work that needs to be done. Boards and sprints are for
managing which work should be done when, and what state the work is in.

<br>


## Musora's YT Setup - 'Projects' Project & Board

This project and relevant board holds issues which represent entire projects. Project managers and product directors will
manage these boards. The issues (which represent entire projects) contain information, links, and documentation 
about the projects. Any issue that is in progress or to be start soon will have a proper associated YouTrack project. 
The project should be linked in the description of the issue which represents it on this board.

Each issue has the following fields:

**Project Priority:**
- High: projects that are in progress or will be started next
- Medium: projects that are candidates to become high priority in the near future
- Low: projects that may become medium or high priority in the far future

**Project State:**
- Ideation: the project is still an idea that is being formed
- Project Planning: the project is a fully formed idea and the planning for how and when we can complete it has begun
- In Progress: the project has begun undergoing implementation such as ux design or development
- On Production: the project is live to students and may require follow-up work
- Complete: the project is totally complete and does not require further work from any product team member

**Start Date:**
When the project should be or was started.

**Deploy Date:**
When the project should be deployed to students. This is the deployment deadline for the project.

**Owner:**
The person who owns this project and is responsible for its timeline and outcome.

<br>

This board also has sprints, 1 for each year, which are primarily for organisation purposes.

<br>

**How to add a new project to the board:**
1. Create a new issue in the 'Projects' YouTrack project.
1. Add a relevant title for the project. Please use a version number when possible such as: Student Lists v2.0.
1. Add a description for the project which should include any relevant information, documentation, or links.
1. Set the project priority based on the above priority field options.
1. Set the project state which should most likely be Ideation if the project has not been started.
1. If the project is going to be medium or high priority, set the Start Date and Deploy Date fields. These can be 
   rough estimates if the dates are way out in the future.
1. Choose a project owner. Often times this will be a PM or PD (Randy, Caleb), or a developer.
1. Click create. Once the issue is created, it will automatically be added to the latest years sprint in the 'A - Projects'
   board. If the project should not be in the current years sprint please move it to another years sprint.
1. If this project is to be started soon, and it is ready for project planning, create a new YouTrack project for it. The 
   title of the YouTrack project should be the same as this issue. When creating a new YouTrack project, please use the 
   'Template Project v1.0' template. Tasks, user stories, etc can now be created in this new YouTrack project.
1. Add a link to the YouTrack project inside the representing issues' description.

Board link:
**[https://musoraproduct.myjetbrains.com/youtrack/agiles/121-11/122-18?tab=general](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-11/122-18?tab=general)**


<br>

## Musora's YT Setup - Team Sprint Boards

Each team has a board dedicated to their sprints. Here are their names and links:
- [S - Product Team Sprints](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-3/current)
- [S - UX Design Team Sprints](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-5/current)
- [S - FEW Dev Team Sprints](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-6/current)
- [S - MA Dev Team Sprints](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-7/current)
- [S - BE Dev Team Sprints](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-8/current)
- [S - QA Team Sprints](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-9/current)

Each team will use a 2-week sprint cycle (I am very open to flexibility on that however). The board rows
represent the project in which the issues exist. Generally, the 'in progress' and 'upcoming' projects should be kept at the
top of the board. You can move the rows/projects up and down by clicking and dragging the 3 dots in the right left of 
the row.

Each board has its own columns that are specific to each team. The columns represent the state of the work for issues.
The states are as follows:

**S - Product Team Sprints**
- Backlogged
- To Do
- Planning & Documentation
- Pass-Off
- Complete

**S - UX Design Team Sprints**
- Blocked
- Backlogged
- To Do
- Low Fidelity Design
- High Fidelity Design
- Complete

**S - FEW Dev Team Sprints**
- Blocked
- Backlogged
- To Do
- In Progress
- Complete

**S - MA Dev Team Sprints**
- Blocked
- Backlogged
- To Do
- In Progress
- Complete

**S - BE Dev Team Sprints**
- Blocked
- Backlogged
- To Do
- In Progress
- Complete

**S - QA Team Sprints**
- Blocked
- Backlogged
- To Do
- In Progress
- Complete

### States Explained
**Backlogged**
This means the issues is ready to be worked on by the relevant team, but it has not yet been added to a sprint.
Teams will take issues from their queue of backlogged issues and move them to their current or next sprint. 

**Blocked**
This means that the issue requires work from another team before the relevant team can start working on it. Once the 
required work is complete by the required team, the issue will automatically move from 'Blocked' to 'Backlogged' or
'To Do'. Blocked issues can still be moved in to a sprint if its likely they will become unblocked during the sprint.

The blocked requirements work like this:
'UX Design State' is blocked until 'Product State' is complete.
'FEW Dev State' is blocked until 'UX Design State' is complete.
'MA Dev State' is blocked until 'UX Design State' is complete.
'BE Dev State' is blocked until 'UX Design State' is complete.
'QA' is blocked until all previous states are complete.

Workflow Chart:
![Workflow Chart](../images/product-division-project-tasks-workflow-sept-2021.jpg)