# GitOps-workflow
- store automation code, application code and cloud automation in Git
- GitHub Actions will detect and apply changes
- each repo has secrets stored of the IAM user, S3 bucket, ecr registry, Sonarcloud, etc...
 


I have 2 GitHub repos, for 2 workflows:
  - iac-profile has infrastructure code:
    - applies changes to AWS 
    - 2 branches, "stage" (testing) and "main" branch to apply the changes
    - GitHub pipeline creates a VPC, eks cluster and outputs values from the terraform folder 
    - only if changes are pushed from the main branch will everything be applied
      - the eks cluster will be created and the ingress controller will be installed  

  vprofile-actions has application code:
  - had to create a Sonarcloud project to store the analysis, had to generate the token for
    authentication then store the details on GitHub secrets
    - set up quality gates for the project to be <50 bugs
  - workflow to fetch code, test with maven checkstyle and sonar analysis 
  - set up to run on manual trigger only.
  - build docker image, upload to amazon ecr
  - helm charts will fetch latest image to run apps
