# Section 19: The Power of Reflogs - Retrieving "Lost" Work

## What Really Matters In This Section
- Important 
  - Exporting Reflog Files 
  - The Git Reflog Command 
  - Rescuing Lost Commits With Reflog 
- Nice to Have
  - Time-Based Reflog Qualifiers 

## Introducing Reflogs
- reflogs 
  - Git keeps a record of when the tips of branches and other referneces were updated in the repo 
  - We can view and update these reference logs using the `git reflog` command 
- HEAD Reflog 
  - Commit G - New Commit 
  - Commit H - New Commit 
  - Commit D - Switched to main from feature 
  - Commit H - Switched to feature from main 
- You can view the logs in the .git directory 
  - In the file HEAD - it tracks when you update the HEAD, switch branches 
  - It is tracking the moves of the HEAD reference 
  - Keeps track of the tip of every branch and when you push 

## The Limitations of Reflogs
- Limitations! 
  - Git only keeps reflogs on your local activity. They are not shared with collaborators 
  - Reflogs also expire. Git cleans out old entries after around 90 dyas, though this can be configured 

## The Git Reflog Show Command
- Git Reflog 
  - The git reflog command accepts subcommands show, expire, delete, and exists. Show is the only commonly used variant, and it is the default subcommand 
  - `git reflog show` will show the log of a specific refernece (it defaults to HEAD)
  - For example, to view the logs for the tip of the main branch we could run `git reflog show main`
  - `git reflog show HEAD`
  - `git reflog`
- Will show you the most recent entry 
- Will show you the reflog identifier `HEAD@{4}`
  - The numbers are not set in stone 
  - You can see the tip of a branch as well 

## Passing Reflog References Around
- Reflog References 
  - We can access specific git refs as `name@{qualifier}`. We can use this syntax to access specific ref pointers and can pass them to other commands including checkout, reset, and merge 

## Time-Based Reflog Qualifiers
- Timed References 
  - Every entry in the refernece logs has a timestamp associated with it. We can filter reflogs entries by time / date by using time qualifiers like: 
    - 1.day.ago
    - 3.minutes.ago
    - yesterday
    - Fri, 12 Feb 2021 14:06:21 -0800
  - `git reflog master@{one.week.ago}`
  - `git checkout bugfix@{2.days.ago}`
  - `git diff main@{0} main@{yesterday}`

## Rescuing Lost Commits With Reflog
- Reflogs Rescue
  - We can sometimes use reflog entries to access commits that seem lost and are not appearing in git log 
- `git reset --hard <commit-hash>` - removes changes from your working directory 
- To access the commit you may have accidentally reset, you can use the reflogs and we can restore that commit 
  - `git reset --hard master@{1}` - reset the tip of this branch to whatever is at `master@{1}` 

## Undoing A Rebase w/ Reflog - It's a Miracle!
- We can add multiple commits that were sqaushed back in, you can undo the rebase by going back to the original commit you started the squash 