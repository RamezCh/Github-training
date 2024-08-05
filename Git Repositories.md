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

## Working with Remote Repo
- To remove the remote: git remote remove <name>
- git remote -v lets us get remote name
- git remote rename <old> <new>
- git remote show -n <name> gets info about remote
- git checkout --track lets us inspect a remote repo
- git checkout --track <remote-repo>/<remote-branch> lets us create a local branch with same name as remote branch
- git checkout --track -b <local branch> <remote-repo>/<remote-branch> to create local branch with diff name from remote
- git branch -vv to verify tracking branches
- git branch --v to see latest commits, commits info and head poitner related info

## Intro to Github
Cloud-based git repository hosting service. Recently acquired by MicroSoft. Free service as an individual and licensed version for organization. Unlimited Repoistory created. It has GUI and CLI. Provides access control, wikis and basic management tools.

Other similar services:
- GitLab
- BitBucket
- AWS CodeCommit
- Azure DevOps
- Codebase
- Perforce
- SourceForge

## Github Features
1. Effective Team Management
- Github supports and organizes all team members on one page
- Team can callaborate with each other
2. Accessibility
- Can create numbers of public and private repositories
3. Integration
- Easy to Integrate with other DevOps toos like Jira, Jenkins
4. Improved Code Writing
- Assists code review
- Assists code approval
5. Increased Code Safety
- Identifies vulnerabilites in the code
- Enables collaboration to secure end-to-end
6. Easy Code Hosting
- Single location for all the code and documentation
- Easy GUI

GitHub has various plans: free, team, enterprise. 

## GitHub Flow
Setup a repo for entire team. When working on new features, create a branch for that feature. Do not work on Master branch.

## Create a New Repo
Login Github -> click on + -> give name and select features you want
- git remote add origin https://GitHub.com/<username><local>
- origin is variable name for remote repo, you can actually name it as you like but its common practice
- git remote add origin <remote_repo_url>
- git remote shows saved remote repo variables
- git remote -v shows variable and its value

## Configure SSH Key
Usernames and Pass outdated, lets use keys easier (passwordless communications).

We need to keys private and public. First we need to create key on PC.
- ls -al ~/.ssh lets us see if we have key
- id_rsa.pub
- id_ecdsa.pub
- id_ed25519.pub

If we don't have public keys we can create them.
- ssh-keygen -t ed25519 -C "your_email@example.com"
- if key already exists, we can overwrite it

id_RSA, id_DSA are standard and not required to be loaded into the OS.Public key is used when accessing SSH keys.
- eval "$(ssh-agent -s)" (Check/Run SSH-agent in background)
- ssh-add ~/.ssh/id_ed25519 (Add key to SSH-agent)
- ssh -T git@github.com (Check the SSH connection)

How to upload public key into github:
- Login GitHub
- Select SSH and GPG options
- Click new SSH key
- Paste public key into key field
- Private keys will be available in local keys only
- Public key will be uploaded into remote repo
- Using public key comunications will be conducted

## Git Push and Fetch Branch
- git remote set-url origin git@github.com:<username>/<local repo name>.git
- git push -u origin master
- Pushes the local content on the master branch of the remote location
- git push
- git pull fetches and merges from remote repo
- git fetch downloads commits, objects and refs from remote repo but no merge
- git fetch <repo URL>
- gitch fetch <branch URL><branch name>
- git fetch -all
- They all work since origin is default and takes current branch
- git pull (works on current branch)
- git pull origin master (remote name, repo url)
- git pull -all (pulls all branches)

To take latest changes from the remote:
- git fetch <remote>
- git merge FETCH_HEAD

OR:
- git pull <remote-repo> <remote-branch>

