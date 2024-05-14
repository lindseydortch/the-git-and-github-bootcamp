# Section 5: Commits In Detail (And Related Topics)

## What Really Matters In This Section
- Critical 
  - Git ignore 
- Important
  - Writing Atomic Commits
  - Configuring Default Editor (Mac) 
  - Writing Good Commit Messages 
  - Navigating the Git Documentation 
- Nice to Have
  - Working With a GUI 
  - Amending Commits 

## Navigating the Git Documentation
- git.scm.com 
- The reference manual is a reference to all the git commands 
  - Gives us all the options we can use once we click into a command 
  - There are also examples provided 
- The book 
  - Split into topics and you can go and read more and has a clear path 
  - Good for configuring things 

## Keeping Your Commits Atomic
- Atomic Commits 
  - When possible, a commit should encompass a single feature, change or fix. In other words, try to keep each commit focused on a single thing. 
    - This makes it easier to undo or rollback changes later on. It also makes your code or project easier to review 

## Commit Messages: Present or Tense?
- Present-tense Imperative style?? 
  - From the Git docs: 
    - Describe your changes in imperative mood, e.g. "make xyzzy do frotz" instead of "[This patch] makes xyzzy to do frotz", as if you are giving orders to the codebase to change its behavior 
- It doesn't really matter, it just depends on the guidelines by the company or open source project you are working with 
- You do not have to follow this pattern 
  - Though the Git docs suggest using present-tense imperative messages, many developers prefer to use past-tense messages. All that matters is consistency, especially when working on a team with many people making commits 

## Escaping VIM & Configuring Git's Default Editor
- VIM is an editor built into the terminal 
  - `i` - enters insert mode 
    - Then you can start typing and leave a commit message 
  - `:wq` - save changes 
- Sometimes the -m doesn't cut it, sometimes you need a longer commit, so we want to configure VSCode as our editor 
  - Can be found here: `git config --global core.editor "code --wait"`
- You need to run `install code command in path` for VSCode to open from the terminal 

## A CLoser Look At the Git Log Command
- We will need the commit hashes later
- There are options we can set on git log 
  - You can filter out who worte the commit 
- We can format the commits 
  - `--pretty=oneline --abbrev-commit"
- Conventual to have the first line be a summary of the commit 

## Committing With a GUI
- You can choose the files you want to stage and then create your commit message 
- Pencil means - modified 
- + - means new file 

## Fixing Mistakes With Ammend
- Ammending Commits 
  - Supposed you just made a commit and then realized you forgot to include a file! Or maybe you made a typo in the commit message that you want to correct. 
    - Rather  than making a brand new separate commit, you can "redo" the previous commit using the --ammend option
  - You will do your commit then you need to stage what you forgot and then you can do git commit --ammend -- will open up in vscode 
    - You can just save the file and close it 
- If you want to remove files from a your most RECENT commit: 
  - `git rm <file>` - to delete the file and tell Git you deleted it 
  - `git commit --amend` - to redo the previous commit 

## Ignoring Files w/ .gitignore
- Ignoring Files 
  - We can tell Git which files and directories to ignore in a given repository, using a .gitignore file. This is useful for files you know you NEVER want to commit including: 
    - Secrets, API keys, credentials, etc. 
    - Operating System files (.DS_Store on Mac)
    - Log files 
    - Dependencies and packages
- .gitignore 
  - Create a file called .gitignore in the root of a repository. Inside the files & folders to ignore: 
    - `.DS_Store` will ignore files names .DS_Store 
    - `folderName/` will ignore an entire directory 
    - `*.log` - will ignore any files with the .log extension 
- gitignore.io -- will have a common enough files to ignore in whatever language you're working in 