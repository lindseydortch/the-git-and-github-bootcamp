# Section 11: Github: The Basics

## What Really Matters In This Section
- Critical 
  - What Does Github do? 
  - Cloning 
  - Rsitering for Github & Setting Up SSH Keys 
  - Creating Github Repos 
  - Working with Remotes 
  - Git Push

## What Does Github Do For Us?
- What is Github? 
  - Github is a hosting platform for git repositories. You can put your own Git repos on Github and access them from anywhere and share them with people around the world. 
  - Beyond hosting repos, Github also provides additional collaboration features that are not native to Git (but are super useful). Basically, Github helps people share and collaborate on repos 
- Git vs Github 
  - Git 
    - Git is the version control software that runs locally on your machine. You don't need to register for an account. You don't need the internet to use it. You can use Git without ever touching Github 
  - Github 
    - Github is a service that hosts Git repositories in the cloud and makes it easier to collaborate with other people. You do not need to sign up for an account to use Github. It's an online place to share work that is done using Git. 
- What is great about pushing code to Github is that you can collaborate and make contributions 
- Github is not your only option...
  - There are tons of competing tools that provide similar hosting and collaboration features, including Gitlab, bitbucket, and Gerrit
- Github is very popular! 
  - Founded in 2008, Github is now the world's largest host of source code. In early 2020, Github reported having over 40 million users and over 190 million repositories on the platform 
- It's free! 
  - Github offers its basic servies for free! While Github does offer paid Team and Enterprise tiers, the basic Free tier allows for unlimited public and private rpos, unlimited collaborators and more 

## Why You Should Use Github!
- Why You should use github (or at least know how to use it)
  - Collaboration 
    - If you ever plan on working on a project with at least one other person, Github will make your life easier! Whether you're building a hobby project with your friend or you're collaborating with the entire world, Github is essential 
  - Open Source Projects 
    - Today Gtihub is THE home of open source projects on the internet. Projects ranging from React to Swift are hosted on Github 
    - If you plan on contributing to open source projects, you'll need to get comfortable working with Github
  - Exporsure 
    - Your Github profile showcases your own projects and contributions to others' project 
    - It can act as a sort of resume that many employers will consult during the hiring process. Additionally, you can gain some clout on the platform for creating or contributing to popular projects 
  - Stay up to date 
    - Being active on Github is the best way to stay up to date with projects and tools you rely on. Learn about upcoming changes and the decisions/ debate behind them 

## Cloning Github Repos With Git Clone
- Cloning 
  - So far we've created our own Git repositories from scratch, but often we want to get a local copy of an existing repository instead 
  - To do this, we can clone a remote repository hosted on Github or similar websites. All we need is a URL that we can tell Git to clone for use 
- git clone 
  - To clone a repo, simply run `git clone <url>` 
  - Git will retrive all the files associated with the repository and will copy them to your local machine 
  - In addition, Git initializes a new repository on your machine, giving you access to the full Git history of the cloned project 
  - Make sure you are not inside of a repo when you clone 

## Cloning Non-Github Repos
- Permissions?
  - Anyone can clone a repository from Github, provided the repo is public. You do not need to be an owner or collaborator to clone the repo locally to your machine. You just need the URL from Github 
  - Pushing your own changes to the Github repo... that's another story entirely! You need permission to do that! 

## Github Setup: SSH Config
- It's better if the email address you use on Git to be the same as Github 
- Configuring SSH Keys 
  - SSH keys 
    - You need to be authenticated on Github to do certain operations, like pushing code from your local machine. Your terminal will prompt you every single time for your Github email and password unless..
      - You generate and configure an SSH key! once configured, you can connect to Github without having to supply your username/password

## Creating Our First Github Repo!
- How Do I Get My Code On Github? 
  - Option 1: Existing Repo 
    - If you already have an existing repo locally that you want to get on Github...
      - Create a new repo on Github 
      - Connect your local repo (add a remote)
      - Push up your changes to Github 
  - Option 2: Start from Scratch 
    - If you haven't begun work on your local repo, you can 
      - Create a brand new repo on Github 
      - Clone it down to your machine 
      - Do some work locally 
      - Push up your changes to Github 

## A Crash Course on Git Remotes
- Remote 
  - Before we can push anything up to Github, we need to tell Git about our remote repository on Github. We need to setup a "destination" to push up to
  - In Git, we refer to these "destinations" as remotes. Each remote is simply a URL where a hosted repository lives 
- Viewing Remotes 
  - To view any existing remotes for your repository, we can run `git remote` or `git remote -v` (verbose, for more info)
  - This just displays a list of remots. If you haven't added any remotes yet, you won't see anything 
- Adding a New Remote 
  - A remote is really two things: a URL and a label 
  - To add a new remote, we need to provide both to Git 
  - `git remote add <name> <url>` 
  - Okay Git, anytime I use the name "origin", I'm referring to this particular Github repo URL 
- Origin? 
  - Origin is a conventional Git remote name, but it is not at all special. It's just a name for a URL 
  - When we clone a Github repo, the default remote name setup for us is called origin. You can change it. Most people leave it.
- Checking our work 
  - Try viewing your remotes with `git remote -v` and you should now see a remote showing up
  - Remember, by setting up a remote we are just telling Git about a remote repository URL. We have not "communicated" with the Github repo at all yet.  
- Other Commands 
  - They are not commonly used, but there are commands to rename and delete remotes if needed 
  - `git remote rename <old> <new>`
  - `git remote remove <name>`

## Introducing Git Push
- Pushing 
  - Now that we have a remote set up, let's push some work up to Github! To do this, we need to use the `git push` command.
  - We need to specify the remote we want to push up to AND the specific local branch we want to push up to that remote 
  - `git push <remote> <branch>`
- An Example 
  - `git push origin master` tells git to push up the master branch to our origin remote 
- You don't have to be on the branch to push it up 
- Reminder: we push up the entire branch, not just the commit 

## Touring a Github Repo
- You can see the differences in branches 
- You can see the most recent commit that effected a file 
- You can also see a visual representation of each commit and click in to see which files were committed 
  - You can also see the commit message and the hash 
  - You can leave comments on the commits 

## Practice With Git Push
- An example 
  - `git push origin master` tells git to push up the master branch to our origin remote 

## A Closer Look At Git Push
- Push In Detail 
  - While we often want to push a local branch up to a remote branch of the same name, we don't have to
  - To push our local pancake branch up to a remote branch called waffle we could do: `git push origin pancake:waffle`
  - `git push <remote> <local-branch>:<remote-branch>`

## What Does "git push -u" Mean?
- The -u option 
  - The -u option allow us to set the upstream of the branch we're pushing. You can think of this as a link connecting our local branch to a branch on Github 
  - Running `git push -u origin master` sets the upstream of the local master branch so that it tracks the master branch on the origin repo 
- What this means...
  - Once we've set the upstream for a branch, we can use the `git push` shorthand which will push our current branch to the upstream 
- `--set-upstream` is the same as using `-u`
- You can also use `-u` to set the upstream if you're using a different name for your branch in Github than on your local 

## Another Github Workflow: Cloning First
- Walkthrough of Option 2, to set up a Github repo 

## Main & Master: Github Default Branches
- As soon as you add one of the initial files in Github then it creates a branch of `main`  

## Github Basics Exercise
- Completed Section Exercise on Github Basics 