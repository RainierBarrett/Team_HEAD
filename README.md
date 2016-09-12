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
`git init` : creates a new empty repo in your local computer

`git clone <url>` : creates a copy of an existing Git repository in your computer

`git status`: shows which file is in which state (staged and unstaged changes)

`git add`: stages your changes

`git commit -a "message"`: records the changes 

`git log`: shows all the past commits made in the repository

`git push origin <branchname>` : pushes our local repo to the Github server

`git pull origin <branchname>` : Fetches and replays changes from the remote branch

`git merge <branchname>`: Merges the branch mentioned with the current branch

`git branch` : Shows a list of existing branches and indicates the branch on which you are currently working

`git branch -d <branchname>`: deletes the branch mentioned

`git rm`: removes files from index or from the working tree and the index

`git mv`: moves or renames a file or directory  

**Section 4: Merge Conflicts**
=====
Sometimes trying to merge one branch into another generates a warning saying that there are "Merge Conflicts" which need to be resolved.
This happens when the contents of the same part of a file in the two branches differ. Instead of auto-resolving the issue, Git allows the user to choose the desired file content. 
The merge conflict message mentions the file where there is a conflict. If we open the file, we see something like this:  
```
<<<<<<< HEAD:foo.txt  
Hello god  
=======  
Hi dog  
>>>>>>> develop:foo.txt
```  
The block between "<<<<<" and "\=\=\=\=" represents a part of the file "foo.txt" in our current branch and the one between "\=\=\=\=" and ">>>>" represents the same part of file "foo.txt" in the branch "develop" that we are trying to merge into our current branch. In order to resolve the conflict, we have to manually modify the conflicting part. For example, we choose to resolve the above mentioned conflict like this:
`Hi god`  
After we are satisfied with the content, we have to add file "foo.txt" to stage it. Staging the file confirms that the merge conflict is resolved.

**Section 6: Gitignore Files, Globs, and You**
====
Has this ever happened to you? You just started working in a git repo, and you're finally ready to commit, when you realize you accidentally entered `git add -a` beforehand. Now you've got all these junky `<file>.o`, `<useless>.a`, and `#<emacs-backup-file>.txt#` files cluttering up your staging area. But wait! When you `git rm` them, Git still won't let you commit because of all these unstaged changes! Luckily, there's an easy and convenient way for you to avoid this mess in the future, without having to manually delete or move all of your backups and executables.

Introducing `.gitignore`: the contents of this unassuming file will designate what Git should ignore in your directory, and let you get on with your work much more smoothly. Now, you *could* simply add each filename by hand, knowing what the list of files are. However, in the future, you'll have to add any changes you've made as well. In order to make the best use of your `.gitignore` file, you can employ gob formatting to ignore wide swaths of files matching a pattern you specify.

Don't want any pesky build files left over from your C++ compiler? Just add the lines `*.o` and `*.obj` in your `.gitignore`, and worry no more.

Perhaps you'd like to keep an entire directory untracked by Git. The format for this directive is just `<directory-name>/`. For example, `foo/*` will ignore the directory "`foo`" and all its contents. You can also recursively ignore a directory and all its subdirectories with `<directory-name>/**`.

The "**" can also be used as a prefix, in which case it invokes a search. Anywhere Git finds a matching pattern in the file path, it will proceed to ignore that path. For example, `**/bar/` will ignore any directory named "`bar`" anywhere in the path below the `.gitignore` location.

Comments: anything preceded by a "`#`" symbol in your `.gitignore` file will not be interpreted. This is a handy way to leave yourself some reminders.

Finally, you can make exceptions with `.gitignore`. Any pattern preceded by a "`!`" will reverse its logical meaning. In other words, include an exclamation point before your exclusion path to explicitly tell Git *not* to ignore something. For example, if you wanted to ignore all your object files generated by your C++ compiler, but you *do* care about tracking the changes in the particular file `foo.o`, you can include the following two lines in your `.gitignore` file:

`*.o` #this means, "ignore all `.o` files."

`*.obj` #this means, "ignore all `.obj` files."

`!foo.o` #"but specifically don't ignore the file `foo.o`.