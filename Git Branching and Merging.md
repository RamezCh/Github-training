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

## Track and Delete Branch
- git branch -u helps in tracking changes and synchronizing with the remote branch
- git branch -vv show a list of all local branches along with their latest commit details and their upstream branches if they are set
- git push -u origin <local-branch> pushes the specified local branch to the remote repository and sets the upstream (tracking) branch for it. This means future git push and git pull commands can be executed without specifying the branch name
- git branch --track <new-branch> origin/<base-branch> useful for creating a new branch that is based on an existing remote branch
- git checkout --track origin/<base-branch> checks out a local branch that tracks the specified remote branch. If the local branch does not exist, it will be created
- git branch -d my-new-branch  it’s a safe way to delete branches you have already merged
- git branch -D my-new-branch forces the deletion of the specified branch, even if it has not been merged
- git push origin --delete <branch-name> deletes the specified branch from the remote repository. This is useful for cleaning up old or unused branches on the remote

## Check diff between Branches
- git diff <branch-name>

## Push and Commit Changes
When creating a new branch, it will be on local machine and will not be accessible to teammates until it is pushed to the remote repository. To collaborate or share push local branch to remote repository
- git push origin <branchName>
- git branch -v = list of branches
- git push <remote> <branchName> = push a specific branch
- git push <remote> = push current branch

## Type of Branches
- Feature Branch (Perform development and add features)
- Master Branch (production ready source code)
- Develop/Integration Branch (Multiple features are integrated)
- Release Branch (finalized branch where merging occurs)
- Hotfix Branch (tempo debugging)

