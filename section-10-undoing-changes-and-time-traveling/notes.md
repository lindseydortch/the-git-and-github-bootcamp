# Section 10: Undoing Changes & Time Traveling

## What Really Matters In This Section
- Critical 
  - Checking out commits 
  - "Escaping" Detached HEAD 
- Important 
  - Discasrding changes with checkout
  - git reset 
  - git revert
- Nice to Have

## Checking Out Old Commits
- Undoing Stuff and Time Traveling 
- Checkout 
  - The `git checkout` command is like a Git Swiss Army Knife. Many developers think it is overloaded, which is what lead to the addition of the `git switch` and `git restore` commands. 
  - We can use `checkout` to create branches, switch to new branches, restore files, and undo history 
  - We can use `git checkout commit <commit-hash>` to view a previous commit 
  - Remember, you can use the `git log` command to view commit hashes. We just need the first 7 digits of a commit hash
  - Don't panic when you see the following message...
- Detached HEAD 
  - You're in a 'detached head' state. You can look around, make experimental changes and commit them and you can discard any commits you make in this state without impacting any branches by switching back to a branch 
- Usually, HEAD points to a specific branch reference rather than a particular commit 
- How it works 
  - HEAD is a pointer to the current branch reference 
  - The branch reference is a pointer to the last commit made on a particular branch 
- When we make a new commit, the branch reference is updated to reflect the new commit 
  - The HEAD remains the same, because it's pointing at the branch reference
- If we switch to the bugfix branch, HEAD is now pointing at the bugfix reference 
- This is all to say that HEAD usually refers to a branch NOT a specific commit 
- Back to this detached HEAD thing 
  - When we checkout a particular commit, HEAD points at that commit rather than at the branch pointer 
- Detached HEAD 
  - Don't panic when this happens! It's not a bad thing! 
  - You have a couple options: 
    - Stay in detached HEAD to examine the contents of the old commit. Poke around, view the files, etc.
    - Leave and go back to wherever you were before - reattach the HEAD 
    - Create a new branch and switch to it. You can now make and save changes, since HEAD is no longer detached

## Re-Attaching Our Detached HEAD!
- Detached HEAD 
  - Don't panic when this happens! It's not a bad thing! 
  - You have a couple options: 
    - Stay in detached HEAD to examine the contents of the old commit. Poke around, view the files, etc.
    - Leave and go back to wherever you were before - reattach the HEAD 
    - Create a new branch and switch to it. You can now make and save changes, since HEAD is no longer detached
- If you checkout an old commit and decide you want to return to where you were before 
  - Simply switch back to whatever branch you were on before (master in this example)
  - `git checkout master` or `git switch master`

## Referencing Commits Relative to HEAD
- Checkout 
  - `git checkout` supports a sightly odd syntax for referencing previous commits relative to a particular commit 
  - HEAD~1 refers to the commit before HEAD (parent)
  - HEAD~2 refers to 2 commits before HEAD(grandparent)
  - This is not essential, but if I wanted to mention it because it's quite weird looking if you've never seen it 
- To get back to the branch you were on 
  - `git switch -`

## Discarding Changes With Git Checkout
- Discarding Changes 
  - Supposed you've made some changes to a file, but don't want to keep them. To revert the file back to whatever it looked like when you last comitted, you can use: 
    - `git checkout HEAD <filename>` to discard any changes in that file, reverting back to the HEAD -- back to where we last committed 

## Un-Modifying With Git Restore
- Another Option  
  - Here's another shorter option to revert a file...
  - Rather than typing HEAD, you can substitute `--` followed by the file(s) you want to restore 
  - `git checkout -- <file>`

## Un-Staging Changes With Git Restore
- Restore 
  - `git restore` is a brand new Git command that helps with undoing operations 
  - Because it is so new, most of the existing Git tutorials and books do not mention it, but it is worth knowing 
  - Recall that `git checkout` does a million different thngs, which many git users find very confusing. `git restore` was introduced alongside `git switch` as alternatives to some of the uses for `checkout`
- Unmodifying Files with Restore 
  - Supposed you've made some changes to a file since your last commit. You've saved the file, but then realize you definitely do NOT want those changes anymore! 
  - To restore the file to the contents in the HEAD, use `git restore <filename>` 
    - NOTE: the above command is not "undoable". If you have uncommitted changes in the file, they will be lost 
- Unmodifying Files with Restore 
  - `git restore <file-name>` restores using HEAD as the default source, but we can change that using the `--source` option 
  - For example, `git restore --source HEAD~1 home.html` will restore the contents of home.html to its state from the commit prior to HEAD. You can also use a particular commit hash as the source 
  - Can also use a commit hash isntead of `HEAD~1`

## Undoing Commits With Git Reset
- Unstaging File with Restore 
  - If you have accidentally added a file to your staging area with `git add` and you don't wish to include it in the next commit, you can use `git restore` to remove it from staging 
  - Use the `--staged` option like this: 
    - `git restore --staged <filename>`
- Feeling Confused? 
  - `git status` reminds you what to use 

## Undoing Commits With... Git Revert
- Git Reset 
  - Supposed you've just made a couple of commits on the master branch, but you actually meant to make them on a separate branch instead. To undo these commits, you can use `git reset`
  - `git reset <commit-hash>` will reset the repo back to a specific commit. The commits are gone 
  - The changes stay in your working directory 
- Oh No! I didn't mean to make that commit here! 
  - Working Directory 
  - Staging Area 
  - Repository 
    - 39c3fdd 
      - modified about.html 
      - created lisa.jpg 
    - 00267739
    - bb43f1f
- git reset 00267739
  - Working Directory 
    - modified about.html 
    - created lisa.jpg 
  - Staging Area 
  - Repository 
    - 00267739 
    - bb43f1f
- You don't lose your work, you lose your commits 
- Reset --hard 
  - If you want to undo both the commits AND the actual changes in your files, you can use the `--hard` option 
  - For example, `git reset --hard HEAD~1` will delete the last commit and associated changes 
- Oh No! I don't want that commit OR the changes 
  - Working Directory 
  - Staging Area 
  - Repository 
    - 39c3fdd 
      - modified about.html 
      - created lisa.jpg 
    - 00267739
    - bb43f1f
- git reset --hard 00267739
  - Working Directory 
    - The changes in the file(s) are gone too! 
  - Staging Area 
  - Repository 
    - Commit(s) are gone 
    - 00267739 
    - bb43f1f
- These are on a per branch basis 

## Reverting Commits With...Git Revert 
- git revert 
  - Yet another similar sounding and confusing command that has to do with undoing changes 
- Git Revert 
  - `git revert` is similar to `git reset` in that they both "undo" changes, but they accomplush it in different ways 
  - `git reset` actually moves the branch pointer backwards, eliminating commits 
  - `git revert` instead creates a brand new commit which reverses/undoes the changes from a commit. Because it will result in a new commit you will be prompted to enter a commit message 
  - `git revert <commit-hash>`
- Which one should I use? 
  - Both `git reset` and `git revert` help us reverse changes, but there is a significant difference when it comes to collaboration (which we have yet to discuss but is coming up soon)
  - If you want to reverse some commits that other people already have on their machines, you should use revert 
  - If you want to reverse commits that you haven't shared with others, use reset and no one will ever know 
- Doesn't alter history 
- Revert can also result in conflicts, you still have to go in and resolve manually 

## Undoing Changes Exercise
- Completed Section Exercise on Undoing Changes 