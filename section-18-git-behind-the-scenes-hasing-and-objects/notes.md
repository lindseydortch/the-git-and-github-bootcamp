# Section 18: Git Behind the Scenes - Hashing & Objects

## What Really Matters In This Section
- Critical 
- Important 
  - The Local Config File 
- Nice to Have
  - The Refs Directory 
  - The HEAD File 
  - Hashing Functions Basics 
  - Gti Objects: Blobs, Trees, and more! 

## Working With The Local Config File
- What is in .git?? 
  - objects 
  - config 
  - HEAD 
  - index 
  - refs
  - There's more, but this is the juicy stuff 
- Config 
  - The config file is for... configuration. We've seen how to configure global settings like our name and email across all Git repos, but we can also configure things on a per-repo basis 
  - There is also a global config file 
  - You can look at the Git configuration documentation for everything you want to do 
  - You can also update the colors you want to show for your git diff, color of the branches and git status 

## Inside Git: The Refs Directory
- Refs Folder 
  - Inside of refs, you'll find a heads directory. `refs/heads` contains one file per branch in a repository. Each file is named after a branch and contains the hash of the commit at the tip of the branch. 
  - For example `refs/heads/master` contains the commit hash of the last commit on the master branch 
  - Refs also contains a `refs/tags` folder which contains one file for each tag in the repo 

## Inside Git: The HEAD file
- HEAD
  - HEAD is just a text file that keeps track of where HEAD points
  - If it contains `refs/heads/master`, this means that HEAD is pointing to the master branch 
  - In detached HEAD, the HEAD file contains a commit hash instead of a branch reference 

## Inside Git: The Objects Directory
- Objects Folder 
  - The objects directory contains all the repo files. This is where Git stores the backups of files, the commits in a repo, and more 
  - The files are all compressed and encrypted, so they won't look like much! 
- 4 Types of Git Objects 
  - commit
  - tree
  - blob
  - annotated tag

## A crash Course On Hashing Functions
- Time out! We need to talk about hashing! 
- Hexadeximal - Base 16 - We use letters 0-9 and then letters 
- Returns a 40 character hash 
- Hashing Functions 
  - Hashing functions are functions that map input data of some arbitrary size to fixed-size output values 
- Cryptographic Hash Functions 
  - One-way function which is infeasible to invert 
  - Small change in input yields large change in the output 
  - Deterministic - same input yields same output 
  - Unlikely to find 2 outputs with same value 
- SHA-1
  - Git uses a hashing function called SHA-1 (though this is set to change eventually)
  - SHA-1 always generates 40-digit hexadecimal numbers 
  - The commit hashes we've seen a million times are the output of SHA-1

## Git As A Key-Value Datastore
- Git Database 
  - Git is a key-value data store. We can insert any kind of content into a Git repository, and Git will hand us back a unique key we can later use to retrieve that content 
  - Theese keys that we get back are SHA-1 checksums 
- Example 
  - Keys - Values 
    - Hash 1 - v1 of app.js 
    - Hash 2 - v2 of app.js 
  - Please give me the content for the key of Hash 2 and then returns the value of v2 of app.js 
- Hashing functions 
  - Git uses SHA-1 to hash our files, directories, and commits 
  - v1 of app.js and v2 of app.js -- SHA-1 --> Hash 1 and Hash 2

## Hashing With Git Hash-Object
- Let's try hash(ing)
  - The `git hash-object` command takes some data, stores it in our `.git/objects` directory and gives us back the unique SHA-1 hash that refers to that data object 
  - In the simplest form (shown below), Gti simply takes some content and returns the unique key that WOULD be used to store our object. But it does not actually store anything 
  - `git hash-object <file>`
  - `echo 'hello' | git hash-object --stdin`
    - The `--stdin` options tells `git hash-object` to use the content from stdin rather than a file. In our example, ir will hash the word 'hello'
    - The echo command simply repeats whatever we tell it to repeat to the terminal. We pipe the output of echo to `git hash-object`
    - This does not get stored 
  - `git hash-object` is a git utility like `git init` 
  - `echo 'hello' | git hash-object --stdin -w` 
    - Rather than simply outputting the key that git would store our object under, we can use the `-w` option to tell git to actually write the object to the database 
    - After running this command, check out the contents of `.git/objects`
    - You can view the file that the hash gets stores in, in objects and then the hash will start with the folder name 

## Retrieving Data With Git Cat-File
- Let's try Hash(ing)
  - `git cat-file -p <object-hash>`
    - Now that we have data stored in our Git object database, we can try retrieving it using the `git cat-file` command 
    - The `-p` option tells Git to pretty print the contents of the object based on its type 
  - `git cat-file -b <object-hash> > <filename>`
    - Will restore file to that object hash 
- Git will spit out the same hash until you change something - small change, any change should lead to a change in the output 
- This all gets stored manually and gets written without even having to make a commit, we have only been hashing things and stored them and been able to retrieve them (this is not a commit)

## Deep Dive Into Git Objects: Blobs
- 'hello' ----> HASH 1 
- 'goodbye' ---> HASH 2
- Hellow Git, I would like to know what you have stored under the key HASH 2
  - --> returns 'goodbye'
- Blobs 
  - Git blobs (binary large object) are the object type Git uses to store the contents of files in a given repository. Blobs don't even include the filenames of each file or any other data. They just store the contents of a file! 
  - This is what we created in the last lecture 

## Deep Dive Into Git Objects: Trees
- Trees 
  - Trees are Git objects used to store the contents of a directory. Each tree contains pointers that can refer to blobs and to other trees 
  - Each entry in a tree contains the SHA-1 hash of a blob or tree, as well as the mode, type, and filename 
  - Tree Hash - tree 
    - blob - hash blob - app.js 
    - tree - hash tree - images 
    - blob - hash blob - README 
    - tree - hash tree - styles 
- See class slides for diagram of how this looks 
- Viewing Trees 
  - `git cat-file -p master^{tree}` 
      - Remember that `git cat-file` prints our Git objects. In this example, the `master^{tree}` syntax specifies the tree object that is pointed to by the tip of our master branch 
  - `git cat-file -t <hash>` 
    - Will show the type of git object 

## Deep Dive Into Git: Commits
- Commits 
  - Commit objects combine a tree object along with information about the context that led to the current tree. Cimmits store a reference to parent commit(s), the author, the committer, and of course the commit message 
  - Commit Hash 
    - tree - tree hash 
    - parent - parent hash 
    - author - siruis 
    - committer - sirius 
    - This is my commit message 
- Visualize a Commit 
  - When we run git commit, Git creates a new commit object whose parent is the current HEAD commit and whose tree is the current content of the index 
  - So every commit is tied to a tree 
  - Commit 1 
    - tree - tree hash 
    - parent - none 
    - author - wolfgang 
    - committer - wolfgang
    - message - initial commit 
  - Commit 2 
    - tree - tree hash 
    - parent - points to the hash for Commit 1 
    - author - wolfgang 
    - committer - wolfgang 
    - message - fix typo 
  - Commit 3
    - tree - tree hash 
    - parent - points to the hash for Commit 2 
    - author - wolfgang 
    - committer - wolfgang 
    - message - add banner 
- Git doesn't give us a new blob if the file doesn't change, but if you add in a change, that hash will change 