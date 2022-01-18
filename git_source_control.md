id: app-development-gini-git-and-source-control
summary: sum all app example
authors: Shay markovich

# git and source control
<!-- ------------------------ -->
##General
In this codelab you we learn will how to use git

<!-- ------------------------ -->
## What is git
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

###
You can use git for manage your code

You should be familiar with at least those git commands and files:

**local**
- git init
- git add .
- git commit -m ""
- git branch
- git checkout

**working with remote (origin)**
- git clone
- git pull
- git push -u origin main ()

**gitignore**
- use git ignore file

### Github tools

You can use github using several git tools
- From terminal
- SourceTree - Software that shows visulay the git commits tree
- Android studio - Manage git inside the android stuido IDE


### Git remote host
In order to colaborate  with other pepole we use a common remote repository in remote git host

We use "GITHUB" to host most of our project

some project use diffrent git host like gitbucke, or gitlab

**Login to github**
- Login with https: user name and password
- Login with ssh: follow the instraction in github how to login with ssh, it include create private key in your computer, and put the public key in github site
- some github repositories require login with ssh, so you better do one

### pull reqest

Every code insertion for new feature will be in new source branch and required "pull request" in order to marge it to the target branch

**Create pull request**
- When starting to work on new feature create new branch
- Commit code in the new branch
- Push the new branch to the remote origin
- Go to github site and create new pull request from the new branch source to the target branch
- After approve, the code will be marge to the target branch
- Use "squash and marge" if you want to squash all the commits to one commit
- Use "marge" if you want to keep the source branch history
- Don't forget to delete the branch after marge

**What to do when there is conflict**
- In your local repository pull the source and target branch so they will be sync with the remote repository
- Marge the soruce branch into the target branch, and resove the conflicts, after check everyting is working well commit the marge
- Push the commit to the remote

**Key points**
- Try to do as many pull request as you can, don't do one big pull request with handreds lines of codes
- Put description of what you did in the pull request description box, also add jira ticket link if needed


<!-- ------------------------ -->
## Return to main
[return to main](../)