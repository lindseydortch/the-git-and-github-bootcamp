# Section 8: Comparing Changes With Git Diff

## What Really Matters In This Section
- Critical 
  - Reading Diffs
  - Git Diff Basics 
- Important 
  - Diffing Brnaches 
  - Diffing Commits 
  - Diffing specific files 
  - Git diff --staged

## Introducing The Git Diff Command
- Comparisons with Git Diff 
- Git Diff 
  - We can use the git diff command to view changes between commits, branches, files, our working directory and more 
  - We often use git diff alongside commands like git status and git log, to get a better picture of a repository and how it has changed over time 
- git diff 
  - Without additional options, `git diff` lists all the changes in our working directory that are NOT staged for the next commit 
  - Compares staging area and working directory 

## A Guide to Reading Diffs
- What Does It Mean? 
  - Last Commit 
    - red 
    - orange 
    - yellow
  - New changes 
    - red 
    - orange 
    - blue 
    - yellow 
- Compared files 
  - For each comparison, Git explains which files it is comparing. Usually this is two versions of the same file 
  - Git also declares one file as "A" and the other as "B"
  - `diff --git a/file.txt b/file.txt`
- File Metadata 
  - You really do not need to care about the file metadata 
  - The first two numbers are the hashes of the two files being compared. The last number is an internal file mode identifier.
- Markers 
  - File A and B are each assigned a symbol 
    - File A gets a minus sign (-)
    - File B gets a plus sign (+) 
- Chunks 
  - A diff won't show the entire contents of a file, but isntead shows portions or "chunks" that were modified 
  - A chunk also includes some unchanged lines before and after a change to provide some context 
- Chunk Header 
  - @@ -3,4 +3,5 @@ 
  - Each chunk starts with a chunk header, found between @@ and @@ 
  - From file a 4 lines are extracted starting from line 3 
  - From file b, 5 lines are extracted starting from line 3
- Changes 
  - Every line that changed between the two files is marked with either a + or - symbol
  - lines that begin with - come from file A 
  - lines that begin with + come from file B  

## Viewing Unstaged Changes
- git diff
  - Without additional options, git diff lists all the changes in our working directory that are NOT staged for the next commit 

## Viewing Working Directory Changes
- `git diff HEAD` lists all changes in the working tree since your last commit 
- --/dev/null - shows us we had nothing there before 
- Shows us everything staged or not 

## Viewing Staged Changes
- `git diff --staged` or `git diff --cached` will list the changes between the staging area and our last commit 
  - "Show me what will be included in my commit if I run git commit right now"

## Diffing Specific Files
- Diff-ing Specific Files 
  - We can view the changes within a specific file by providing git diff with a filename 
  - `git diff HEAD [filename]`
  - `git diff --staged [filename]`

## Comparing Changes Across Branches
- Comparing Branches 
  - `git diff branch1..branch2` will list the changes between the tips of branch1 and branch2
  - Order does matter here 
  - You can get the same outcome if you use a space instead of the .. in between branches 

## Comparing Changes Across Commits
- Comparing Commits 
  - To compare two commits, provide git fidd with the commit hashes of the commits in question
  - `git diff commit1..commit2`

## Visualizing Diffs With GUIs
- This is where GUIs shine when working with Git 
- Hold down shift to compare commits 

## Diff Exercise
- Completed Section Exercise on Diff's 
  - Do not run the git clone command from an existing repository 