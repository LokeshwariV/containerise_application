# Instructions to run application

Application is containerized using docker. Deployment definitions is written in the form of docker-compose. Continuous Integration and Continuous delivery adapted using Gilab CI-CD pipelines

Details of architecture, choice of technology stack , versioning, source code analysis, deployment management are provided in Build_Deploy_plan.pptx

## Project files included

* Application files i.e requirements.txt, app.py and app_test.py
* Includes dockerfile and docker-compose.yml files
* Environment variable files referred in docker compose
* .gitlab-ci.yml file which included CI-CD definition
* dockerfile_custom showing the base image which is used to running CI-CD pipeline
* Build_Deploy_Plan.pptx PPT  which explains architecture and tool stack used
* sample_release.zip file which will be created after CI-pipeline is run
* Sample_release.zip also includes docker images that is required to run docker swarm

Below steps contain the information to setup paltform and run the application and pipelines.

### To Only test docker images

* Install docker
* Clone repo to target location
* Run *Docker build -t py-web-app .* to build docker image
* Then pull redis image from docker registry *Docker pull redis*
* Run *docker-compose up -d* to deploy containers
* Access the application using *http://localhost:5000*

### CI-CD Pipeline

Used Gitlab-CI to build and deploy the application. To run the pipeline please follow the below steps.

1. Create a project in gitlab and commit the python project with all the files
2. Create a branch of the current project in gitlab
3. Create custom docker image including python, CUrl, jfrog cli, docker and Unzip and push it in artifactory docker registry (Example docker image included in the project with the name dockerfile_custom)
4. Gilab runners has to be configured
5. Using custom docker image build as default to run the pipeline
6. Artifactory repository for docker and release project repo must be created
      - Artifactory Generic Project name: py-web-app-release
      - Docker-virtual: Docker registry in artifacotry
7. Artifactory secrets msut be stored in Gitlab CI-CD masked variables. Secrets are
      - Artifacotry URL
      - Artfacotry Username
      - Artifacotry Password
8. SSH credentials and details for target deployment server must be stored in Gitlab CI-CD masked variables
      - Deployment Target Machine IP
      - SSH Username
      - SSH Password
9. Run the pipeline
      - Pipeline will run docker build and created docker images
      - Provision docker containers
      - Run the unit tests and integration test
      - If the Merge requests is apporved then images are zipped with the docker container file and uploaded to artifacotry
      - When the master/origin is tagged with the correct version then the deploy stage is triggered and the application is deployed to target machine
