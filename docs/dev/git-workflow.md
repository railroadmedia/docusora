# Git Strategy

Our strategy combines elements of the 'Feature Branch' strategy and the 'Gitflow' strategy. 
While trunk based development may be appropriate for teams pushing many small changes to a main branch (or trunk), 
Musora development sometimes requires long-lived feature branches that take longer to merge. 
To solve this we can adopt a version of Gitflow where the main branch stores the official release history, 
and the staging branch serves as an integration branch for features.



## Repository Types

### **Implementation Repositories**  
Implementation repositories are for entire brands, tools, websites, or apps. They represent a final implementation for a product that is
used by customers. Often times these repositories are Laravel projects, React Native projects, 
WordPress blogs, or development tools.  


### **Package Repositories**
Package repositories are for reusable packages such as PHP packages or JS packages. They are versioned and often published to 
packagist or NPM. These packages are installed and utilised inside the implementation repositories.



## Branch Types & Prefixes

### **Hotfix Branches**  
Hotfix branches are for a small changes that will can be reviewed and deployed quickly.

- Prefix: **hotfix-**
- Example branch names: hotfix-fix-layout-bug, hotfix-remove-test-code, hotfix-change-image


### **Feature Branches**  
Feature branches are for features and updates that require a significant amount of time and commits to finish. Typically, these
updates need to be code reviewed and tested by QA.

- Prefix: **feature-**
- Example branch names: feature-improved-sorting, feature-header-redesign, feature-new-content-api-endpoint


### **Project Branches**  
Project branches are for full projects that will involve multiple other branches and multiple developers.
Typically, these branches live for the entire length of a project which can be multiple months.
These branches are merged in to master for final deployment.

- Prefix: **project-**
- Example branch names: project-coaches-2.0, project-unified-platform, project-user-playlists


### **Version Branches**  
Version branches are for package repositories which are version controlled. These repositories have core branches
which represent an entire version. For example a PHP package repository might have the branches, v1.0, v2.0, etc.
These core version branches are considered the 'master' branch for that version.  
The same types of branches above apply when developing on version branches (hotfix, feature, project). 
The only difference is that branches in these package repositories should always be prefixed with the version number.

- Prefix: **vX.X-**
- Example branch names: v1.0-hotfix-sorting-bug-fix, v7.2-feature-new-header-components, v12.0-project-new-api


### **Deployment Branches**
Deployment branches are for sending code to a specific server environment. Here is a list of our current deployment branches:
_(subject to change soon, Feb 2022)_

- **master**
  - These branches always represent our live production environments. Development should never be done directly on the 
  master branch. Code should only every be pushed to master if it is safe to be deployed at any time. Even if you
  push something to master but intend to deploy it at a later time, another developer might deploy those commits to
  the production server at any time.

- **staging**
  - These branches represent our staging environments which are used for testing and review. Development should never
  be done directly on a staging branch. Staging is regularly deleted and recreated from another branch so any commits
  pushed directly to staging that don't exist on another branch can be permanently deleted. Staging is only for merging 
  other branches in to. Generally it's safe to push any updates to staging unless there are conflicts with other 
  developers updates. Our staging environments are being updated soon so this is subject to change.

- **app-staging**
    - Same as staging, but generally used for back end updates for our mobile app APIs.



## Mobile App Repositories

## Branch Types & Prefixes

### **Hotfix Branches**  
Hotfix branches are for a small changes that will be reviewed and deployed quickly.

- Prefix: **hotfix-taskNumber**
- Example branch names: hotfix-BR-121, hotfix-MCV20-216, hotfix-MT-82

### **Bug fixing Branches**  
Bug fixing branches are for bugs that will be code reviewed, tested and merged into staging. After a bug is found a new branch is 
created from 'staging' branch, 'BR-number'. Bug is fixed on new branch and is ready for code review. Once reviewed, it goes into QA pipeline. 
If approved, it is merged into staging else fixed on the bug branch.

- Prefix: **BR-**
- Example branch names: BR-121

### **Feature Branches**  
Feature branches are for features and updates that require a significant amount of time and commits to finish. Typically, these
updates need to be code reviewed and tested by QA. These get merged into a Project Branch when working on a new project or into staging
when a small new feature needs to be done.

- Prefix: **feature-taskNumber**
- Example branch names: feature-MCV20-1, feature-MT-8

### **Project Branches**  
Project branches are for full projects that will involve multiple other branches and multiple developers.
Typically, these branches live for the entire length of a project which can be multiple months.
These branches are merged in to staging for final deployment.

- Prefix: **project-**
- Example branch names: project-coaches-2.0, project-unified-platform

### **Deployment Branches**
Deployment branches are for creating builds that can be deployed on Google Play/App Store. Here is a list of our current deployment branches:

- **production**
  - This branch always represents our live production environment. Development should never be done directly on the 
  prod branch. Staging branch is merged into prod when the prod builds are released to the apps.

- **staging**
  - Staging is used for testing and review. Development should never be done directly on a staging branch. Staging is 
  only for merging other branches in to. Generally it's safe to push any updates to staging if this update is approved through 
  code review and testing, unless there are conflicts with other developers updates.
