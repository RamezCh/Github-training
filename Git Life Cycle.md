# Git Life Cycle

## Git File States
1. Untracked
- Means version control system is not tracking them nor their changes
- git add
2. Staged (after running git add)
- git commit
3. Commited
- Changes won't move file to untracked state, it is now part of version control system
4. Modified (after committed and changes done)

### Staged:
After all the changes are completed, files are added up to the staging area to be committed and preserved in local repo.
- Part of version control system
- Ready for commit files
- For commits, only files from index area will be picked up

### Committed:
Indicates that the file is stored safely in the local database
- Record changes into local DB (git repo)
- Commits are seen in git history and changes are preserved in local DB

### Modified:
Only files which are already part of Version control System or local repo can move to modified state. After changes are recorded and committed into repo, next time changes are not going to be in untracked file.
- changes made can be viewed alone with diff with the previous version
- same thing of adding up file ot the stage and performing staging activity then commit activity

## HEAD
It is used to point to the last commit or latest commit.
- git show HEAD
- It is a pointer that points to the latest commit
- It keeps on moving with new commits and lets us know about location and specific branch
- Head can move forward and backward
- cat .git/HEAD to check HEAD and know which branch

