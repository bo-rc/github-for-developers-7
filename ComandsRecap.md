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

# Using Git

## `git config` three levels
![git-config](https://cloud.githubusercontent.com/assets/14265605/11482675/c619f6f0-9769-11e5-9b74-8dcc21e4875a.png)

```bash
git config --list
git config --global user.name "<your_full_name>" 
git config --global user.email "<your_email>"
git config --global core.editor "atom --wait"
git config --global core.autocrlf # Windows: set to true; Unix: set to input.
                                  # autocrlf: "auto carriage return line feed".
git config --global push.default simple # only want to push the branch we are on.
```

## Local GitHub
### Cloning a Repository: Recap
* Start a new branch on GitHub to work on.
* Copy the clone URL on GitHub.
* Using the command line, `cd` to the directory that you want to put your local repo in.
* Type `git clone <clone_url>`.
 * You might be prompted for your password. You should enter your GitHub password at this point.
* `cd` into the new cloned repo and type `git status`.
* `git branch` will show you the available branches. Only `master` appears.
* `git branch -a` will show all the remote branches.
* `git checkout <branchname>` will create a local branch that matches the remote branch. All edits you make locally with be applied to that branch until you checkout another one.

### Two-Stage Commit
![two-stage](https://cloud.githubusercontent.com/assets/14265605/11482854/c3b7206c-976a-11e5-9368-279c99544429.png)

![git-add](https://cloud.githubusercontent.com/assets/14265605/11482921/2359b188-976b-11e5-97ca-01e2217bbd30.png)

![git-commit](https://cloud.githubusercontent.com/assets/14265605/11482934/2eb256e8-976b-11e5-80c8-9918596b931f.png)

#### The Two Stage Commit: Recap

* `git status` lets you see which files have been changed since the last commit.
* `git add <filename>` adds that file to the staging area.
* `git add .` adds all the changed and untracked files to staging.
* `git commit` will submit all those file changes under one unit of work.
* This also opens your default text editor (as set earlier in this lesson) for you to add a commit message.
* This commit will happen locally, and only on the checked out branch. If you check out another branch, the changes will no longer show in that file.

# Git and GitHub
## Pushing Changes: Recap

* Check `git status`: the working directory needs to be clean. If it's not, make sure there isn't anything that you meant to commit!
* Do `git push`: assuming you set the default push behavior to simple, this will push your changes to the same branch on the remote system.
* Back in GitHub, you can easily start a new pull request to merge the changes into `master` using the same process you learned earlier.

## Workflow
###Creating a Repository on GitHub: Recap
* Use the green `New` button on the `Repositories` tab of your GitHub profile page.
* The name of your repository must be unique to your account.
* Choose whether your repo will be public or private.
 * Anyone can can view, clone, or fork a public repo, but only collaborators can push changes to it.
 * Private repositories can only be viewed, cloned, etc. by collaborators you have added.
 * You are allowed an unlimited number of public repos on your account, but must have a paid account to have any private repositories.
* A `.gitignore` file tells git which types of files it shouldn't bother tracking. GitHub allows you to auto-generate your `.gitignore` file.
* You should add an open source license to your repository if you'd like to make it open source.
* Once you've created your repo, you can add collaborators by searching for their GitHub user name in the `Collaborators` section of the repo.

### Creating Branches Locally: Recap
* `git branch` shows which branch you're on locally, and which other local branches exist.
* `git branch <new_branchname>` creates a new local branch.
* You still must check out this new branch to edit it. `git checkout <new_branchname>`

### Workflow Review: Recap

* `git add .` adds *all* modified or new files to be committed, so you don't have to write out each file.
* You can write your commit message along with your commit command using the syntax: `git commit -m "<commit_message>"`.
* You should then push your changes up to GitHub. 
 * `git push -u origin <branch_name>` will push your (new) local branch changes to a branch with the same name on GitHub, as well as setting upt the tracking of that branch in the future (`-u`: `--set-upstream`), `git push` alone will complete the same command.
* Once this is finished, you must create a pull request on GitHub, and merge it on GitHub once it's completed.

### Pulling Changes: Recap

* When the remote repository has been changed (such as after someone else's pull request is merged), your local repository will not be updated until you choose for it to be.
* The command `git pull` will make your local working branch up to date with the remote version of that same branch.
* This will not delete local branches that have been deleted on the remote repo.
* To delete local branches that do not have a remote counterpart, use the `git branch --merged` command to list all such local branches, and then `git branch -d <branchname>` to delete specific local branches.

## Working with local files
`git checkout -b "<new_branchname>"` is a quick way to both create a new branch and check it out.

### Viewing Local Diffs: Recap

* `git diff` allows you to compare different versions of a file against each other.
* On its own, `git diff` compares the working directory to the staged version of the file.
* `git diff --staged` compares the staged version to the most recent commited version.
* `git diff HEAD` *combines* the changes in your working and staged versions of the file, and compares them to the version of the file designated as HEAD (most often, the most recent commit).
* `git diff --color-words` displays a word-by-word comparision rather than a line-by-line comparison, helpful for small changes.

![git-diff](https://cloud.githubusercontent.com/assets/14265605/11483301/4f041d62-976d-11e5-982d-915065cc6e5c.png)

### Merging Local Changes: Recap

* When performing a merge, you need to have checked out the branch you are merging into.
* `git merge <branchname_to_merge>` will merge the branch locally.
* To send the merge to the remote, simply `git push`. If you already have a PR for that branch open on GitHub, this will automatically close that PR.
* You must still delete the branch separately on GitHub (in the PR window) and locally (using `git branch -d <branchname>`).

### Viewing Project History: Recap

* `git pull` updates the local directory to include all the changes made to the remote directory, even those done by other people.
* `git log` provides a list of all of the commits on the current branch, with the most recent commit first.
* `Up` and `down` arrows navigate, `enter` cycles through log entries, and q quits log viewing screen.
* `git log --oneline` shows a smaller version of the log.
* `git log --oneline --graph` shows a graph of the changes along with the one-line log.
* `git log --oneline --graph --decorate` includes information about the branches and the head.
* `git log --oneline --graph --decorate --all` also includes unmerged branches.
* `git log --stat` tells you which files were included in each commit.
* `git log --patch` shows the actual changes that were made in each commit as diffs.

## Reverting
### Creating a Repository on the Command Line: Recap

* To create a project from scratch, type `git init <directoryname>`.
* This creates the directory as a subdirectory of the current location, and initializes a repo there.
* You will have to create your `README.md` file manually.

### Handling Merge Conflicts: Recap

* When you have a merge conflict, type `git status` and look for "unmerged paths" to see which files are creating the merge conflict.
* Open the file in your text editor. You will see some lines that look like the following:

```
<<<<<<<< HEAD
Some text here.
========
Different text here.
>>>>>>>> merge-me
```
* The text above and below the equal signs are what is causing the merge conflict. They appear on the same line but are different text.
* Decide how you want to resolve the conflict, and once that's completed delete the merge markers. Save and close your text editor.
* `git status` will show that the files are no longer in conflict, but that you are in the middle of a merge. git add the file and then `git commit` it, and the merge will then automatically complete.

### Renaming and Moving Files: Recap

* When moving files, use the command `git mv` rather than just the `mv` command.
* The syntax for this is `git mv <filename> <new_directory>/<filename>`.
* `git mv` automatically `add`s the file to the staging area after it is moved, so it can be commited right away.
* Just as with `mv`, you can use `git mv` to rename a file like so: `git mv <filename> <new_filename>`.

### Reverting Commits: Recap

* When reverting, you revert a specific commit.
* Find that commit, and copy the first several characters of the SHA-1 hash.
* `git revert <commit_hash>` will create a new commit that is the exact opposite of the commit you're reverting.

### Fixing Bad Commits: Recap

* The command `git commit --amend` will add whatever is in your staging area to your last commit, and allow you to edit that commit message.

### Unstaging Files: Recap

* `git reset HEAD <filename>` will remove a file from the staging area, putting it back in your working directory.

### `git reset`

*modes*:

![git-reset](https://cloud.githubusercontent.com/assets/14265605/11483554/94e22a80-976e-11e5-9e68-89141893da7a.png)

#### Git Reset Options: Recap

* `git revert` reverts a specific commit. `git reset` resets git to a specific commit.
* `git reset --soft <to_commit>` resets git to a specific commit, and puts the commits you're resetting into the staging area where they can be easily re-committed.
* `git reset --mixed <to_commit>` resets git to a specific commit, and puts the commits you're resetting into the working directory so you can edit them directly.
* `git reset --hard <to_commit>` resets git to a specific commit, and deletes the commits you're resetting.
* Just like with `git revert` you can use the commit ID, or you can use the syntax `HEAD~<number>`. The number you put will be the number of commits backwards from the current `HEAD` that git will move the new HEAD to.
* You can always use `git log` to see all your previous history to know where to reset to.

