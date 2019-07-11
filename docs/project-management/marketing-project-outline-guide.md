# Outlining Marketing Projects For Development

## Define Scope

Describe the general scope of the project in a few sentences. Examples of questions to answer in the scope description:
 
- Which system/brand is this project for?
- Would you consider this project an update to an existing system, or the creation of a brand new system?
- Will there be back and forth time with regards to front-end and back-end development? Once the back-end work is done, will front-end need to do more work based on the changes made by back-end? Or will the project be ready to deploy as soon as backend is done their work?
- Does this update also include bug fixes for existing systems/features?

## Share Designs

Designs files are by far the most important part of any web project planning phase. Please share them with the developers as soon as possible if any changes are being made which require new design. Dev will not be able to provide an estimate without design files when they are required for a project.

## Outline The Sub-Parts or 'Stories'

We call the sub-parts of a project stories. Each outlined story should follow these 3 requirements:

- **Title**
    - A short sentence describing the end goal of the story
    - Ex: Create home page section under the top banner with the 3 latest blog posts content
    - Ex: Modify search functionality so users can also search by artist or author
    - Ex: Admins need to be able to set the top banner featured posts manually with the post ID
- **Type**
    - One of the following options: 'feature', 'task', 'bug'
    - Feature: a new feature or section/part to be added, usually user or admin facing
    - Task: a non-user facing change, such as 'change database row X to Y', or 'setup redirect from X to Y url'
    - Bug: fixing something wrong with existing systems or features
- **Description**
    - Not always needed but if you need to add more details or add pictures/screenshots they should go here
    - Please try and link the related design file in the description, it saves us a ton of time
- **Current Functionality**
    - If the story is an update to an existing feature, please outline how it is currently working so we can more accurately gauge how complex the update is
    - If you are not sure how the current feature works that it totally fine, just let us know that you are unsure
    - Ex: Currently the search only accounts for post titles and descriptions
    - Ex: Currently the main banner pulls the first latest post from each category
- **Requires BE/FE Collaboration**
    - Many times a specific story will require back and forth between the BE and FE devs. FE will make some additions, then BE will add some things, then FE can finish once the BE is done
    - Please describe what will need to be done on the FE side once the BE work is complete, so we can make sure the data is well mapped and ready to be used on the FE

## The Project Is Ready For Development

Present the outline to the BE team. If the outline follows this guide we should be able to easily and accurately give estimates for how long a project will take!