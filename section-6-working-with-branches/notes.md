# Section 6: Working With Branches

## What Really Matters In This Section
- Critical 
  - Branching.. what is it? why use it? 
  - Understanding Git HEAD 
  - Git Branch 
  - Git Switch 
  - Git Checkout 
- Important 
  - Deleting & Renaming Branches 
  - Master vs. Main Branch 
- Nice to Have
  - HEAD & Refs Behind the Scenes 

## Introducing Branches
- Git Branching 
  - When we make a commit, each commit gets a unique hash an references at least one parent commit that came before it 
- Contexts 
  - On large projects, we often work in multiple contexts: 
    - You're working onb 2 different color scheme variations for your website at the same time, unsure of which you like best 
    - You're also trying to fix a horrible bug, but it's proving tough to solve. You need to really hunt around and toggle some code on and off to figure it out 
    - A teammate is also working on adding a new chat widget to present at the next meeting. It's unclear if your company will end up using it 
    - Another coworker is updating the search bar autocomplete 
    - Another developer is doing an experimental radical design overhaul of the entire layout to present next month 
- Branches 
  - Branches are an essential part of Git! 
  - Think of branches as alternative timelines for a project 
  - They enable us to create separate contexts where we can try new things, or even work on multiple ideas in parallel 
  - If we make changes on one branch, they do not impact the other branches (unless we merge the changes)

## The Master Branch (Or Is It Main?)
- In git we are always working with a branch 
- The Master Branch
  - In git, we are always working on a branch
    - The default branch name is master
  - It doesn't do anything special or have fancy powers. It's just like any other branch 
- Master 
  - Many people designate the master branch as their "source of trith" of the "official branch" for their codebase, but that is left for you to decide 
  - From Git's perspective, the master branch is just like any other branch. It does not have to hold the "master copy" of your project 
- Master? Main? 
  - In 2020, Github renamed the default branch from amster to main. The default Git branch name is still master, though the Git team is exploring a potential change
- Branching 
  - Master Branch  
    - Commit --> Commit --> Feature Branch (commit --> commit) --> merge to master 

## What On Earth Is HEAD?
- HEAD
  - We'll often com across the term HEAD in Git
  - Head is simply a pointer that refers tot the current "location" in your repository. It points to a particular branch reference 
  - So far, HEAD always points to the latest commmit you made on the master branch, but soon we'll see that we can move around and HEAD will change 
- Think of a book with three different bookmarks and the book can only be open to one point in time 
- Tip is the latest commmit 
- See class diagram's for visual representation 
- (Main --> Commit) <-- HEAD 
- The HEAD changes based on the commits 
- A branch is just a reference to a commit 

## Viewing All Branches With Git Branch
- Viewing branches 
  - Use `git branch` to view your branches, The defualt branch in every git repo is master, though you can configure this 
  - Look for the * which indicates the branch you are currently on 

## Creating & Switching Branches
- Creating Branches 
  - Use `git branch <branch-name>` to make a new branch based upon the current HEAD 
  - This just creates the branch. It does not switch you to that branch (the HEAD stays the same)
- Switching Branches 
  - Once you have created a new branch, use `git switch <branch-name>` to switch to it
- Git log will show our head for our current branch and then the commit where our master head is pointing to  

## More Practice With Branching
- Where HEAD is makes an impacts the branch that we create 
- `git commit -a -m` - adding all unstaged changes to a commit 

## Another Option: Git Checkout vs. Git Switch
- Another way of switching 
  - Historically we used `git checkout <brnach-name>` to switch branches, this still works 
  - The checkout command does a million additional things, so the decision was made to add a standalone switch command which is much simpler 
  - You will see older tutorials and docs using checkout rather than switch, both now work 
- Creating & switching 
  - Use `git switch` with the `-c` flag to create a new branch and switch to it all in one go 
    - Remember -c as short for "create"
    - `git swtich -c <branch-nanme>` 
- Even though the demo included one file, branches are not limited to updating just one file or folder 

## Switching Branches With Unstaged Changes?
- You need to commit or stash before switching to a new branch or else you will get an error if the file existed in another branch 
  - This file that was created will come with you to a new branch 
  - It is recommended to add and commit changes when you switch branches 

## Deleting & Renaming Branches
- `git branch -d <branch-name>` - deletes a branch 
  - Branch needs to be fully merged 
  - To delete without fully merging 
    - `git branch -D <branch-name>`
- `git branch -m <new-branch>` - to rename a branch, need to be on the branch you are trying to rename

## How Git Stores HEAD & Branches
- Inside of .git we get a file called HEAD 
  - This shows `ref: refs/heads/master`
- `cat`- to look inside file 
- Every branch has a file and there is just a pointer to a particular commit -- each one of these is like a bookmark 

## Branching Exercise
- Completed Section Exercise on Branching 