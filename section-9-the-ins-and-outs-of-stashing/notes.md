# Section 9: The Ins and Outs of Stashing

## What Really Matters In This Section
- Some people don't use git stash that often
- Important 
  - Git Stash Basics 
  - Git Stash save 
  - Git stash pop
- Nice to Have
  - Git stash apply 
  - Dropping and cleaning the stash 
  - Working with multiple stashes 

## Why We Need Git Stash
- I'm on master and I make a new branch and switch to it and then you have uncommitted work on an old branch and you need to switch back to another branch quickly 
- Options 
  - My changes come with me to the destination branch 
  - Git won't let me switch if it detects potential conflicts 

## Stashing Basics: Git Stash Save & Pop
- Stashing 
  - Git provides an easy way of stashing these uncomitted changes so that we can return to them later, without having unnecessary commits 
- Git Stash 
  - `git stash` is super useful command that helps you save changes that you are not ready to commit. You can stash changes and then come back to them later 
  - Running stash will take all uncommitted changes (staged and unstaged) and stash them, reverting the changes in your working copy 
  - You can also use `git stash save` instead 
- Stashing 
  - Use `git stash pop` to remove the most recently stashed changes in your stash and re-apply them to your working copy 
- Branch: bugfix 
  - Working directory 
    - modified nav.css 
    - modified nav.js 
  - Staging Area 
    - modified index.js 
    - created footer.js 
  - Repository 
    - 0026739
    - bb43f1f
  - Working on this and then a coworker asks for help 
  - I'm not at all ready to commit these changes, but I also don't want to take them with me to master 
  - git stash 
    - All of my uncommitted changes have been stashed away 
      - The stash has the following changes from: 
        - Working Directory 
        - Staging Area 
- Stash 
  - Now that I have stashed my changes, I can switch branches, create new commits, etc. 
  - I head over to master and take a look at my coworker's changes 
  - When I'm done, I can re-apply the changes I stashed away at any point 
- git stash pop
  - My stashed changes are restored! 
  - Puts everything back in the working directory and the staging area 

## Practicing With Git Stash
- index - what git calls the staging area 

## Git stash Apply
- 90% of the time you're primarily going to just use `git stash` and `git stash pop`
- Stash apply 
  - You can use `git stash apply` to apply whatever is stashed away, without removing it from the stash. This can be useful if you want to apply stashed changes to multiple branch
- You can still get merge conflicts and then edit what you want to keep from the stash 

## Working With Multiple Stashes
- Stashing Multiple Times 
  - You can add multiple stashes onto the stack of stashes. They will all be stashed in the order you added them 
- Viewing stashes 
  - Run `git stash list` to view all stashes 
    - Gives us the most recent commit the changes were stashed on 
- Applying specific stashes 
  - Git assumes you want to apply the most recent stash when you run `git stash apply`, but you can also specify a particular stash like `git stash apply stash@{2}`

## Dropping & Clearing the Stash
- Dropping stashes 
  - To delete a particular stash, you can use `git stash <stash-id>` 
  - Apply doesn't drop things from the stash 
- Clearing the stash 
  - To clear out all stashes, run git stash clear 
- Do I really need this? 
  - 99% of the time, you'll just use git stash and git stash pop

## Stashing Exercise
- Completed Section Exercise on Stashing 