# Section 12: Fetching & Pulling

## What Really Matters In This Section
- Critical 
  - Remote Tracking Branches 
  - Git Fetch 
  - Git Pull 

## Remote Tracking Branches: WTF Are They?
- A Closer Look at Cloning 
  - Github Repo with commits -- git clone --> My Computer 
    - My computer 
      - A regular reference. I can move this around myself 
      - origin/master
        - This is a "Remote Tracking Branch". It's a reference to the state of the master branch on the remote. I can't move this myself. It's like a bookmark pointing to the last known commit on the master branch on origin 
- Remote Tracking Branches 
  - "At the time you last communicated with this remote repository, here is where x branch was pointing" 
  - They follow this pattern <remote>/<branch>
    - origin/master references the state of the master branch on the remote repo named origin 
    - upstream/logoRedesign references the state of the logoRedesign branch on the remote named upstream (a common remote name)
- Remote Branches 
  - Run `git branch -r` to view the remote branches our local repository knows about 

## Checking Out Remote Tracking Branches
- My computer 
  - I make a new commit locally. My master branch reference updates, like always 
    - The remote reference stays the same 
  - I make another commit, and the local branch reference moves again 
    - Remote reference doesn't move 
- `git status` will also show you how far ahead you are of the remote repo 
  - Then you can checkout remote branch pointers 
- You can checkout these remote branch pointers 
  - `git checkout origin master`
  - Detached HEAD! Don't panic. It's fine

## Working With Remote Branches
- Supposed I just cloned a Github Repo 
- Remote Branches 
  - Once you've cloned a repository, we have all the data and Git history for the project at that moment in time. However, that does not mean it's all in my workspace 
  - The Github repo has a branch called 'puppies', but when I run `git branch` I don't see it on my machine, all I see is the master branch? What's going on?
- Workspace --> Remote 
  - Workspace 
    - master
    - By default, my master branch is already tracking origin/master 
    - I didn't connect these myself 
  - Remote 
    - origin/master 
    - origin/puppies 
- I want to work on the puppies branch locally! 
  - I could checkout 'origin/puppies' but that puts me in detached HEAD 
  - I want my own local branch called puppies, and I want it to be connected to 'origin/puppies', just like my local master branch is connect to 'origin/master'
- It's super easy! 
  - Run `git switch <remote-branch-name>` to create a new local branch from the remote branch of the same name 
  - `git switch puppies` makes me a local puppies branch AND sets it up to track the remote branch 'origin/puppies'
- NOTE! 
  - The new command `git switch` makes this super easy to do! It used to be slightly more complicated using `git checkout`
  - `git checkout --track origin/puppies`

## Git Fetch: The Basics
- Github 
  - Uh oh! The remote repo has changed! A teammate ha pushed up changed to the master branch, but my local repo doesn't know
    - How do I get those changes? 
- Local
  - I've also made a commit to the master branch on my computer 
- Workspace -- git add --> Staging (index) -- git commit --> Local repository -- git push --> Remote repository 
- Remote Repository -- git fetch --> local repository -- git pull --> Local, Staging, Workspace 
- Fetching 
  - Fetching allows us to download changes from a remote repository, BUT those changes will not be automatically integrated into our working files
  - It lets you see what others have been working on, without having to merge those changes into your local repo 
  - Think of it as "please go and get the latest information from Github, but don't screw up my working directory"
- git fetch 
  - The `git fetch <remote>` command fetches branches and history from a specific remote repositroy. It only updates remote tracking branches 
  - `git fetch origin` would fetch all changes from the origin remote repository 
    - If not specified, <remote> defaults to origin 
  - We can also fetch a specific branch from a remote using `git fetch <remote> <branch>` 
  - For example, `git fetch origin mster` would retrieve the latest information from the master branch on the origin remote repository 

## Demonstrating Git Fetch
- You have to tell git that you need the changes because it is not constantly asking Github for the changes, this is why `git fetch` is important 
  - You can see if you're behind by using `git status` 

## Git Pull: The Basics
- Pulling 
  - `git pull` is another command we can use to retrive changes from a remote repository. Unlike fetch, pull actually updates our HEAD branch with whatever changes are retreived from the remote 
  - "go and download data from Github AND immediately update my local repo with those changes" 
- git pull = git fetch (update the remote tracking branch with the latest changes from the remote repository) + git merge (update my current branch with whatever changes are on the remote tracking branch)
- git pull 
  - To pull, we specify the particular remote and branch we want to pull using `git pull <remote> <branch>`. Just like with git merge, it matters WHERE we run this command from. Whatever branch we run it from is where the changes will be merged into 
  - `git pull origin master` would fetch the latest information from the origin's master branch and merge those changes into our current branch 

## Git Pull & Merge Conflicts
- Pulls can result in merge conflicts 
  - I now have the latest commits from 'origin/master' on my local master branch (assuming I pulled while on my master branch)
- When you pull it will tell you it couldn't auto-merge and then you can go in and fix the merge conflicts and then you can commit and push up 
- I have a commit locally that is not on Gtihub. When I pulled, it was merged with the new commits. As with any other merge, this can result in merge conflicts 

## A Shorter Syntax For Git Pull?
- An even easier syntax! 
  - It we run `git pull` without specifying a particular remote or branch to pull from, git assumes the following: 
    - remote will refault to origin 
    - branch will default to whatever tracking connection is configured for your current branch 
  - Note: this behavior can be configured, and tracking connections can be changed manually. Most people don't mess with that stuff 
- When I'm on my local master branch ... git pull - pulls from origin/master automatically 
  - When I'm on my local puppies branch ... git pull - pulls from origin/puppies automatically
- git fetch 
  - Gets changes from remote branch(es) 
  - Updates the remote-tracking branches with the new changes 
  - Does not merge changes onto your current HEAD branch 
  - Safe to do at any time 
- git pull 
  - Gets changes from remote branch(es) 
  - Updates the current branch with the new changes, merging them in 
  - Can result in merge conflicts 
  - Not recommended if you have uncommitted changes 