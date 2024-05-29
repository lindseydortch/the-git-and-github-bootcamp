# Section 14: Git Collaboration Workflows

## What Really Matters In This Section
- Critical 
  - The problems with working on a single branch 
  - Feature Branch Workflow 
  - Pull Requests 
  - Forking 
  - Fork-And-Clone Workflow 
- Important 
  - Branch Protection Rules 

## The Pitfalls of a Centralized Workflow
- Centralized Workflow 
  - AKA everyone works on Master/Main AKA the most basic workflow possible 
  - The simplest collaborative workflow is to have everyone work on the master branch (or main, or any other SINGLE branch)
  - It's straightforward and can work for tiny teams, but it has quite a few shortcomings 
- Repository Example 
  - Pamela clones the repo 
  - David clones the repo 
  - Forest clones the repo 
  - Forrect gets to work on a new feature! Adding and committing all day long! 
  - Forest now pushes up his new work to Github 
  - Pamela has also been hard at work on her own new feature 
    - She tries to push her new work up to Github, but she runs into trouble! 
      - Failed to push. Updates were rejected because the tip of your current branch is behind its remote counterpart. Merge the remote changes (e.g. git pull) before pushing again 
    - So she pulls to get the changes from origin master 
    - Forrest's work must be merged in. hopefully this goes relatively smoothly! 
  - Now that she has merged the latest work from Github, she can push her master branch up! 
  - David working on a new features, but is having some doubts. He'd like to share his commits with the rest of the team to start a discussion 
    - Before he can even share these iffy commits, he has to pull from Github and merge them into master 
    - Now he can finally push his work up to Github. His teammates can pull to get his new commits. 
- The problem 
  - While it's nice and easy to only work on the master branch, this leads to some serious issues on teams! 
    - Lots of time spent resolving conflicts and merging code, especially as team size scales up 
    - No one can work on anything without disturbing the main codebase. How do you try adding something radically different in? How do you experiment? 
    - The only way to collaborate on a feature together with another teammate is to push incomplete code to master. Other teammates now have broken code... 

## Centralized Workflow Demonstration
- Demonstration of a Centralized Workflow 

## The All-Important Feature Branch Workflow
- Enter Feature Branches - Don't work on master 
- Feature branches 
  - Rather than working directly on master/main, all new development should be done on separate branches! 
    - Treat master/main branch as the official project history 
    - Multiple teammates can collaborate on a single feature and share code back and forth without polluting the master / main branch 
    - Master/ Main branch won't contain broken code (or at least, it won't unless someone messes up)
- Workflow Example 
  - Everyone clones the repo 
  - David starts work on a new feature. He does all this work on a separate branch 
  - David wants Pamela to take a look at his new feature. Instead of merging it into master, he just pushes his feature branch up to Github 
  - Pamela is hard at work on her own feature. Just like everyone else, she's working on a separate feature branch rather than master 
  - Pamela hears from David that he wants her to take a look at his new work. She pulls down his feature branch from Github. 
  - Pamela takes a look at the code and makes a couple improvements of her own. She adds/ commits on the same feature branch 
  - Pamela pushes up her new work on the add-dark-theme feature branch so that David can pull them down 
  - David returns to work the next morning. After an hour on reddit he decides he should actually do some work 
  - David fetches from Github and sees that there is new work on the add-dark-theme branch. He pulls the changes down and continues work 
  - David decides he is happy with the new feature, so he merges it into master 
    - *At a real company, you don't just decide you are "happy with" a feature. There are mechanisms for code approval and merging we'll discuss shortly!
  - David pushes up the updated master branch to Github. The others can now pull down the changes 

## Feature Branch Workflow Demo
- Demonstration on a Feature Branch Workflow

## Merging Feature Branches
- Merging in Feature Branches 
  - At some point the new work on feature branches need to be merged in to the master branch! There are a couple of options for how to do this...
    - Merge at will, without any sort of discussion with teammates. JUST DO IT WHENEVER YOU WANT 
    - Send an email or chat message or something to your team to discuss if the changes should be merged in 
    - Pull requests 

## Introducing Pull Requests
- Pull requests 
  - Pull requests are a feature built in to products like Github and Bitbucket. They are not native to Git itself. 
  - They allow developers to alert team-members to new work that needs to be reviewed. They provide a mechanism to approve or reject the work on a given branch. They also help facilitate discussion and feedback on the specified commits 
  - "I have this new stuff I want to merge in to the master branch... what do you all think about it?"
- The workflow 
  - Do some work locally on a feature branch 
  - Push up the feature branch to Github 
  - Open a pull request using the feature branch just pushed up to Github 
  - Wait for the PR to be approved and merged. Start a discussion on the PR. This part depends on the team structure.
- Example 
  - I push my feature branch up to Github, so that I can open a Pull Reuqest 
  - Go on Github and click Compare & Pull request or Pull request 
  - My Boss's Github...
    - My boss leaves some feedback to me. She asks me to make a couple changes before she merges the pull request
  - I can respond! We can discuss and give feedback! 
  - Once I make the requested changes, my boss (or whoever is in charge of merging) can merge in my pull request 
- There is a section on every repository with pull requests 
  - The structure of the pull request depends on the organization 

## Making Our First Pull Request
- Demonstration on creating a Pull Request in Github 

## Merging Pull Requests With Conflicts
- Just like any other merge, sometimes there are conflicts that need to be resolved when merging a pull request. This is fine. Don't panic. 
- You can perform the merge and fix the conflicts on the command line like normal, or you can use Gtihub's interactive editor
- You can resolve conflicts through Github or you can resolve them on your own machine 
  - To resolve on your own machine, you select "Checkout via command line"
- --no-ff -- tells git merge to not fast forward if it sees that it can 
- My Boss's Local Machine 
  - My boss can merge the branch and resolve conflicts locally 
    - Switch to the branch in questions. Merge in master and resolve the conflicts. 
    - Switch to master. Merge in the feature branch (now with no conflicts). Push changes up to Github 

## Configuring Branch Protection Rules
- Go into settings -> Brnaches 
  - You can change the default branch 
  - You can add branch protection rules under branch protection rule 
- Brand protection rule 
  - You can add a branch name pattern 
  - Require pull request reviews before merging -- requires your pull request to be approved before it can be merged 
  - There's a bunch of protections you can set up depending on the level of your Github account 

## Introducing Forking
- Fork & Clone: Another Workflow 
  - The "fork & clone" workflow is different from anything we've seen so far. Instead of just one centralized Github repository, every developer has their own Github repository in addition to the "main" repo. Developers make changes and push their own forks before making pull requests. 
  - It's very commonly used on large open-source projects where there may be thousands of contributors with only a couple maintainers 
- Forking 
  - Github (and similar tools) allow us to create personal copies of other peoples' repositories. We call those copies a "fork" of the original 
  - When we fork a repo, we're basically asking Github "Make me my own copy of this repo please" 
  - As with pull requests, forking is not a Git feature. The ability to fork is implemented by Github. 

## Forking Demonstration
- Demonstration on forking a repo from Github 
  - You can add collaborators to your forks 

## The Fork & Clone Workflow
- Now what? 
  - Now that I've forked, I have my very own copy of the repo where I can do whatever I want! 
  - I can clone my fork and make changes, add features, and break things without fear of disturbing the original repository. 
  - If I do want to share my work, I can make a pull request from my fork to the original repo 
- Example 
  - Pamela is ahrd at work on her own new feature. Just like everyone else, she's working on a separate feature branch rather than master 
  - The official project repo 
    - My fork - Taylor's Fork - Lupe's Fork 
  - My local machine 
    - I make a clone of my forked repository so that I can start working on it locally
    - When we clone a repo, Git automatically adds a remote called `origin` that points to our forked repo on Github  
    - Next, I add a remote pointing to the original prokect repo (NOT the fork). The remote can be named anything, but you'll often see "upstream" or "original" used 
      - This allows you to pull down the original repo 
    - I do some work locally. Normally, I would work on a feature branch, but only to keep the diagrams simpler I'm not going to 
    - To share my changes with others, I cannot push to upstream. I don't have permission! But I can push to origin (my Github fork)
  - Github 
    - Next, I can make a pull request from my fork on Github to the original project repository 
    - Now I wait to hear from the project maintainers! Do they want me to make further changes? It turns out they accept and merge my pull request! 
    - The next day, I get back to work. The official project repo now contains work done by other collaborators. I don't have their new work on my machine, I'm behind 
  - My Local Machine 
    - All I need to do is pull from upstream (the original repo) to get the latest changes in my local repo 
- An Even Briefer Summary 
  - Fork the project 
  - Clone the fork 
  - Add upstream remote 
  - Do some work 
  - Push to origin 
  - Open PR 
- Fork & Clone 
  - This "Fork & Clone" workflow might seem complicated, but it's extremely common for good reason! 
  - It allows a project maintainer to accept contributions from developers all around the world without having to add them as actual owners of the main project repository or worry about giving them all permissions to push to the repo (which could be disastrous!)

## Fork & Clone Workflow Demonstration
- Demonstration of the Fork & Clone Workflow 