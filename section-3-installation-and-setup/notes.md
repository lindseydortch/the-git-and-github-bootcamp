# Section 3: Installation & Setup

## What Really Matters In This Section
- Critical 
  - The different ways of interacting with Git: command line and GUIs 
  - Installing Git 
  - Configuring Your Git Name & email 
  - Terminal Crash Course Videos 
- Important 
  - GitKraken 

## Installing Git: Terminal Vs. GUIs
- Git is (primarily) a terminal tool 
  - Git was created as command-line tool. To use it, we run various git commands in a Unix shell. This is not the most user firendly experience, but it's at the very core of git! 
- The rise of GUI's 
  - Over the last few years, companies have created graphical user interfaces for Git that allow people to use Git without having to be a command-line expert 
  - Popular Git GUI's include: 
    - Github desktop 
    - SourceTree 
    - Tower 
    - GitKraken 
    - Ungit 
- GUI Clients Pros and cons 
  - Pros 
    - Way lower barrier-of-entry for beginners compared to the command-line 
    - Friendlier to use. Can be much better experience (when it works)
    - Some people prefer the visual experience, even those who can use the command line 
  - Cons 
    - At times, there is lots of "magic" involced. The inner-workings of Git are obfuscated and hidden away with GUIs
    - Often leads to dependence on a particular piece of software 
    - When things go seriously wrong, it can be ery challneging to fix without the commnad-line 
    - The interfaces, buttons and menus vary between different GUIs
- The Command Line Pros and Cons 
  - Pros 
    - Git is a command-line tool. All the documentation and resources online will refer to the command-line 
    - The command-line can be way faster once you get comfortable with it 
    - Some of the more advanced Git features are only available on the command-line 
    - The commands are always the same, no matter what machine you are on 
  - Cons 
    - Not begginer-friendly. Can be difficult to learn and remember the commands at first 
    - Even for some practiced users, the command-line interface is just not a good experience. It's really a matter of preference 
- Installing a GUI 
  - There are many options to choose from dpeending on your operating system, and most of them are incredibly simple to install 

## WINDOWS Git Installation
- Walkthrough of how to install Git on a Windows machine 

## MAC Git Installation
- Most macs come with Git built in, but you need to install git for some of the more up to date features that may not be installed 
- Do the binary installer 

## Configuring Your Git Name & Email
- Configuring Git 
  - Now that Git is hopefully installed, it's time to configure some basic information. You do not need to register for an account or anything, but you will need to provide: 
    - Your name 
    - Your email 
  - If you are using a GUI it should prompt you for your name and email the first time you open the app 
- Configuring Git 
  - Yo configure the name that Git will associate with your work, run this command: 
    - `git config --global user.name "Lindsey Dortch"` 
    - To check if you already have a name 
      - `git config user.name`
  - Do the same for email 
    - When we get to Github, you'll want your Git email address to match your Github account 
      - `git config --global user.email email@email.com`

## Installing GitKraken (Our GUI)
- We will use Gitkraken throughout the course to visual what we are doing 

## Terminal Crash Course: Introduction
- We will go through the basic git commands like: ls, pwd, cd, etc. 

## Terminal Crash Course: Navigation
- List
  - Use `ls` to list the contents of your current directory 
  - `ls folderName` - to view inside a specific folder 
- Print Working Directory 
  - Prints the path to the working directory (where you currently are)
  - `pwd`
- Change Directory 
  - Use `cd` to change and move between folders 
- cd .. 
  - Use `cd ..` to "back up" one directory 
- `open .` - opens up where you currently are in Finder on a Mac 
  - `start .` - same command on a window 
- `clear` - clears out the terminal 

## Terminal Crash Course: Creating Files & Folders
- Both of these run relative to where you are 
- Touch 
  - Use `touch` to create a file (or multiple) 
    - You can touch a file that already exists and edit a timestamp, but not commonly used for that 
  - Just need a name and an extension 
- mkdir (make directory)
  - `mkdir` will create a new directory (or directories)
  - Do not put spaces in your files 
    - Not recommended to use spaces in your directories in general, it can cause a lot of issues 

## Terminal Crash Course: Deleting Files & Folders
- rm 
  - `rm` will delete a file or files, it permanently removes them! 
    - Does not go into your trash 
      - You may be able to save the file if you were tracking with Git, but if not the file is gone 
- rm -rf 
  - use `rm rf` to delete a directory 
    - r = recursuve 
    - f = force
  - Be careful with this, this is gone 
- Flags are represented as - and are modifiers or options we can pass in 
- `Command + K` - clear shortcut 