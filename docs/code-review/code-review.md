# Code Review

_If there are n developers in the room, then there are n+1 opinions on how things should be done._

### Communication

- Accept that many programming decisions are opinions. Discuss tradeoffs, which you prefer, and reach a resolution quickly.
- Ask good questions; don't make demands. ("What do you think about naming this :user_id?")
- Good questions avoid judgment and avoid assumptions about the author's perspective.
- Ask for clarification. ("I didn't understand. Can you clarify?")
- Avoid selective ownership of code. ("mine", "not mine", "yours")
- Avoid using terms that could be seen as referring to personal traits. ("dumb", "stupid"). Assume everyone is intelligent and well-meaning.
- Be explicit. Remember people don't always understand your intentions.
- Be humble. ("I'm not sure - let's look it up.")
- Don't use hyperbole. ("always", "never", "endlessly", "nothing")
- Don't use sarcasm.

### Having Your Code Reviewed

- Be grateful for the reviewer's suggestions. ("Good call. I'll make that change.")
- Be aware of how hard it is to convey emotion and how easy it is to misinterpret feedback. If feedback seems aggressive or angry or otherwise personal, consider if it is intended to be read that way and ask the person for clarification of intent, in person if possible.
- Assume the best intention from the reviewer's comments.
- Explain why the code exists. ("It's like that because of these reasons. Would it be more clear if I rename this class/file/method/variable?")
- Seek to understand the reviewer's perspective.

### Reviewing Other Developers Code

- Communicate which ideas you feel strongly about and those you don't.
- Identify ways to simplify the code while still solving the problem.
- If discussions turn too philosophical or academic, move the discussion to another time.
- Offer alternative implementations, but assume the author already considered them. ("What do you think about using a custom validator here?")
- Seek to understand the author's perspective.
- Remember that you are here to provide feedback, not to be a gatekeeper.

---

## Review Resources

### PHP
- [https://www.php-fig.org/psr/](https://www.php-fig.org/psr/)
- [https://code.tutsplus.com/series/the-solid-principles--cms-634](https://code.tutsplus.com/series/the-solid-principles--cms-634)
- [https://thevaluable.dev/dry-principle-explained/](https://thevaluable.dev/dry-principle-explained/)
- [http://verraes.net/2014/08/dry-is-about-knowledge/](http://verraes.net/2014/08/dry-is-about-knowledge/)
- [https://github.com/alexeymezenin/laravel-best-practices](https://github.com/alexeymezenin/laravel-best-practices)
- [https://github.com/biberlabs/awesome-doctrine](https://github.com/biberlabs/awesome-doctrine)


### JS
- _coming soon_

---

## The Process

### 1. Code reviews will be scheduled by Caleb after a large project is completed. Each review will be for a specific completed project (or partially completed in some cases). The review may or may not include the entire development team.

Caleb will schedule the date and time for the reviews in Google Calendar. For some projects, only the developers from that specific department will be involved in the code review. For example a backend only project will generally only be reviewed by the backend developers.

### 2. On each scheduled code review day, reviewees will go through the projects code and note their feedback in a document.

Write your feedback anytime during the allotted work day. Information about the project undergoing review and where you can access the code will be inside of the google event details. Please spend up to a full day reviewing the project and writing your feedback.

### 3. After the review day is complete a meeting will be scheduled (usually the next morning) where each developer will present their feedback.

During the meeting each involved developer will present their feedback. Caleb will put the code in question on the meeting room TV and on his video conference stream so we can all look at the code and feedback together. We will discuss the feedback and any workflow/system changes that need to be made.

### 4. All invited developers should give their best effort to provide some feedback, whether positive or negative.

You will be expected to attend code review days and present your feedback in the follow up meeting for any projects that involve your department. If you only have basic feedback or positive feedback, that is totally fine.

### 5. When the review meeting is finished it is up to the involved developers to note and plan a time to carry out any necessary changes.

During the review meeting the developers who have been working on the project should note any improvement or changes required for their work. Caleb will also keep track of conclusions drawn from the meeting.

### 6. Our review process is meant to help us motivate and reward each other.

Please be respectful and mindful of others. If you believe something should be done a certain way always be aware that your solution may not be the best solution. We will make important programming decisions as a team, not only based on 1 team members opinion. If there are any lasting conflicts we will either have a vote, or I will make the final call.

### 7. Please do not reach out to others directly to criticise them or their work, or to assign them tasks or fixes privately.

The goal of this process is to ensure all feedback happens in an open place where everyone can learn and provide value. If you have a problem with someone else's work and you are not willing to mention it to the entire team (or in the relevant slack channel), please keep it to yourself or reach out to me directly.

### 8. Caleb posts review summary in the slack code-review channel.

## Tools

- Google Calendar
- YouTrack
- Google Docs
- Slack (code-review channel)
- Github

## How To Prepare For A Code Review Meeting

1. Review the code and put your feedback in a google doc. Include line numbers and file names, so we can track down the files in the review meeting. You are not required to share your actual document, however it may be a good idea.
2. During the meeting, present your feedback. We will go file by file or line by line if necessary be during the meeting.
3. If your code is being reviewed, note any changes or updates that come up as a result of feedback from other developers.
4. Ask questions if you do not understand any of the code being presented/reviewed so we can learn from and discuss different engineering decisions.

## Meeting Schedule

1. Greetings and setup.
2. Caleb or the project owner presents a brief overview of the project undergoing review.
3. 1 by 1 each developer in question presents their feedback and we discuss it.
4. An opportunity to share final thoughts.
5. Meeting ends.