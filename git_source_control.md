id: app-development-gini-git-and-source-control
summary: sum all app example
authors: Shay markovich

# git and source control
<!-- ------------------------ -->
##General
In this codelab you we will how to use git

<!-- ------------------------ -->
## What is git
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

###
You can use git for evertying you do

you should learn at least those actions:

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

### Github tools

You can use github using several git tools
- From therminal
- SourceTree - Softwere that shows visulay the git commits tree
- Android studio - manage git inside the android stuido IDE


### Git remote host
In order to colaborate  with other pepole we host in remote git host

We use "GITHUB" to host most of our project

some project use diffrent git host like gitbucke, or gitlab

**login**
- login with https: user name and password
- login with ssh: follow the instraction in github how to login with ssh, it include create private key in your computer, and put the public key in github site
- some github repositories require login with ssh, so you better do one

### pull reqest

Every code insertion for new feature will be in new source branch and required "pull request" in order to marge it to the target branch

**create pull request**
- When starting to work on new feature create new branch
- Commit code in the new branch
- Push the new branch to the remote origin
- Go to github site and create new pull request from the new branch source to the target branch
- After approve, the code will be marge to the target branch
- Use squash and marge to if you want to squash all the commits to one commit
- Use marge if you want to remember the source branch history
- Don't forget to delete the branch after marge

**What to do when there is conflict**
- In your local repository pull the source and target branch so they will be sync with the remote repository
- From the soruce branch marge the target branch, after check everyting is working well commit the marge
- Push the commit to the remote

**need to remember**
- Try to do as many pull request as you can, don't do one big pull request with thousand lines of codes
- Put description of what you did in the pull request descripinn box, and also jira ticket link if needed


<!-- ------------------------ -->
## Return to main
[return to main](../)