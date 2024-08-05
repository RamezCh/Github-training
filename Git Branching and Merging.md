# Git Branching and Merging

## Branch
A Basic approach followed in any version control system. Independent development line. Do the changes in branch and then merge it to master branch.
- Master is default branch which gets created at time of git initialization
- Most of development projects have two mainstream branches: Master (final source code), Dev (for development and testing purposes)
- HEAD or master branch points to the latest commit

## Branching Main Operations
- Create Branch
- Delete Branch
- Rename
- Publish
- Switch
- Compare

## Create and Check Branch
- git branch <new-branch-name>
- HEAD points to the branch we are currently on (MASTER)
- git branch -l shows available branches
- * green color = current branch
- git branch --list
- git branch

## Switch and Rename Branch
- git checkout <other-branch> moves HEAD to latest commit on other branch
- git branch -m master returns to master branch
- git checkout -b <new-branch-name> creates a new branch + switches to it
- git branch -m <new-name> renames current checked out branch
- git branch -m <old-name> <new-name> renames specific branch
- git push origin --delete <old-name> to delete branch from remote repo
- git push -u origin <new-name> to publish new branch to remote repo

