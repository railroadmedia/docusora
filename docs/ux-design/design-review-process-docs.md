# Design Review Process

The core purpose of a design review is to get feedback from people across teams and departments. 
A design review ensures that the design meets the business’s goals and serves our students to the best degree possible. 
Design reviews are crucial, and if not done well, they can go wrong quickly and have a negative impact on the 
end product.

Generally there are 2 types of design review:  

**Internal**
    - Creating, reviewing, and collaborating on designs internally withing the UX Design and Product team.  
**External** 
    - Presenting designs to other teams or stakeholders to collect feedback.


## Internal Design Review

### The Figma Branch Strategy

Much like git repositories and branches in development, branches in Figma are a way of cloning an existing design
element or file, making changes to it, reviewing its differences from the original, then merging those changes back in 
to the original after approval. It allows multiple team members to branch a design, experiment and make changes, then 
present those changes to the team or project lead. Their system makes it easy to review multiple proposed changes
from multiple people, provide feedback, find the best option, then merge the final changes in to the master file.

I highly recommend reading Figma's official documentation on how review, approval, and branches work: 
[https://www.figma.com/best-practices/branching-in-figma/](https://www.figma.com/best-practices/branching-in-figma/)

### Our Design Process

**1. The assigned design lead for a project creates the master file and initial designs.**  

Often times a master file will already exist, in which case this step should be skipped and instead a new branch
should be created from the master file. In the future we hope to have master files for the entire platform that are 
maintained and always used to branch off of.

**2. The design lead requests a design review.**  

The design lead is responsible for posting a slack message in the 'pr-ux-design' channel requesting design review. 
It must include a link to the figma file or figma branch as well as some details about the project that are 
relevant to the design.

Examples:

```
I have completed the first draft of our new sidebar design. This is a brand new project without an existing 
master file so its a new file built from scratch. Please review the new sidebar here *LINK* and add your comments 
in figma or make your own branch from my file to propose changes.
```

```
I have redesigned our filtering system for our content organisation project. 
The changes are on this branch *LINK* which based on the master file for our current filtering design.
Please review the changes in the branch. 
```

**3. Reviewers comment on the design or create branches if they want to propose their own changes or ideas.**  

This generally happens asynchronously but can happen in a design review meeting as well. Sometimes we'll be able to
land on a final design decision asynchronously via figma or slack conversation, other times a meeting will be needed. 
It's up to the lead project designer to facilitate which is necessary.

**4. Design lead for the project makes final changes or merges in branches and requests final approval.**

Before a design change is approved for development, it must be approved by either Caleb F, Jord P, or Randy E. Often 
times approval responsibility will be assigned to the UX design team member who is leading the project. If this is the 
case one of the 3 approves mentioned above will let the project lead know.  

When requesting approval in the context of review, please always tag Caleb F, Jord P, and Randy E at minimum.


**4. Project design lead merges the approved branch changes in to the master file or if there is no existing master file, the new file becomes the master file.**


## External Design Review

_Coming soon..._