# Section 15: Rebasing: The Scariest Git Command?

## What Really Matters In This Section
- Important 
  - Rebasing vs. Merging 
  - Git Rebase Basics 
  - When NOT to Rebase 

## Why Is Rebasing Scary? Is it?
- Rebasing 
  - When I first learned Git, I was told to avoid rebasing at all costs. 
    - It can really mess things up 
    - It's not for beginners 
  - So Colt avoided the git rebase command for YEARS! 
  - It's actually very usefule, as long as you know when NOT to use it! 
  - There are two maun ways to use the git rebase command: 
    - as an alternative to merging 
    - as a cleanup tool 

## Comparing Merging & Rebasing
- I'm working on a collaborative project 
  - I make a new feature branch 
  - I do some work on the branch 
  - I do some more work 
  - Master has new work on it! 
    - My feature branch doesn't have this work 
  - I merge master into feature 
    - This results in a new merge commit 
  - I keep working on my feature branch 
  - A coworker adds new work to master 
  - I merge master into my feature branch 
    - This results in yet another merge commit 
  - The feature branch has a bunch of merge commits. If the master branch is very active, my feature branch's history is muddied 
- Rebasing 
  - We can instead rebase the feature branch onto the master branch. This moves the entire feature branch so that it BEGINS at the tip of the master branch. All of the work is still there, but we have re-written history
  - Instead of using a merge commit, rebasing rewrites history by creating new commits for each of the original feature branch commits 
  - `git switch feature`
  - `git rebase master` 
  - We can also wait until we are done with a feature and then rebase the feature branch onto the master branch 

## Rebase Demo Pt. 1: Setup & Merging
- Walkthrough of the first part of the diagram where we do some work and then merge master into our branch 

## Rebasing Demo Pt. 2: Actually Rebasing
- Git rebase re-creates new commits 
- This won't screw up the master branch, it re-bases them to the tip of the master branch, this helps us end up with a linear structure 
- You can also rebase instead of merging 
- It removes our merge commits and our commit hashes actually change 
- Cleans up your history and makes it easier to see what you've done and the commits you've made on that branch 
- Moves our feature branch commit onto the top of the master branch head commit 
- You can rebase instead of merge 

## The Golden Rule: When NOT to Rebase
- Why rebase? 
  - We get a much cleaner project history. No unnecessary merge commits! We end up with a linear project history 
- WARNING!
  - Never rebase commits that been shared with others. If you have already pushed commits up to Github... DO NOT rebase them unless you are positive no one on the team is using those commits.
- SERIOUSLY! 
  - You do not want to rewrite any git history that other people already have. It's a pain to reconcile the alternate histories! 

## Handling Conflicts & Rebasing
- You can end up with conflicts just like when we merge 
- You have the options to: 
  - Abort the rebase 
  - Resolve the conflicts manually 
  - You can also skip a certain commit 
- Git will provide you with help if you run into this 