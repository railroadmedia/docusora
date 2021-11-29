# Sysops Overview Of Environments & Deployment

This document is meant to provide an overview of how our deployment cycle works and all the tools and technologies
involved. It also describes our different environments (staging, production, etc) and how to set up new ones.

<br>

## Deployment Process Overview

1. We run a bash script from our local dev environment which uses the AWS cli tool to trigger a codebuild build.
2. Codebuild pulls the configured repository (like drumeo, pianote, etc) and branch, then runs the steps inside the 
   repositories buildspec.yaml (or buildspec-eks.yaml for newer staging envs) file.
3. In summary, the buildspec file tells codebuild to make a .env file for the laravel configuration based on an AWS
   secret. Then it uses docker to build the image and upload it to an AWS ECS repository.
4. Once the build is complete, the bash script running will automatically detect that the build is complete (it does
   this by polling the build job using the AWS cli every 30 seconds). Once it does, it updates the k8 deployment
   to use the new docker image URL.
5. Our kubernetes stack automatically applies the new image pod by pod.


## Secret Management (the latest system)

Our app secrets (sensitive environment details like database connection info) are stored inside AWS Secret Manager 
as key-value pairs. Our AWS Code Build config automatically pulls this secret in to a JSON variable in the 
build process. We access this data inside the buildspec.yaml file commands and copy all the data to a .env file in the 
repository files. The build process then encrypts the .env file using an encryption key. We encrypt the file so the 
docker image doesn't have the actual secrets inside. If someone were to have one of our platforms docker images 
it would be useless without the encryption key.

When new build are deployed to our kubernetes cluster, the deployment bash command 
(inside the kubernetes yaml file for the deployment) decrypts the .env file so laravel can read it.