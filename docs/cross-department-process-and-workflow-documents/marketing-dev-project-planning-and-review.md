# Overview

All marketing dev projects are created inside 
the musora Asana team [Marketing-Dev](https://app.Asana.com/0/1199995198037877/overview).
The developers, creative team members, and markers associated with the project 
should use the same project in Asana. A new Asana project should be created if the project
will take more than a few hours to complete or if the project requires the full workflow 
of design, development, QA, review, deployment. The Asana project is created using the 
[X - Project Template 2021](https://app.asana.com/0/1199995198037881/list) template.
The asana project should always be added to the 
[Dev-Marketing Asana Portfolio](https://app.asana.com/0/portfolio/1200330095730280/list) once its created.

Anyone can get an overview of all ongoing and scheduled projects and see their priority
in the [Dev-Marketing Asana Portfolio](https://app.asana.com/0/portfolio/1200330095730280/list). Checkout the 'List'
 and 'Timeline' tabs.

# Project Stages By Department

1. **Ideation, Planning, Docs & Links** - (marketing, creative, dev)
1. **Design/Creative** - (creative)
1. **Front-End Development** - (dev)
1. **Back-End Development** - (dev)
1. **QA Testing** - (qa, dev)
1. **Review** - (marketing, creative)
1. **Launch, Monitoring, Review** - (dev, marketing)

# Asana Setup & Guide

## Important Notes About Asana & Dependencies
You need a basic understanding of how dependencies work in Asana to use 
this workflow properly. If you are unfamiliar please read about how they work here: 
[https://asana.com/guide/help/tasks/dependencies](https://asana.com/guide/help/tasks/dependencies).  
  
**Dependencies TLDR:**   
When a task is dependent on another task it is marked as 'blocked' 
until that other task is completed. This feature is useful for passing work between team members
and departments. For example, once the milestone '_Finish marketing project planning_' is completed,
the '_Finish the designs & creative assets_' task is set as ready to be started and the creative team is 
notified to begin work on the design. In the same manner once the '_Finish the designs & creative assets_' task
is completed, the '_Finish coding the front end_' task is marked as ready to be started, and the dev
is notified they can begin coding.

**Milestones**  
Milestones are a critical part of the workflow and should not be deleted. 
If an entire section or milestone is unnecessary, those tasks should be marked complete rather than
be deleted. A milestone represents the state of an entire
part of the workflow. For example if the '_Finish designs & assets, get approval from project owners_' milestone is
not yet completed that means the project is still in the design phase and not ready for the devs to start coding. 
Once that milestone is completed, the latter dev tasks will be automatically unblocked and assigned.  
  
The purpose of milestones is to easily track the state of a project and pass the project between team members 
and departments seamlessly and with notifications. Milestones are linked together as dependencies. Feel free to 
modify the milestones or change their dependencies if you wish however there should be a good reason to do so.

<br>

## Our Default Milestones & Dependency Graph

_Each milestone is dependent on the previous one in the list._    

1. **Finish marketing project planning**  
To be assigned to and completed by project owning marketer.
     
1. **Finish designs & assets, get approval from project owners**  
To be assigned to and completed by the assigned creative team member.

1. **Finish coding the front end**  
To be assigned to and completed by the relevant FE developer.

1. **Finish coding the back end**  
To be assigned to and completed by the relevant BE developer.
   
1. **Finish QA testing**  
To be assigned to and completed by the relevant developer OR QA team member.
   
1. **Finish review by marketing/creative team, get approval for final launch from project owners**  
To be assigned to and completed by project owning marketer and involved creative team members.

1. **Launch this project to students, notify marketing and creative teams (using slack)**  
To be assigned to and completed by the relevant project owning developer.
   
1. **Project is totally complete and can be archived in Asana**  
To be assigned to and completed by the relevant project owning marketer or the relevant developer. Once this milestone 
is complete the project should be archived in Asana.

<br>

## Is it a project or a small update?  

### It's a small update that will take less than a few hours and doesn't require the full workflow:
- Check if there is an existing Asana project for wherever you would like to make the update.
  If so, please create a new task in the 'Post Launch Tasks, Monitoring, Review' section.
- Otherwise, if there is no existing project, please create a new task in the Asana project named 
'Misc Tasks'.
  
The most important question to ask when determining whether you need a full project or just a misc task is: 
**Does this require work and coordination from multiple departments?** If so, you should likely use a project.  

For example: 'Trent can you please update the top banner on this page to say X instead of Y' is a misc task because
it doesn't need any design work. Some tasks which only require a small amount of design work may still only warrant
a misc task.

'We need a new design and new pages for our trial offers.' This should be a project since it will require design,
design review, coding, qa, etc.

When in doubt, create a misc task with the details of your project and post in the
dev-marketing-creative channel, and we'll figure it out together.
  
<br>  

### It's a full project that needs the entire workflow:  

1. Create a new Asana project in the 'Dev-Marketing' team using the 'X - Project Template 2021' 
   template. Please use the project name format: 'PROJECT NAME - BRAND'.
   Please segment projects from the top level per brand. For example if every brand needs a 'April Promo Updates' 
   project, please make 1 project for each brand assuming the updates are large enough to justify a project
   
2. Choose a start and end date for the project. Typically, we operate on a monthly schedule so 
if the project is for a promotion that needs to launch July 1st, the start date can be June 1st, 
   and the end date July 1st. Please review the Asana portfolio timeline and project priority list when choosing a
   timeline. We will tackle priority issues and questions in our monthly dev-marketing meetings or in slack.

![Dev-Marketing Asana Portfolio](https://app.asana.com/0/portfolio/1200330095730280/timeline)

3. Please choose the relevant color for the brand and set it accordingly for the project.

![Brand Asana Colors](../images/brand-asana-colors.jpg)

2. If you are not already familiar, review the top guide task for your department 
   'How to use this project template & plan projects - **marketers** - DELETE ME' or 
   'How to use this project template - **devs** - DELETE ME'
   
4. Place all planning documentation, outlines, assets, etc inside the
   'Project overview, documents, design assets, etc - go here' task description.
   
5. Assign all the milestones that are relevant to your department. For example the 
   '_Finish marketing project planning_' task should be assigned to the marketer who owns the project. Generally,
   dev tasks should be assigned to Trent H. Design tasks should be assigned to Jord D. If you are not sure who to 
   assign leave the task unassigned. Please also assign multiple collaborators if necessary. For example the 
   '_Finish review by marketing/creative team, this project is approved for final launch_' task may often have multiple marketers
   set as collaborators if they would like to also review the project before launch.
   
6. Choose a final deadline when this project must be completed and live on production. Enter the Due Date for 
  'Launch this project to production' task inside the 'Launch' section. Please also enter this as the project due 
  date. You can do this when you create the project or by clicking the arrow to the right of the project name and 
  'Edit project details'. Setting the date for the project will make it show up in the overall team calendar
   view here: [Asana Dev-Marketing Team Calendar](https://app.asana.com/0/1199995198037877/calendar)
   The dev team will let you know if the deadline is possible. The dev team will set the review dates.
   
7. If the marketers project planning is complete and ready for design or dev, complete the 
   'Finish marketing project planning' task. 
   This task is set up as a dependency which means that other tasks 
   related to design and development will not be triggered to be ready to be started 
   until this planning task is marked complete.
   
8. Notify the dev and creative team about the project and that it's been set up using slack.

...

9. Once the design and development is complete, the project will be put on a testing, staging, or hidden production
url for review. A dev will notify the marketing & creative team via the slack channel **'devc-marketing-creative'** that the project is ready for review. An Asana task
   will also automatically be un-blocked.
   
10. Put your feedback and changes under the 'Review' section near the task called '_Review feedback goes here_'

11. Once the review is complete, and the project has been given approval for launch 
    by the project owners and the marketing team, complete the 
   '_Finish review by marketing/creative team, this project is approved for final launch_' task so the developers know when to launch
   the project. This task must be completed by the project owner, not a developer. Please also set a date for the '_Launch this project to production_' task if the project is not already
   live on production. The dev team will launch the project at the specified date and notify the marketing team right 
   after its live.
   
...

12. After the project is completely launched, please put all future feedback, change requests, 
   promo closures and updates, etc, in the '_Post Launch Tasks, Monitoring, Review_' section and assign to Trent.
