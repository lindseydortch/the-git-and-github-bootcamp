# Section 4: The Very Basics of Git: Adding & Committing

## What Really Matters In This Section
- Critical 
  - What are git repos? 
  - Git init 
  - Git status 
  - The Committing workflow 
  - Git add 
  - Git commit 
  - Git Log 
- Important 
  - Understanding the .git folder 

## What Is A Git Repo?
- A quick high-level conceptual overview 
  - Repository 
    - A git 'repo' is a workspace which tracks and manages files within a folder 
      - Anytime we want to use Git with a project, app, etc. we need to create a new git repository. We can have as many repos on our machine as needed, all with separate histories and contents 

## Our First Commands: Git Init and Git Status
- Our Very First Git Command 
  - `git status` gives information on the current status of a git repository and its contents 
    - It's very useful, but at the moemnt we don't actually have any repos to check the status of 
- Use `git init` to create a new git repository
  - Before we can do anything git related, we must initialize a repo first 
  - This is something you do once per project. Initialize the repo in the top-level folder containing your project 

## The Mysterious .Git Folder
- Creates a folder .git when a repo is initialized 
  - If you delete this folder, your git history is gone 

## A Common Early Git Mistake
- Git tracks a directory and all nested subdirectories 
  - It's top-down 
  - We do not want to initialize another repo inside an existing repo 
- Do Not init a repo inside of a repo 
  - Before running `git init`, use `git status` to verify that you are not currently inside of a repo 
- Don't put a git repo on your entire machine 

## The Committing Workflow Overview
- Committing - the most important feature 
  - I start a new project -> add a checkpoint
    - Initialize project -> Add top navbar -> add first row -> change to dark theme 
  - A commit is a checkpoint 
- Commits are not the same as saving a file 
  - We have to save first and then commit our changes as a group 
- The Basic Git Workflow 
  - Work on Stuff 
    - make new files, edit files, delete files, etc
  - Add changes 
    - Group specific changes together, in preparation of committing 
  - Commit 
    - Commit everything that was previously added
- Example: I made changes in 7 different files this morning 
  - You can group together 3 files and commit with add branded navbar 
- Working directory -- git add --> staging area -- git commit --> repo 

## Staging Changes With Git Add
- Working directory 
  - Where we're actually working on our project 
- Repository 
  - This is the .git folder 
  - .git gets updated when we make changes 
- Staging area
  - This is where we add our changes before we make a commit 
- Adding 
  - Use `git add` to add specific files to the staging area. Separate files with spaces to add multiple at once 

## Finally, the Git Commit Command!
- Git commit 
  - We use the `git commit` command to actually commit changes from the staging area 
    - When making a commit, we need to provide a commit message that summarizes the changes and work snapshotted in the commit 
  - Running `git commit` will commit all staged changes. It also opens up a text editor and prompts you for a commit message. 
  - The -m flag allows us to pass in an inline commit message, rather than launching a text editor

## The Git Log Command (And More Committing)
- modified - git knows about it and says, 'hey you changed a file'
- untracked - means you haven't staged that file yet and it's not really tracking the changes
- git log - doesn't do anything, but it does retrieve a log of commits 
- `git add .` - stages all changes 

## Committing Exercise
- Completed exercise for section 