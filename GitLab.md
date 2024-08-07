# GitLab
It is a popular Version Control System (VCS)/Source Control Management(SCM). It is published in 2011 and designed in Ruby on Rails.
- Enables the agile development of cross-team software
- Enables collaboration
- Supports roll-back

Offering:
- Git repo management
- Code Reviews
- Issue tracking
- Activity Feed
- Wikis
- Complete DevOps platform is supported by GitLab
- Provides CI/CD pipelines which helps DevOps operations

You can be an admin user and create other users.

on top bar -> Menu -> Admin area -> Users -> New User

## Working using GitLab
- Click on GitLab
- Click on New Project
- Visibility level: private
- Lock symbol = private project
- Choose Settings (Repo)-> Members -> Add Collaborators -> Give them Access/permissions
- We can also import members from another project to our project
- We can setup Access expiration date for members

## Working with GitLab Remote Repo
- Login
- Choose Repo or Create
- https://gitlab.com/gitlab-tests/sample-project
- Fork above repo as its provided by GitLab for Practice
- Every Remote Repo has URL
- There are 2 types: HTTPS requires user and pass/SSH password-less, requires key-pair
- You can use Git Bash or Power Shell editor
- git clone https://gitlab.com/gitlab-tests/sample-project.git
- mkdir directoryname makes an empty folder
- git init converts folder into a git repo
- git remote add origin <repoURL>
- git remote -v

## Branch Names
Can:
- User lowercase letters
- numbers
- hyphens
- underscore
Can NOT:
- contain empty space
- special characters



