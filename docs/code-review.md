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

### 1. Code reviews will be scheduled weekly and will last 1-2 hours.

I will be scheduling the day and time of review a few weeks ahead of schedule so we can avoid conflicts with deadlines and deploy dates. Code review will be scheduled in Google Calendar. Remote developers are free to do the code review anytime during their work day.

### 2. On each code review day 2 team members will be scheduled for review. The entire development team, including QA, devops, and the developers in marketing will review the 2 scheduled team members work independently.

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

\* of every month.

**First week:**
- Caleb (back end dev)
- Jon M (back end dev)

**Second week:**
- Curtis (front end dev)
- Bogdan D (front/back end dev)

**Third week:**
- Roxana (back end dev)
- Trent (front end dev)

**Forth week:**
- Tee (sysops/devops)
- Jon C (QA/automated testing)

**Note: During your scheduled week you are still required to review your partners code. For example during week 1 review Jon M and I will still review each others code along with everyone else.**

## Tools

- Google Calendar
- YouTrack
- Slack (code-review channel)
- Github

## Review Process

1. Team members under review list and outline their work and commits over the last month, including github links when necessary
2. Reviewers review the code/systems in question
3. Reviewers post feedback in the Slack, including screenshots or links to github commits
4. At the end of review team members under review go over the feedback and create/schedule stories for any required changes
5. Reviewers update code standards documentation as necessary to prevent future quality issues

## Example Schedule

Week 1: Jon & Caleb scheduled for 1pm on Thursday.

1. Anytime before 1pm Jon and Caleb prepare an outline of what they worked on for the last few months, along with github links or other resources.
2. At 1pm (or later in the night for the remote devs) all other team members begin reviewing and going through all the work Jon & Caleb have outlined. As they review they write feedback inside slack.
3. The following day once all review is complete, Jon & Caleb go through all the feedback and create stories/schedule an necessary updates.

## References

I am always open to feedback and we will likely shape the process as we try it and learn. For those curious about my reasoning behind this process:

https://slack.engineering/how-about-code-reviews-2695fb10d034
https://www.codeproject.com/Articles/524235/Codeplusreviewplusguidelines
https://blog.fullstory.com/what-we-learned-from-google-code-reviews-arent-just-for-catching-bugs/
https://sback.it/publications/icse2018seip.pdf
https://blogs.msdn.microsoft.com/vsappcenter/how-the-visual-studio-mobile-center-team-does-code-review/
https://en.wikipedia.org/wiki/Code_review