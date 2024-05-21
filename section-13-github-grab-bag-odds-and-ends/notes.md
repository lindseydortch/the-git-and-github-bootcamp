# Section 13: Github Grab Bag: Odds & Ends

## What Really Matters In This Section
- Critical 
  - Repo Visibility: Public vs Private
  - Adding Github Collaborators 
- Important 
  - README files 
- Nice to Have
  - Writing Markdown 
  - Github Gists 
  - Github Pages 

## Github Repo Visibility: Public vs. Private
- Public vs. Private Repos 
- Public Repos 
  - Public repors are accessible to everyone on the internet. Anyone can see the repo on Github 
- Private 
  - Private repos are only acessible to the owner and people who have been granted access 
  - Will show as a 404 

## Adding Github Collaborators
- You go into Settings -> Manage Access 
  - You need to know the username or email of who want to add to the repository 
  - The person has to accept the invitation 
- The collaborator doesn't have access to settings, this is only for the owner, unless it's a Github Enterprises account 

## Github Collaboration Demo
- Having two different users in your terminal is typically painful 
  - Focus on being one user 

## What are READMEs?
- READMEs
  - A README file is used to communicate important information about a repository including: 
    - What the project does 
    - How to run the project 
    - Why it's noteworthy 
    - Who maintains the project 
  - If you put a README in the root of your project, Github will recognize it and automatically display it on the repo's home page 
- README.md
  - READMEs are Markdown files, ending with the .md extension. Markdown is a convenient syntax to generate formatted text. It's easy to pick up! 

## A Markdown Crash Course
- Markdown is a text-to-html tool for web writers
  - It allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML)
- To make headings we use `# i am a heading`, we have the same amount of headinfs as HTML 
- To make text bold `** hello`
- To make italic `*hello*`
- `> blockquote`
- Spacing, you have to have an empty line between them 
- `code`
- ``` js console.log('Hello') ``` -- creates block of code 
- Reddit uses markdown 
- [link text](url) - writes out a link 
- ![Minion](url) - for images

## Adding a README To A Project
- A walkthrough of how to create a README to a project 
- READMEs are the one thing a recruiter would be able to look at and understand instead of the code of your project 
- To preview markdown - Command + Shift + P and then `Markdown: Open Markdown`

## Creating Github Gists
- Github Gists 
  - Github Gists are a simple way to share code snippets and useful fragments with others. Gists are much easier to create, but offer far fewer features than a typical Github repository. 
- gist.github.com
  - People will use this for sharing code on sites like Github 

## Introducing Github Pages
- gh pages 
  - Github Pages are public webpages that are hosted and published via Github. They allow you to create a website simply by pushing your code to Github 
- Static Sites 
  - Github pages is a hosting service for static webpages, so it does not support server-side code like Python, Ruby or Node. Just HTML/CSS/JS
- Two types of Github Pages 
  - User Site 
    - You get one user site per Github account. This is where you could host a portfolio or some form of personal website. The default URL is based on your Github username, following this pattern: `username.github.io` though you can change this 
  - Project Sites 
    - You get unlimited project sites! Each Github repo can have a corresponding hosted website. It's as simple as telling Github which specific branch contains the web content. The default urls follow this pattern: `username.github.io/repo-name`

## Github Pages Demo
- Walkthrough of how to setup a Github Pages site on a Github Repository that you own 