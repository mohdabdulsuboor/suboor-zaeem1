### :camel: setup and maintain a end-to-end CICD pipeline with github,Jenkins,Nexus,Dockerhub,Helm,K8s on AWS(EKS)
---
### Architecture 
![Architecture of Project k8s&aws](https://i.gyazo.com/6e66f96059ab7628491ae496bc595bf6.png)

* *this is only a partial architecture diagram

###  Task1: create github account
* go to www.github.com and create a free account using your personal email id 
* create an empty repository on github
* clone the repo from github remote to git local 
* Branch Checkout
git status                      
git checkout -b my-new-branch 
git commit -m
* push the branch to remote 
git push origin --all
### Task2: Build Jenkins Server
* Install Jenkins
* Install Nexus
* Jenkins plugins Installation
* Install & configure Maven
* Nexus Repository Configuration on Jenkins
* slack configuration for notifications
### Task3: Job Configuration
* Free style job Configuration
* parameterized job configuration
* scripted pipeline configuration
* declarative pipeline configuration
### Task4: Create Dockerhub Account
* go to www.docker.com and create an account
* login to the account and create a new Repository
* Install docker-ce 
* search & Pull images from dockerhub
* launch containers with port and volumes
* tag images & push images to dockerhub
### Task5: Create Chartrepo account
* Create a new repository on your github account(i.e."helm chart")
* clone the repository 
* create chart.yml file
* yml files deployed to dockerhub and images has been pulled for    Deployment of pods
* Nexus OSS to store the helm charts
### Task6: Run the Jobs
* Build Docker images
* Build helm chart
###  Task7: Build EKS Cluster
* Go to Aws Console
* Search Default Eks
* Create EKS cluster
### Task8: Run a Jenkins helm job to Deploy the app
* Helm package manager to deploy helm chart based applications to EKS cluster (through jenkins pipelines)