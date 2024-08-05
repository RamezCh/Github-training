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

## Check File Status
- git status
- Tracked? Un-tracked?
- Branch Info
- Ready to commit files
- modified files

To see details diff:
- git diff HEAD
- git diff --summary

To move File to Staging:
- git add <file name>
- git add file1 file2 file3..
- to add all files (including new, deleted, modified files) git add -A, git add --all (both same)
- git add -u (stages modified and deleted but not new files) | (basically tracked files)
- git add . (stages new and modified files in current directory)
- These do not affect remote repo, this is a local operation

Move files from Staging to local Repo:
- git commit ( will open vim file so you write message )
- git commit -m "message"
- empty message or improper message will be rejected
- git push origin <branchName>

Bypassing Staging:
- git commit -a (adds all files available in repo)
- git commit -am "message"

## Revert a Commit
Done when changes aren't correct and need to be fixed
- git revert <commitHash>
- git log to find commitHash
- Revert is undo, going back in time
- Will not remove log, will be seen as a new commit

What if we want to revert a Merge?
One by one is a pain.
- Merging is a commit that has at least two parents: Main commit, Merge commit
- We need to rollback parent as well
- git revert <commit reference> -m 1
- -m 1 is used for the first parent ( to roll back)

## Git Reset
We are at head, we have v1 of file.txt. In working directory we have v2 of file.txt.
- For a Specific file
- For a repo
- git reset file.txt
- git status
- git reset --hard will reset multiple files
- git reset --main/file.txt resets one file only

Reset has 3 flags: --soft, --mixed, --hard
- soft: git reset --soft <commit-id>
- it removes files from local repo only, not staging nor working directory
- hard: all changes made are completely removed, HEAD moved backward, can't see content again
- mixed: removes from staging and local but keeps them at working directory

Use case:
- git reset -- main/*
- commit will be reverted and removes from log history
- HEAD moves from latest to one step down
- git reset --soft HEAD^
- means that the commit is cancelled and moved before HEAD
- Add another file to the staging area and commit or amend files and commit

Revert all changes to a file:
- git diff <fileName>
- git checkout <fileName> discards all changes made in a file
- git reset --hard discards all changes on the branch

In simple terms:
- soft makes them as if you did git add and didn't do git commit
- hard removes all traces of the crime
- mixed as if you didn't do git add nor git commit, they are just a file present in repo

- git checkout <commit> cleans it completely
- reset [commit] <paths> working directory is safe
- checkout [commit] <paths> working directory isn't safe

## ^(caret symbol) and ~(tilde)
- HEAD~n means n commits before HEAD
- nth generation ancestore of HEAD
- HEAD~ or HEAD~1 means 1 commit before HEAD
- HEAD~2 goes 2 commits backward and so on..
- HEAD^ refers to the first parent of HEAD (useful in merges)
- HEAD^1 is equivalent to HEAD^
- HEAD^2 refers to the second parent of HEAD (in case of a merge commit)
- HEAD~n^ refers to the first parent of the nth commit before HEAD
- HEAD~n^2 refers to the second parent of the nth commit before HEAD

## Git Internals
Git Objects: Files and data are stored in form of Objects but they aren't in readable format. They are simple key-value data store maintained at remote and local repo. Any type of content can be inserted in a Git repo.
- All files are commited in form of git objects in .git folder
- .git folder should be secured
- There are 3 types of objects: blob (contents of a file), tree (directory listing), commit (snapshot of working tree)

Blob:
- Content of files are stored in form of objects called blobs (Binary Large Objects)
- Secured
- Every blob in git is identified by its SHA-1 hash
- Doesn't register its creation date, its name or anything but its content
- Contains binary stream of data

Tree:
- Directory Structure
- Refers to blobs as well as other trees
- Identified by SHA-1 hashes

Commit:
- snapshot
- HEAD points to latest commit in branch
- Identified by SHA-1 Hashes
- Every commit holds entire snapshot, thats why its easy to check differences
- Contains blob files and trees

## Git Data Storage

