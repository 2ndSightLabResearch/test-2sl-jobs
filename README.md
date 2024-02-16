# 2sl-jobs
Jobs that can be run using the 2nd Sight Lab (2sl) Job Execution Framework

See the readme in the 2sl-job-exec repository for more information.

# scripts
The scripts folder contains scripts that build containers in this repository, pull or push to an ECR repository.

# AWS Jobs
See the readme in each job directory for more information on the job.

awsorginit - initialize a new account with an AWS Organization and administrative role named root-admin

awsenvinit - initializes a job execution framework environment including accounts, roles, KMS key, ECR and Code Commit repository

awsenvconfig - deploy the rest of your environment using the environment administrator IAM account.

awsdeploy - once you have an environment, you can use awsdeploy to deploy...anything. MFA is required to deploy jobs.


