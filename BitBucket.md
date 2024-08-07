# BitBucket
It is a repository hosting tool based on git. Host private or public repo. 
- Create repo and enables collaboration between teams
- Bitbucket belongs to the Atlassian family - JIRA
- Bitbucket Cloud is a Git based cloud hosting and collaboration tool
- In-built integration with Jira and Trello integration
- In-built support for CI/CD pipeline automation
- Core Bitbucket can be used for performing the variety of activities
- Single package which is performing a variety of tools and number of tasks

Features:
- All features provided by Git
- Access control (Authentication levels, limitations)
- Workflow control to maintain project workflow
- Pull requests for code review with merging activity
- Jira integration for full development activity and traceability
- Rest API to build custom features from Marketplace

Organize BitBucket Project on Server
- Team area
- Project area
- Can provide access to the team to specific repo or project
- Access specifier

- We have Bitbucket Repo and Project area: Project A, B, C
- Team area: Project A: A1, A2, A3
- Project B: B1, B2
- Project C: C1, C2

- Jira tool used for issue management
- Recording of issues

## Key Terms to Know
1. Pipelines
- An integrated CI/CD service no need for Jenkins, TeamCity or Bamboo
- Build automation Deployment
- Provides end to end pipeline
- Usage quota - in minutes
2. Pipes
- Pre-defined workflows to automate CI/CD pipeline
- Configure as per the specific need
- Automatically generates pre-defined pipelines which can be easily integrated
3. Project
- Composition of repo
- Makes it easier for teams to work together

## BitBucket Pipeline
- Code Change -> BitBucket
- Build App, Test App -> Maven -> Jar > Docker Image > Docker registry
- Build docker image, push docker image > Docker > Docker registry
- Deploy App -> Kubernetes Cluster -> Docker Registry

- Helps implement CI/CD
- Connect to tany cloud, on-premises
- No need to create third party infrastructure
- already have runners to run CI/CD pipeline
- Specific quota will be given on how much minutes one can run

## Working with remote BitBucket repo
- Need Bitbucket cloud acc
- Need Git
- Git commands (clone, branch, checkout)

Your work - > New Repo -> Fill Details

