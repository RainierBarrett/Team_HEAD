#A GIT STUDY GUIDE

A small pseudo-manual for the new Git user. Project for Dr. White's Advanced Numerical Methods class at University of Rochester, Fall 2016. Enjoy.

**Section 1: Starting Up Git**
====

First of all, you'll want to make an account on [github.com](https://github.com). Once you've done that, make sure you've installed the appropriate git client on your computer. If you have Windows, you'll want to use git-scm. On Linux or Mac, you likely already have git installed out of the box. To check, you can run `man git`, `which git`, etc. If you don't have it, go ahead and install it via your favorite apt-like service.

Finally, before you begin using git, it will be useful to run a couple of initial setup commands, to make sure git knows who you are:
`git config --global user.email <your-email-address>` 
`git config --global user.name <your-git-username>`

**Section 2: Git command cheat sheet**
======
`git checkout -b <newbranchname>`: Creates and checks out a new branch  
`git add filename`: Sets the file to the staging area  
`git status` : Shows the status of the files in the working directory and the staging area  
`git commit -m <commit message>` : Captures the snapshot of how things are in the staging area  

**Section 3: Git command list**
======
`git init : creates a new empty repo in your local computer
`git clone <url> : creates a copy of an existing Git repository in your computer
`git status: shows which file is in which state (staged and unstaged changes)
`git add: stages your changes
`git commit -a "message": records the changes 
`git log : shows all the past commits made in the repository
`git remote add <url> : pushes our local repo to the Github server


