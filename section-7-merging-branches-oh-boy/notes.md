# Section 7: Merging Branches, Oh Boy!

## What Really Matters In This Section
- Critical 
  - Fast Forward Merges 
  - Git Merge & Merge Commits 
  - Resolving Merge Conflicts 
- Nice to Have
  - Using VSCode to Resolve Conflicts 

## An Introduction to Merging
- Merging 
  - Branching makes it super easy to work within self-contained contexts, but often we want to incorporate changes from one branch into another 
  - We can do this using `git merge` command
- A common workflow 
  - Master Branch (trunc) --> feature branch with commits --> merged to head of master 
- Merging 
  - The merge command can sometimes confuse students early on. Remember these two merging concepts: 
    - We merge branches, not specific commits 
    - We always merge to the current HEAD branch 
- Merging Made Easy 
  - To merge, follow these basic steps:
    - Switch to or checkout the branch you want tot merge the changes into (the receiving branch)
    - Use the `git merge` command to merge changes from a specific branch into the current branch 
    - To merge the bugfix branch into master 
      - `git switch master`
      - `git merge bugfix`
- See slides for visual representation 

## Performing A Fast Forward Merge
- `git branch -v` -- we get the last commit with the branch 
- Simpler merge to perform -- has to move a pointer up a couple of commits 
  - Switch to the branch and then merge some other branch in 

## Visualizing Merges
- You can update your commits from GitKraken as well 
- Master is going to fast-forward and catch up with those commits 

## Generating Merge Commits
- Not all merges are fast forwards 
  - What if we add a commit on  master? 
    - This happens all the time, imagine one of your teammates merged in a new feature or change to master while you were working on a branch 
  - What happens when I try to merge? 
    - Rather than performing a simple fast forward, git performs a "merge commit" 
    - We end up with a new commit on the master branch 
    - Git will prompt you for a message 
    - We can then have two different parent commits - one on bugfix and one on the master branch 

## Oh No! Merge Conflicts!
- Heads Up! 
  - Depending on the specific changes you're trying to merge, Git may not be able to automatically merge. This results in merge conflicts, which you need to manually resolve 
- Git will fail the merge 
- When you encounter a merge conflict, Git warns you in the console that it could not automatically merge 
  - It also changes the contents of your files to indicate the conflicts that it wants you to resolve 
- Conflic markers 
  - The content from your current HEAD (the branch you are trying to merge content into) is displayed between the <<<<< HEAD and =======
  - The content from the branch you are trying to merge from is displayed between the ===== and >>>> 
- Resolving Conflicts 
  - Whenever you encounter merge conflicts, follow these steps to resolve them: 
    - Open up the file(s) with merge conflicts 
    - Edit the file(s) to remove the conflicts. Decide which branch's content you want to keep in each conflict. Or keep the content from both 
    - Remove the conflict "markers" in the document 
    - Add your changes and then make a commit 

## Resolving Merge Conflicts
- Once a branch is merged in, you then are able to delete the branch without a force delete 

## Using VSCode To Resolve Conflicts
- VSCode has the options for 
  - Accept Current Change 
  - Accept Incoming Change 
  - Accept Both Changes 
  - Compare Changes 
  - Or you can delete everything and put whatever you wanted 
- GitKraken will also show you the conflicts 

## Merging Exercise
- Completed Section Exercise on Merging 