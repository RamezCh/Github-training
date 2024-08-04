# Working with Git

## Initialization
we have 2 interfaces GUI and CLI. CLI > GUI you can see results and know operations you are running

- git init
- It starts a git repository in current folder
- git init (repository name)
- this will start git repository at specific folder
- After running command we can see .git folder

In Version Control it is important to track changes and who did those changes. So Author details are important
- git config --global user.name "[name]"
- git config --global user.email "[email address]"
- git config --global user.name "learnkarts"
- git config --global user.email "git@example.com"
- git log or login github website  or bitbucket to see details of who is doing the changes

.git folder is known as Git Repository
Working directory is your project file

## Adding Files to Staging Area
Empty repo -> Add files -> Multiple files in version control system

- Working directory: File.txt v1
- git add .
- Staged: File.txt v1
- Repository: empty

- git add <filename>
- git add file1 file2 file3 and so on.. (To add multiple files)
- git add . (adds all files into the staging area)
- git add * or git add -A adds all non-tracked files in current repo directory
- git add -u adds currently tracked files which have been modified into the staging area and checks if deleted or not

But should we add all files? What shouldn't we add?
- Runtime files such as log, lock, cache, or temporary files
- Files with sensitive information, such as configuration files, passwords, or API keys
- Compiled code, such as .class, jar files, .o, so files...
- Dependency directories, such as /vendor or /node_modules
- System files like .DS_Store or Thumbs.db
- IDE or text editor configuration files

How do we ignore those files?
- Add such file to a file .gitignore
- git status won't show those files as well

1. /access.log ignores the access.log file only in the root directory
2. access.log ignores any access.log file in any directory
3. build/  ignores the build folder and everything inside it, only in the root directory
4. *.log ignores any file that ends with .log in any directory
5. logs/** ignores everything inside the logs directory, no matter how deep the structure
6. **/build ignores any directory named build, regardless of its location
7. foo/**/bar ignores any bar directory or file that is inside a foo directory, regardless of the number of intermediary directories
8. access?.log  ignores files named access0.log, access1.log, accessa.log, where the question mark represents any single character
9. foo?? ignores any file or directory named foo followed by exactly two characters.

## Git Commit Command
- Working directory -> git add -> Staged -> ? -> Repository
- git add only preserves them temporary, we need git commit to save them permanently
- Working directory -> git add -> Staged -> git commit -> Repository

- git commit -m "message"
- This messages helps identifying what we have changed
- If we don't put -m, command line will open vim so you put commit message
- Empty commit messages are rejected
- Commits are reserved in log file and repository

If we don't want to add then commit we can combine them
- git commit -am "message"
- It stages tracked files and commits them directly
- It doesn't add untracked files

## Remove file command
- git rm <filename>
- removes file from working directory and deletes from staging area

- git rm --cached <filename>
- removes file only from staging area
- We can restore file by using git add again

- git restore <filename>
- Checks previous code and if changes done, rolls back and we lose all our temporary changes

- git mv <filename> command is used to rename a file or move a file

- git clean removes unwanted files from working directory (untracked files), temporary files
- It doesn't remove the following: tracked files, committed files, files in .gitignore

- git clean -n does a dry run to show what it will do (safe practice)
- git clean -f forcefully removes untracked files
- git clean -x removes files listed in .gitignore

## Check file status
- git status
- Shows new files, untracked files, files that are modified
- It provides a complete summary of file status
- git status -s gives summary and not detailed output

What if we want to check differences between files?
- Head refers to latest commit
- git diff HEAD gives detailed difference in comparison to latest commit
- git diff shows diff between working directory and staging area
- git diff --staged shows diff between staging area and last commit
- This command helps us check diff between commits and be on safe side
- git diff master <branch_name>

There is third party tool called difftool, it shows comparison in external tool instead of command line

Resetting a file means rolling back the changes
- git reset --hard resets all files in directory
- git reset --hard command <filename>

## Reverting a Commit
It means going back in time
- git revert <commitHash>
- We can see hash in git log command or check remote repo for it
- After revert everything after Hash we gave gets removed

## Git Log
- Used to check commit history
- Shows all commits, author details, commit hash, head pointer, date of commit (timestamp), commit message
- git log -p -<number of commits>
- git log -p -1 sees last commit

## Git Show
- Shows detailed INFO like what we did inside the commit
- git show [<options>] [<object>...]
- Green means added
- Red means deleted

## Git Configuration
- git config
- git config -h or git config -help shows all options
- 3 Levels of config: Local, Global, System
- System is highest level and can be accessed at global and local level and to all users
- Local is current repo, Global is current User(PC), System is all users
- git config --global --list allows us to see all global config values most of times author details
- Global file found at /home/GIT/.gitconfig
- git config --system --list
- System stored in /etc/gitconfig
- System config can be overriden by global and local settings and they can be inherited as well
- git config --local --list shows local config
- Local found in .git/config

