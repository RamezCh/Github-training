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

## Master Branch
Git automatically creates a master branch when first commit in a repository is made. All commits by default are done in master branch unless a new branch is created explicitly. Developers must NOT make changes directly in master branch, rather should use feature branch.

## Feature Branch
To work on a new feature/bug fix. Multiple feature branches can be created for specific needs. Bugfix branch, new feature development branch. Helps to avoid disrupting source code every time an update is needed. All feature branches may not be merged into develop branch.

## Release Branch
Create a release branch one changes in a develop branch are done. Release branch helps to make sure that no further commits are done. It is merged with the Master branch after final check. It gets created close to production release.
- name usually begins with prefix 'release-'
- addresses bug fixes and release-related issues
- only when final code is ready, release branch is created
- when everything okay, we merge it with master branch

## Hotfix Branch
Used to add a critical fix to the production codebase. Used if issues happen in production environment and want to avoid the full cycle of development. Hotfix branch is merged with master and back merged with development branch. It starts with 'hotfix-' prefix.

## Develop/Integration Branch
Used for development. All feature branches will be merged to the integration/develop branch. It should always be stable and can be direcly merged with master.

## Git Merge
Multiple developers work on local repo on specific feature branch.
- git merge <branchName>

Example:
- git log
- git checkout master
- git merge develop

## Types of Merging:
- Two-way Merge
- Three-way Merge

Two-Way Merge: (two snapshots)
- feature branch to master branch
- When merging occurs they compare both latest commits
- After comparison the final result comes in

Three-way Merge: (three snapshots)
- Similar to Two-Way Merge but Master branch has new commit that isn't common ancestor with featuer branch
- It compares 3 points and then merges

## Merge Conflict
If two or more team members work in the same file simultaneously. Overlap of work may result in a conflict at the time of merging. During the integration of different feature branches into the develop branch may cause conflicts

Scenario:
- Henry pushes into Remote repo
- John tries to Push but merge conflict appears
- Why? Remote repo isn't same one as John has, there are more differences!
- git status (to see whats missing/wrong)
- Recommendation: Synchronize local repo with remote (Push/Pull) frequently
1. Open the conflicted file and make the necessary changes
2. Use git add command to stage the newly merged content
3. Perform a new commit using git commit command
4. Git creates a merge automatically

Commands to resolve conflicts:
- git log --merge (list of conflicting commits)
- git diff (shows differences)
- git checkout (to reverse the file changes or to change branches)
- git reset --mixed
- git merge --abort (exits merge and return to state before merge started)
- git reset

There is a mergetool:
- git mergetool
- Shows where problem at (differences/conflicting value)

How to Avoid Merge Conflict?
- Talk to team and decide who is primarily responsible for editing which files
- Review mechanism can also be added
- No one outside team should access files

## DEMO
- git branch -l
- git checkout -b develop
- git branch -l
- echo "Adding Content in Develop Branch" >> Readme.md
- git status
- git diff
- git log
- git add .
- git commit -m "Commit in Develop Branch"
- git status
- git checkout master
- git log
- git merge develop
- git log
- cat Readme.md
- git reset --hard <commitID>
- git log
- git merge develop --no-ff
- Editor opens to show message
- git log
 
Merge Strategies:
- Recursive
- Resolve
- Octopus
- Ours
- Subtree

Recursive:
- detect and manage mergers
- default strategy
- git merge -s recursive branch1 branch2

Resolve:
- 3 way merge
- resolves maximum of 2 commits
- git merge -s resolve branch1 branch2
- provides very fast resolution

Octopus:
- dealing with 2 or more branches
- git merge -s octopus branch1 branch2 branch3 branchN
- does NOT allow manual conflict resolution
- more than one branches can be merged

Ours:
- does NOT consider the changes from feature branch in case of conflict and uses our changes
- All the changes from feature branch is ignored and changes from master branch will be considered
- git merge -s ours branch1 branch2 branchN

Subtree:
- merging trees which have common ancestor
- git merge -s subtree branch1 branch2
- they need to have common ancestor

## Merge Conflicts DEMO (Manual Fix)
Git can't make a decision, so we need a strategy to solve it
- vi sample.java
- git status
- git add sample.java
- git status
- cat sample.java
- function1(){}
- git commit -m "added function1"
- git log
- ls -lart
- git branch develop
- git branch -l
- vi sample.java
- cat sample.java
- function3(){}
- git add sample.java
- git commit -m "adding function3"
- git status
- git checkout develop
- cat sample.java
- vi sample.java
- function2(){}
- git add sample.java
- git commit -m "Adding function2"
- git log
- git checkout master
- git log
- git merge develop
- merge conflict
- git status
- cat Readme.md
- cat sample.java
- <<<<< means from Head
- >>>>>>> means from branch
- git vi sample.java
- git status
- git add .
- git commit -m "merging develop to Master"
- git log

## Rebase
Rebase is a single patch for all changes
- Copy the change and implement in a branch as a patch
- No merge commit will be created in the destination branch
- Seems like a local commit
- Another way to integrate changes between branches
- git rebase <branchName>
Unlike merging, rebasing flattens the history because it transfers the complete work from one branch to another.
- Cleans the history, shows only commits done by developers and removes unnecessary commit information from history
- Merging becomes very clean

Why Rebase?
- Cleans the history
- Easy to manipulate any commit
- Avoids merging noise
- Cleans intermediate commits by making them a single commit

Merge > Rebase when:
- add branch changes back to base branch
- keep same history rather than rewrite it
- revert the changes quickly

Rebase > Merge when:
- squash multiple commits
- can cahnge the order of commits
- helps clean the history

## Git Rebasing - DEMO
End result in rebasing is almost the same as merging.
- git branch -l
- git checkout -b develop
- echo "Adding New Content" >> Readme.md
- git status
- git add Readme.md
- git status
- git commit -m "Commit in Develop Branch"
- git log
- git checkout master
- git branch
- git rebase develop
- git branch
- git log
Notice, commit in develop branch came to master and looks as if it was a local commit.







