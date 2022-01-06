# Code Review

_If there are n developers in the room, then there are n+1 opinions on how things should be done._

https://google.github.io/eng-practices/review/reviewer/  
https://testing.googleblog.com/2019/11/code-health-respectful-reviews-useful.html

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
- [https://laravel.com/docs/4.2/contributions#coding-style](https://laravel.com/docs/4.2/contributions#coding-style)
- [https://code.tutsplus.com/series/the-solid-principles--cms-634](https://code.tutsplus.com/series/the-solid-principles--cms-634)
- [https://thevaluable.dev/dry-principle-explained/](https://thevaluable.dev/dry-principle-explained/)
- [http://verraes.net/2014/08/dry-is-about-knowledge/](http://verraes.net/2014/08/dry-is-about-knowledge/)
- [https://github.com/alexeymezenin/laravel-best-practices](https://github.com/alexeymezenin/laravel-best-practices)
- [https://github.com/biberlabs/awesome-doctrine](https://github.com/biberlabs/awesome-doctrine)


### JS
- _coming soon_

---

## The Process

We use GitHub and pull requests to review code. Generally you can only create a pull request if you have another branch
to compare against. With large project launches we often want to do code review over a large span of changes in the 
master branch. When there is no other branch to compare against we need to make one so a PR can be submitted.  

**You can set up a PR for the changes between any 2 commits in the commit history on a single branch like this:**
1. Start with the branch which has the commits you wish to review, for example 'master'
1. Make a new branch based on this branch, for example: 'master-project-z-code-review'
1. On this new branch, 
   [hard reset](https://stackoverflow.com/questions/9529078/how-do-i-use-git-reset-hard-head-to-revert-to-a-previous-commit/9530204) 
   it back to the commit you wish to compare against the current state
1. Push the branch
1. Create a new PR on github. Set the 'base' branch as your new reset branch 'master-project-z-code-review'. Set the compare branch as your original final state branch 'master'
1. PR can now be used for code review