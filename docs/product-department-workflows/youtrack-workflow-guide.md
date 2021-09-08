# YouTrack Setup Basics

<br>

## What Is YouTrack

_A project management tool that can be adapted to your processes to help you deliver great products. 
Track projects and tasks, use agile boards, plan sprints and releases, keep a knowledge base, work with 
reports and dashboards, create workflows that follow your business processes. Never force your process
to fit the limits of a tool again. Unlike other project management tools, YouTrack can be customized to your needs!_

<br>

## General YT Basics

YouTrack's most basic element is an **issue**. An issue can be thought of as a task, user story, issue, bug, etc.

YouTrack also has **projects**. Projects contain issues and generally represent a specific project.

**Hierarchy: projects -> issues**

<br>

YouTrack also has **boards**. A board is a tabular way to visualise issues using rows and columns. Typically, 
the column name is the state of an issue such as 'to do', 'in progress', 'completed'. Issues can easily be moved between
rows and columns by clicking and dragging. This can be used to change the issue state or any other field/data.
Often times, the row names are the priority or project name. Rows and columns can be configured to any field or value. 
A board can be used for multiple projects.

Boards contain **sprints** (if configured). A sprint is a way to encapsulate a set of issues that are relevant to 
a specific time period. Typically, if a team runs on a 2-week sprint cycle, they would choose which issues to tackle in
the upcoming 2 weeks, then complete those issues. After 2 weeks, any issues that were not completed would get moved
in to the following 2-week sprint. This makes it easy for team members to know what they should be working on, and 
it makes it easy to see what was completed in previous sprints.

**Hierarchy: boards -> sprints**

<br>

In summary, projects and issues represent work that needs to be done. Boards and sprints are for
managing which work should be done when, and what state the work is in.

## Musora's YT Setup

### 'A - Projects' Project & Board

This project and relevant board holds issues which represent entire projects. Project managers and product directors will
manage these boards.

Each issue (which represents an entire project) has the following fields:

**Priority:**
- High: projects that we are currently working on or will move on to next
- Medium: projects that are prime candidates to become high priority in the near future
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

Board link:
**[https://musoraproduct.myjetbrains.com/youtrack/agiles/121-11/122-18?tab=general](https://musoraproduct.myjetbrains.com/youtrack/agiles/121-11/122-18?tab=general)**