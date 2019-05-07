# Code Review

## Goals

The goals of our code review process are:

- To promote openness and give the opportunity to provide constructive criticism and praise
- To continually increase code/systems quality and maintain our coding standards and styles
- To reduce bugs and issues in code or systems before they are shipped
- To give all team members the opportunity to learn and grow from others work
- To help spark new ideas
- To maintain healthy teamwork
- To reward and promote high quality work

## Outline

There are an endless amount of resources online for code review processes and practices, including detailed outlines from big companies like Google and Microsoft. I have done my best to combine the best aspects of their processes and modify them in a way that will work for us.

### 1. Code reviews will be scheduled every few months per department and will last 3-4 hours (or up to a full work day if necessary and time permits).

I will be scheduling the day and time of review a few weeks ahead of schedule so we can avoid conflicts with deadlines and deploy dates. Code review will be scheduled in Google Calendar. Remote developers are free to do the code review anytime during their work day.

### 2. On each code review day an entire department of the development team will be scheduled for review. The entire team, including QA, devops, and the developers in marketing will review the departments team members work independently. The departments are: back end, front end, qa/devops.

This will ensure all code is reviewed by multiple team members and if others are away or on vacation there will always be someone around to do the review.

### 3. It's up to the scheduled team members to outline how others can easily track down the code they have committed and give a rough overview of what they worked on.

This will prevent code that is still in progress or in a refactoring stage from unnecessarily being reviewed. We should not be critiquing code that is still in the early development phase since most of us worry less about cleanliness and quality in the early stages of development.

### 4. Everyone must give their best effort to provide at least a some feedback, whether positive or negative.

Participation is key to a healthy code review process. The only exception to this is if you are away or have critical work to do.

### 5. When the review is finished it is up to the people undergoing review to schedule and plan a time to carry out any necessary follow up changes.

### 6. The review process is designed to help us motivate and reward each other.

Please be respectful and mindful of others. If you believe something should be done a certain way you could still be incorrect. We will make important programming decisions as a team, not purely based on 1 team members opinion. If there are any lasting conflicts we will either have a vote, or I will make the final call.

### 7. Please do not reach out to others directly to criticise them or their work, or to assign them tasks or fixes privately.

The goal of this process is to ensure all feedback happens in an open place where everyone can learn and provide value. If you have a problem with someone else's work and you are not willing to mention it to the entire team, please reach out to me directly.

## Scheduling

Caleb will schedule the review events manually. The goal is to get in 6 code reviews each per year for front end and back end, and 4 reviews per year for qa/devops.

An example could look like this:

- January: Backend & Frontend
- March: QA/Devops
- April: Backend & Frontend
- June: Backend & QA/Devops
- July: Frontend
- August: QA/Devops
- September: Backend & Frontend
- October: Backend
- November: Frontend
- December: Backend & Frontend & QA/Devops

## Tools

- Google Calendar
- YouTrack
- Google Docs
- Slack (code-review channel)
- Github

## Review Process

1. Team members under review list and outline their work and commits over the few months, including github links when necessary
2. Reviewers review the code/systems in question
3. Reviewers create a new google document for their feedback, including screenshots or links to github commits
4. When reviewers are finished they link and share their google doc in the slack #code-review channel
4. At the end of review team members under review go over the feedback and create/schedule stories for any required changes
5. Reviewers update code standards documentation as necessary to prevent future quality issues

## Google Docs Organization & Naming Schema

All docs should sit inside the shared folder: **Development Department / Code Reviews / 'X | DATE: REVIEWEES'**

[https://drive.google.com/drive/folders/1jZgkF_UBhwE5n6Ko7CL8q4sWS1y0iq9Y](https://drive.google.com/drive/folders/1jZgkF_UBhwE5n6Ko7CL8q4sWS1y0iq9Y)

- For example folder 1 is called: '1 | March 21 - 2019: Back End Review'. A new folder will be created before review starts  

**There are 3 types of review documents: 'overview', 'feedback', 'summary'**
- 'overview' is the document describing the team members work to be reviewed
- 'feedback' is the document that holds the feedback for the team member being reviewed
- 'summary' is the full code review summary, which will usually be created by Caleb  

Each **overview** document title should follow the following naming schema: 'TYPE - X - MONTH DD YEAR'

- Where X is the name of the team member being reviewed
- Examples:  'Overview - Caleb - March 21 2019'
- Examples:  'Overview - Jon M - March 21 2019'  

Each **feedback** document title should follow the following naming schema: 'TYPE - For X/Y - From Z - MONTH DD YEAR'

- Where X/Y are the names of the team members being reviewed, Z is the team member doing the review (the reviewer)
- Examples: 'Feedback - For Caleb - From Jon M - March 21 2019'
- Examples: 'Feedback - For Caleb/Jon M - From Jon C - March 22 2019' for a combined feedback doc


## Example Schedule

Back end scheduled for May 1st.

1. Anytime before May 1st the backend team (Jon, Caleb, Roxana, Bogdan D) prepare an outline of what they worked on for the last few months, along with github links or other resources.
2. On review day all other team members begin reviewing and going through all the work that has been outlined. As they review they each write feedback inside their own google doc.
3. When the review is finished all the reviewers post and share links to their feedback doc inside the #code-review slack channel.
4. The following day once all review is complete, the backend team goes through all the feedback and create stories/schedule an necessary updates.

## References

I am always open to feedback and we will likely shape the process as we try it and learn. For those curious about my reasoning behind this process:

* https://slack.engineering/how-about-code-reviews-2695fb10d034
* https://www.codeproject.com/Articles/524235/Codeplusreviewplusguidelines
* https://blog.fullstory.com/what-we-learned-from-google-code-reviews-arent-just-for-catching-bugs/
* https://sback.it/publications/icse2018seip.pdf
* https://blogs.msdn.microsoft.com/vsappcenter/how-the-visual-studio-mobile-center-team-does-code-review/
* https://en.wikipedia.org/wiki/Code_review