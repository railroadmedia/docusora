# Overview

All marketing dev projects are created inside 
the musora Asana team [Marketing-Dev](https://app.Asana.com/0/1199995198037877/overview).
The developers, creative team members, and markers associated with the project 
should use the same project in Asana. A new Asana project should be created if the project
will take more than a few hours to complete or if the project requires the full workflow 
of design, development, QA, review, deployment. The Asana project is created using the 
[X - Project Template 2021](https://app.asana.com/0/1199995198037881/list) template.

# Project Stages By Department

1. **Ideation & Planning** - (marketing, creative, dev)
1. **Design/Creative Work** - (creative)
1. **Front-End Development** - (dev)
1. **Back-End Development** - (dev)
1. **QA Testing** - (qa, dev)
1. **Review** - (marketing, creative)
1. **Launch** - (dev)
1. **Post Launch Tasks, Monitoring, Review** - (dev, marketing)

# Asana Setup & Guide

## Important Notes About Asana & Dependencies
You need a basic understanding of how dependencies work in Asana to use 
this workflow properly. If you are unfamiliar please read about how they work here: 
[https://asana.com/guide/help/tasks/dependencies](https://asana.com/guide/help/tasks/dependencies).  
  
**Dependencies TLDR:**   
When a task is dependent on another task it is marked as 'blocked' 
until that other task is completed. This is very useful for passing work along between team members
and departments. For example, once the default task '_Finish marketing project planning_' is completed,
the '_Finish the designs & creative assets_' task is set as ready to be started and the creative team is 
notified to begin work on the design. In the same manner once the '_Finish the designs & creative assets_' task
is completed, the '_Finish coding the front end_' task is marked as ready to be started, and the dev
is notified they can begin coding.

**Default Tasks**  
Default tasks are marked with a gray 'Default Task' priority. These tasks are a critical part of the workflow and should
not be deleted unless an entire section of the workflow is unnecessary. A default task represents the state of an entire
part of the workflow. For example if the '_Finish design review & design feedback cycle_' task is not yet completed 
that means the project is still in the design phase and not ready for the devs to start coding. 
Once that task is completed, the latter dev tasks will be automatically unblocked and be ready to be started.  
  
The purpose of default tasks is to easily track the state of a project and pass the project between team members 
and departments seamlessly and with notifications. Default tasks are linked together as dependencies. Feel free to 
modify the default tasks or change their dependencies if you wish however there should be a good reason to do so.

**Our Default Stories & Dependency Graph:**



## Is it a project or a small update?  

**It's a small update that will take less than a few hours and doesn't require the full workflow:**
- Check if there is an existing Asana project for wherever you would like to make the update.
  If so, please create a new task in the 'Post Launch Tasks, Monitoring, Review' section.
- Otherwise, if there is no existing project, please create a new task in the Asana project named 
'Misc Tasks'.
  
  
**It's a full project that needs the entire workflow:**  

1. Create a new Asana project in the 'Dev-Marketing' team using the 'X - Project Template 2021' 
   template. Please choose the relevant color for the brand
   
1. If you are not already familiar, review the top guide task for your department 
   'How to use this project template & plan projects - **marketers** - DELETE ME' or 
   'How to use this project template - **devs** - DELETE ME'
   
1. Delete the 'DELETE ME' tasks at the top. Do not delete the other default tasks since they are used in the rest of the
workflow.
   
1. Place all planning documentation, outlines, assets, etc inside the
   'Project overview, documents, design assets, etc - go here' task description.
   
1. If the marketers project planning is complete and ready for design or dev, complete the 
   'Finish marketing project planning' task. 
   This task is set up as a blocking task which means that other tasks 
   such as design and development will not be triggered to be ready to be started 
   until this planning task is marked complete.
   
1. Notify the dev and creative team about the project using slack.

...

1. Once the design and development is complete, the project will be put on a testing, staging, or hidden production
url for review. A dev will notify the marketing team via slack that the project is ready for review. An Asana task
   will also automatically be un-blocked.
   
1. Put your feedback and changes under the 'Review' section near the task called '_Review feedback goes here_'

1. Once the review is complete, and the project is ready for launch, complete the 
   '_Finish review by marketing/creative team and get approval for launch_' task so the developers know when to launch
   the project. Please also set a date for the '_Launch this project to production_' task if the project is not already
   live on production. The dev team will launch the project at the specified date.
   
...

1. After the project is completely launched, please put all future feedback, change requests, 
   promo closuers and updates, etc, in the '_Post Launch Tasks, Monitoring, Review_' section and assign to Trent.