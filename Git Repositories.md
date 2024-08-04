# Git Repositories

## Learning Objectives:
- Understand and Use GitHub
- Explain diff types of Git Repo
- Work with Repo - Forking, Push/Pull, Branch

## Repository
It is like a folder or a directory where source code is stored. It also stores each file's revision history.

There are two types of repo, local and remote/central. Local is our PC. Remote is Github, BitBucket or GitLabs.

There are Public, Internal and Private Repo.
- Public is for everyone to see
- Private is only for you and who you give permission
- Internal is for company/organization

Common tasks: Push/Pull. Done doing changes? Push. Want to get the new changes? Pull.

Remote Repo Allows us to:
- Host onto a server
- Accessible to all team members
- Similar to Local Repo
- Clone/download remote to local
- All activities like branches, commits, tags, merging, rebasing ( can be performed on local )
- After changes, push those changes to remote repository

Actual project work is carried out in local repository and after they are made and committed locally we push them into remote repo

## Terminology - Origin
Origin is a shorthand name for the remote repository (URL). Gotta make things easier to type right?
- git clone janedoe@git.ourcompany.com:project.git
- git.ourcompany.com: f4265(master) -> a6b4c -> 0b743
- My Computer: f4265(Origin/master | remote/local) -> a6b4c ->0b743

- We use forking if we do not have direct access to remote repository
- Push to move changes from local to remote
- Pull to move changes from remote to local
- Locally we add, commit, push and pull
- git clone makes a local copy of a remote repo
- git fetch downloads the meta data
- git merge merges the changes to local repo
- git pull executes git fetch and merge internally
- git pull <remote> = git fetch <remote> + git merge origin/<current-branch>

workspace -> add -u > index -> commit -> local repo -> push -> remote repo

remote repo -> fetch -> local repo

