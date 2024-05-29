# Section 16: Cleaning Up History With Interactive Rebase

## What Really Matters In This Section
- Nice To Have
  - Rewording Commits 
  - Fixing Up/ Squashing Commits 
  - Dropping Commits 

## Introducing Interactive Rebase
- Rewriting History 
  - Sometimes we want to rewrite, delete, rename, or even reorder commits (before sharing them), we can do this using `git rebase`
- Interactive Rebase 
  - Running git rebase with the `-i` option will enter the interactive mode, which allows us to edit commits, add files, drop commits, etc. Note that we need to specify how far back we want to rewrite commits. 
  - Also, notice that we are not rebasing onto another branch. Instead, we are rebasing a series of commits onto the HEAD they currently are based on 
  - `git rebase -i HEAD~4`

## Rewording Commits With Interactive Rebase
- We will basically be combining commits that are similar, for instance, you added bootstrap to your file and then forgot to add the JS file for bootstrap, so you have another commit for that, so you want to combine those into one commit instead of two 
- What Now? 
  - In our text editor, we'll see a list of commits alongside a list of commands that we can choose from. Here are a couple of the more commonly used commands: 
    - pick - use the commit 
    - reword - use the commit, but edit the commit message 
    - edit - use commit, but stop for ammending 
    - fixup - use commit contents but meld it into previous commit and discard the commit message 
    - drop - remove commit 
  - You will see oldest commit first and newest last -- starts at the beginning of the sub-section of commits we selected 
  - Once you save after updating the action you want to do, it will open that commit in your editor 
  - Every commit is rehashed after the one we changed 

## Fixing Up & Squashing Commits With Interactive Rebase
- We can use fixup to drop the commit message, squash keeps the old commit message 

## Dropping Commits With Interactive Rebase
- To edit the most recent commit you can do `git commit --amend` 