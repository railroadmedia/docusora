# Development Guide

A comprehensive guide on our development process from creating tickets to contributing code.

## Sprint Cycle and Task Management
- All Development work should be Tracked in YouTrack
- During Bi-Weekly Sprint Planning Meetings, team memebers should move tasks that are ready from 'Backlogged' to 'To Do' 
- Tasks in the 'To Do' column should:
  - include a detailed description
  - be assigned a story point value
  - be assigned to a team member
  - include a git branch name (if requires development)
  - Assigned a priority (Low, Medium, High)
- Each Project in YouTrack that requires development should have a git branch created for it
- Large tasks should be broken down into smaller Sub Tasks
- Branch names should be descriptive and be prefixed with the YouTrack (task ID Ex: MCV-20-40-update-contact-forms)

## Developing in Brand Environments
- All brand environments are located in the /app/ directory
- cd into the respective brand directory and create a feature branch
- For local development, use the dev urls when testing your changes
  - dev.drumeo.com
  - dev.singeo.com
  - dev.pianote.com
  - dev.guitareo.com
- Run `yarn dev` in the root directory to test frontend CSS and JS changes.
  - Drumeo's code exists in the /laravel/ directory
- Once you've completed your task create a PR to merge into staging
- In the staging branch, run `yarn prod` to build the assets for production
- Deploy to staging using the `r deploy 'brand name' ` script and select the appropriate options for staging
- You can see your changes in the respective staging environments:
  - staging.drumeo.com
  - staging.pianote.com
  - staging.guitareo.com
  - staging.singeo.com
- If the branch is ready to be merged create a PR to merge your feature branch into master
- Once in master follow the steps outlined in the deployment guide to deploy to production

## Developing for Vuesora
- Create a feature branch off of the current stable release
  - The current release is v0.17-
- In your feature branch run the `./symlink.sh` and select the appropriate option for the brand you're working on.
- Once you've completed your task, create a pull request to merge your branch into staging.
- In the staging environment run the `/prelease.sh` script in your terminal to create a staging release of Vuesora for testing
- Once published, you can install the staging version with `yarn add vuesora@staging` in your working brand environment. 
- If the feature has been tested in staging and is ready for prod, create a PR to merge into master.
- Once in master follow the steps outlined in the deployment guide to publish Vuesora for production.

## Git Strategy 
Our strategy combines elements of the 'Feature Branch' strategy and the 'Gitflow' strategy. While trunk based development may be 
appropriate for teams pushing many small changes to a main branch (or trunk), Musora development sometimes requires long-lived feature
branches that take longer to merge. To solve this we can adopt a version of Gitflow where the main branch stores the official release history, 
and the staging branch serves as an integration branch for features. Here's the breakdown:
  - Feature Branch
    - Where you develop your feature and test locally. 
    - This branch is code-reviewed before merging into staging. 
  - Staging Branch
    - Where you deploy to staging for QA and UX testing
    - Install the staging version of Vuesora if necessary
    - If it passes QA and UX, this branch is merged into master
  - Master Branch
    - This is the code that exists in production. 
    - This branch should be kept clean. Meaning, you should not be developing on master. Again, only production ready code should exist in this branch.  

