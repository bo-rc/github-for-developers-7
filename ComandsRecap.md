# Using github

## Using Issues: Recap

* You can use Markdown to format issues.
* You can @mention somebody in order to alert them of the issue.
* The "Preview" tab shows how your comment will be rendered.
* Add screenshots or pictures to the issue by simply dragging and dropping them into the comment field.
* You can assign an issue to anyone with access to the repo.
* Labels can be used to organize issues.
* You can filter issues by label, author or assignee.

## GitHub Flow
### Branch and Pull Request (PR)
![pr](https://cloud.githubusercontent.com/assets/14265605/11482337/dd3ed6ea-9767-11e5-8fc1-8ca0bd5ee546.png)

* Everything on GitHub lives on a branch.
* The "canonical" version of the code lives on the `master` branch by convention.
* Use new branches to experiment with the code without affecting master.
* When you're done experimenting and want to add the feature into `master`, you create a pull request (PR).
* PRs don't have to be perfect, but should be ready for other people to look at, comment on, and work on.
* Once the changes to the PR are completed, the branch is "merged" into `master` and can then be removed.

### Creating a Branch: Recap

* Create a branch by clicking on the `branch` drop-down and entering your branch name in the text field.
* Any files you create, edit, or delete will then be applied to that branch.
* Be careful; GitHub automatically puts you on `master` when you leave the repo and come back, so always make sure you're on the right branch before you start working.

### Understanding Pull Requests: Recap

* Pull Requests (or PRs) are used to add code to another branch, in this case `master`.
* A Pull Request asks that the team merge one branch into another.
* The ***base*** is the branch you want to merge ***into*** (often `master`), the ***compare*** is the branch you're merging, in this case the feature branch.
* Make sure to leave a comment to tell people what changes you made and why.
* In the comment, you should put number sign (`#`) in front of the number of the issue that you're fixing. This will automatically link your PR to that issue.
* Once you've made the PR, the `Files changed` view allows you to see what this PR will change on the base branch. Red means "deleted", green means "added". This view is often called the "diff".
* You can add comments directly to the diff, or in the `Conversations` view.
* You can edit PR after PR issued; the changes, once committed, will be included in the PR.

### Merging Pull Requests: Recap

* To merge your branch into the master branch, click the `Merge pull request` button in the `Conversation` view.
* Use the keyword `Fixes` followed by `#` and the issue number to close the issue at the same time as you merge the PR.
  * A full list of keywords for closing issues via commit msg:
    * `close`
    * `closes`
    * `closed`
    * `fix`
    * `fixes`
    * `fixed`
    * `resolve`
    * `resolves`
    * `resolved`
    * e.g. `This closes #34, closes #23, and closes another_user/his_repo#42`
* Once the PR is successfully merged, you can delete your feature branch as it is no longer needed.









