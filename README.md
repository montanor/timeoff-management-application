# Gorilla Logic DevOps candidate test
## Introduction
This repo content is a fork of https://github.com/timeoff-management/timeoff-management-application, This project was only created as a deliverable for a recruitment test.

## How the pipeline works
![Pipeline Diagram](https://i.ibb.co/NpCP76w/Untitled-Diagram.png)
- Jenkins is polling every minute to this repo for checking new commits.
- When a new push is accepted into the MASTER branch of this repo a pipeline is triggered.
- This pipeline, builds the NodeJS artifact and uploads it into a Nexus repository.
- Finally, the artifact gets deployed into the application server.
  
![Pipeline Screenshot](https://i.ibb.co/zVrkCCQ/Screenshot-20201004-192022.png)

## Files added to this repo
- **Jenkinsfile** Groove definition file for the jenkins pipeline
- **deploytimeoff.yml** Ansible playbook for deploying the artifact into the server
- **hosts** Ansible targets definition file

## Pre-requisites
- A functional Jenkins server
- Nexus repository with NPM repos (Proxy and private) enabled
- A debian based distribution for the execution of the ansible script

## To-do
- Using a hostname for the ansible and NPM private registry URL.
- Using NPM module for ansible instead of shell scripts.
