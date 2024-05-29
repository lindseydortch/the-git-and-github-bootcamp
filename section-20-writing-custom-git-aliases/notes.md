# Section 20: Writing Custom Git Aliases

## What Matters In This Section
- Important 
  - The Global Config Gile 
- Nice to Have
  - Writing Basic Aliases 

## The Global Git Config File
- Global Git Config 
  - Git looks for the global config file at either `~/.gitconfig` or `~/.config/git/config`. Any configuration variables that we change in the file will be applied across all Git repos 
  - We can also alter configuration variables from the command line if preferred 
  - There is also a system-wide file, but not commonly used, usually used for if more than one user is using the computer 

## Writing Our First Git Alias
- Adding Aliases 
  - We can easily set up Git aliases to make our Git experience a bit simpler and faster 
  - For example, we could define an alias "git ci" instead of gaving to type "git commit"
  - Or we could define a custom `git lg` command that prints out a custom formatted commit log 
- You don't have to write out git, you still have to type it in the terminal 

## Setting Aliases From the Command Line
- `git config --global alias.showmebranches branch` 

## Aliases With Arguments
- Git will just depend whatever we need to the end 

## Exploring Existing Useful Aliases Online
- Check out the resources tab for articles on useful and popular git aliases 
  - Used in lecture 
    - ll 
    - ls 
    - la
- If you use aliases just remember it's set up for your machine 