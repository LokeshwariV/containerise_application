# DevOps Interview Assignment

## Introduction
As an engineer in the Platform team, you will often be faced with task around best practices for docker, orchestration, continuous integration and deployment, logging, security, monitoring, network and hosting.

This assignment is meant to showcase abilities within the fields above, and is used a discussion point for interviews.

## The Assignment

### The Task
The `./app` directory contains a python/flask based API. The API is a very simple application, with the functionality that allows getting, setting and resetting timestamps from and in a redis database. Included is also a test script.

You are expected to minimum deliver the following:

* Dockerfiles for the app and a redis database.
* Deployment definitions in the form of docker-compose or kubernetes manifests.
* Build script, makefile and/or jenkinsfile, travis.yml or similar pipeline definition.


Further the following topics can be added either as part of the delivery or with considerations in documentation (in no particular order). We are not expecting all topics to be covered, and we prefer deep coverage of few topics over broad coverage of many topics.

Core topics:

* Logging
* Execution of different types of tests
* Environment configuration
* Deployment strategy

Stretch topics:

* Linting and static code analysis
* Versioning (app and dependencies)
* Secrets management
* Monitoring
* Health / Readiness checks
* Ingress / Reverse proxy
* Branching strategy
* Git structure
* Security
* Storage and persistency
* Scalability
* Means of deployment
* Operations

Feel free to change or restructure app files as you see fit.

Minimally, it should be possible to:

* Build Dockerfiles
* Execute deployment with docker-compose or minikube
* curl or otherwise reach API endpoints

For code and config requiring SaaS solutions or e.g. Jenkins, please add comments on required config, dependencies etc.


### General Guidelines

* Your code and other deliverables must be provided as a link to a private git repository (GitHub or Bitbucket).
* The delivery must include a markdown readme file with concise and complete instructions on how to use (unpack, build, install, execute, access, etc.) your delivery.
* You must provide additional documentation (architecture, structure of the code base, discussion of the technology stack choices you made, etc); the format is up to you, but ideally it will be some form of source code (e.g., markdown).
* Your solution must only be accessible to you and us; please make sure it is not available for a wider audience, especially not publicly.
We would like to reuse the challenge, please help us keeping it fair!
